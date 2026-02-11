Market Analysis Dashboard

This project provides a comprehensive web-based dashboard for analyzing market trends across cryptocurrencies, crude oil, and stock indices. Built using Streamlit, it offers interactive data exploration, SQL query execution, and detailed cryptocurrency analysis, all accessible through a user-friendly interface.

 Live Application

Access the live Streamlit application here: [https://concha-coreless-habitably.ngrok-free.dev](https://concha-coreless-habitably.ngrok-free.dev)

 Features

The dashboard is organized into three main pages:

 1. Filters & Data Exploration
- **Date Range Selection**: Customize the period for data analysis.
- **Average Prices**: View average prices for Bitcoin, Crude Oil, S&P 500 (`^GSPC`), and NIFTY 50 (`^NSEI`).
- **Daily Market Snapshot**: Visualize daily price trends of selected assets with interactive Altair charts.

 2. SQL Query Runner
- **Predefined Queries**: Execute a variety of pre-configured SQL queries against the underlying SQLite database.
- **Data Display**: Results are presented in a clear, tabular format.

 3. Top Crypto Analysis
- **Cryptocurrency Selection**: Choose up to three top cryptocurrencies (Bitcoin, Ethereum, Tether) for detailed analysis.
- **Daily Price Trends**: Visualize historical daily price movements for selected cryptocurrencies.
- **Raw Data**: View the raw historical price data.

 Data Sources

The application integrates data from several sources:
- **CoinGecko API**: Cryptocurrency market data and historical prices.
- **datasets/oil-prices (GitHub)**: Historical WTI crude oil prices.
- **Yahoo Finance API (`yfinance`)**: Historical stock prices for S&P 500 (`^GSPC`), NASDAQ (`^IXIC`), and NIFTY 50 (`^NSEI`).

 Technologies Used
- **Python**: Primary programming language.
- **Streamlit**: For building the interactive web application.
- **Pandas**: Data manipulation and analysis.
- **SQLite**: Local database for storing and querying market data.
- **Altair**: Declarative statistical visualizations.
- **Requests**: For API interactions.
- **`yfinance`**: Python library for fetching Yahoo Finance data.
- **`pyngrok`**: For exposing the local Streamlit application publicly.

 How to Run Locally (or in Colab)

To set up and run this project, follow these steps:

 1. Environment Setup

First, install the required Python libraries:

```bash
pip install streamlit pyngrok requests pandas yfinance
```

 2. Ngrok Authentication

To expose your Streamlit app publicly (necessary for sharing or if running in environments like Colab), you need an Ngrok authtoken.

1.  **Get your authtoken**: Sign up at [ngrok.com](https://ngrok.com/) and retrieve your authtoken from the dashboard.
2.  **Set authtoken**: In Google Colab, add your authtoken to the 'Secrets' tab (🔑 icon on the left panel) with the name `NGROK_AUTH_TOKEN`.

 3. Data Collection and Database Setup

The project requires a SQLite database named `mydatabase.db` populated with cryptocurrency, oil, and stock data. The necessary Python code to fetch this data from APIs and populate the database is provided within the Colab notebook.

 4. Run the Streamlit Application

Once the `app.py` file is created (as demonstrated in the Colab notebook) and the database is populated, run the Streamlit application. If running in a local terminal, use:

```bash
streamlit run app.py
```

If running in Google Colab, the notebook provides a Python cell that starts Streamlit in the background and sets up the Ngrok tunnel, printing the public URL for access. This cell handles killing previous Streamlit processes, configuring Ngrok, and launching the app:

```python
import subprocess
import time
from pyngrok import ngrok
import os
from google.colab import userdata
... (code to kill processes, start Streamlit, configure ngrok, and connect tunnel) ...

NGROK_AUTH_TOKEN = userdata.get('NGROK_AUTH_TOKEN') # Fetches from Colab secrets
ngrok.set_auth_token(NGROK_AUTH_TOKEN)

tunnel = ngrok.connect(8501) # Connects to Streamlit's default port
public_url = tunnel.public_url
print(f"Streamlit App is live at: {public_url}")
```

 Project Structure

- `app.py`: The main Streamlit application script containing all dashboard logic.
- `mydatabase.db`: SQLite database file storing all collected market data.
- `README.md`: This file, providing an overview of the project.

For any questions or suggestions, please open an issue in the repository.
