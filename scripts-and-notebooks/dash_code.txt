# Import required libraries
import pandas as pd
import dash
from dash import html
from dash import dcc
from dash.dependencies import Input, Output
import plotly.express as px

# Read the SpaceX launch data into pandas dataframe
spacex_df = pd.read_csv("spacex_launch_dash.csv")

# Get max and min payload values
max_payload = spacex_df['Payload Mass (kg)'].max()
min_payload = spacex_df['Payload Mass (kg)'].min()

# Create a dash application
app = dash.Dash(__name__)

# Create an app layout
app.layout = html.Div(children=[
    html.H1('SpaceX Launch Records Dashboard',
            style={'textAlign': 'center', 'color': '#503D36', 'font-size': 40}),

    # TASK 1: Dropdown list to select Launch Site
    dcc.Dropdown(
        id='site-dropdown',
        options=[{'label': 'All Sites', 'value': 'ALL'}] +
                [{'label': site, 'value': site} for site in spacex_df['Launch Site'].unique()],
        value='ALL',
        placeholder="Select a Launch Site here",
        searchable=True
    ),

    html.Br(),

    # TASK 2: Pie chart to show successful launches
    html.Div(dcc.Graph(id='success-pie-chart')),
    html.Br(),

    # TASK 3: Payload Range Slider
    html.P("Payload range (Kg):"),
    dcc.RangeSlider(
        id='payload-slider',
        min=0,
        max=10000,
        step=1000,
        marks={i: f'{i}' for i in range(0, 10001, 2500)},
        value=[min_payload, max_payload]
    ),

    # TASK 4: Scatter plot for success rate vs payload
    html.Div(dcc.Graph(id='success-payload-scatter-chart')),
])

# TASK 2: Callback to update pie chart based on selected site
@app.callback(
    Output(component_id='success-pie-chart', component_property='figure'),
    Input(component_id='site-dropdown', component_property='value')
)
def get_pie_chart(entered_site):
    if entered_site == 'ALL':
        fig = px.pie(spacex_df,
                     values='class',
                     names='Launch Site',
                     title='Total Success Launches by Site')
    else:
        # Filter data for selected site
        filtered_df = spacex_df[spacex_df['Launch Site'] == entered_site]
        counts = filtered_df['class'].value_counts().reset_index()
        counts.columns = ['Result', 'Count']
        counts['Result'] = counts['Result'].replace({1: 'Success', 0: 'Failure'})
        fig = px.pie(counts,
                     values='Count',
                     names='Result',
                     title=f'Success vs Failure Launches for site: {entered_site}')
    return fig

# TASK 4: Callback to update scatter plot based on site and payload
@app.callback(
    Output(component_id='success-payload-scatter-chart', component_property='figure'),
    [Input(component_id='site-dropdown', component_property='value'),
     Input(component_id='payload-slider', component_property='value')]
)
def get_scatter_chart(selected_site, payload_range):
    low, high = payload_range
    filtered_df = spacex_df[(spacex_df['Payload Mass (kg)'] >= low) &
                            (spacex_df['Payload Mass (kg)'] <= high)]

    if selected_site != 'ALL':
        filtered_df = filtered_df[filtered_df['Launch Site'] == selected_site]

    fig = px.scatter(filtered_df,
                     x='Payload Mass (kg)',
                     y='class',
                     color='Booster Version Category',
                     title='Payload vs. Launch Outcome')
    return fig

# Run the app
if __name__ == '__main__':
    app.run()
