import streamlit as st
import numpy as np
import plotly.graph_objs as go

# Function to calculate asset valuation
def asset_valuation_model(initial_investment, annual_growth_rate, years):
    # Perform asset valuation calculations
    valuation = initial_investment * (1 + annual_growth_rate) ** years
    return valuation

# Function to generate graph
def generate_graph(initial_investment, annual_growth_rate, years):
    # Generate data for graph
    years_range = np.arange(0, years+1)
    valuations = [asset_valuation_model(initial_investment, annual_growth_rate, year) for year in years_range]

    # Create Plotly figure
    fig = go.Figure()
    fig.add_trace(go.Scatter(x=years_range, y=valuations, mode='lines+markers', name='Asset Valuation'))
    fig.update_layout(title='Asset Valuation Over Time',
                      xaxis_title='Years',
                      yaxis_title='Valuation ($)',
                      template='plotly_white')
    st.plotly_chart(fig)

# App title and description
st.title('Asset Valuation Model')
st.write("""
This app calculates the valuation of an asset based on the initial investment, annual growth rate, and number of years.
""")

# Sidebar inputs
st.sidebar.header('Input Parameters')
initial_investment = st.sidebar.number_input('Initial Investment ($)', value=10000, step=100)
annual_growth_rate = st.sidebar.slider('Annual Growth Rate (%)', min_value=0.0, max_value=1.0, value=0.05, step=0.01, format='%.2f')
years = st.sidebar.number_input('Years', value=5, step=1, min_value=1, max_value=50)

# Calculate asset valuation
valuation = asset_valuation_model(initial_investment, annual_growth_rate, years)

# Display result
st.subheader('Asset Valuation')
st.write(f"The valuation of the asset after {years} years is ${valuation:,.2f}")

# Generate and display graph
st.subheader('Asset Valuation Over Time')
generate_graph(initial_investment, annual_growth_rate, years)

# Additional features or explanations can be added here
