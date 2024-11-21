# Financial Market Code Repository

This repository contains Python scripts and Jupyter notebooks for analyzing and working with financial data. It includes tools for tasks such as web scraping, yield curve interpolation, and quantitative analysis. The goal is to provide practical solutions for financial professionals and enthusiasts interested in market data analysis, forecasting, and risk management.

Feel free to explore, use, and contribute to the code. Contributions to improve or extend the functionality are always welcome!

## Contributions

If you'd like to contribute to this repository, please fork the project, make your changes, and submit a pull request. All contributions are appreciated!





# **b3_historical_quotes_for_any_asset.ipynb**

This code extracts and processes historical quotes for assets listed on B3 (Brazilian Stock Exchange) from the standardized COTAHIST_AAAA.TXT file provided by the exchange.

The script reads the fixed-width formatted file, assigns column names according to B3 documentation, and processes the data, including decimal adjustments and market type filtering. It allows specific asset selection, such as WEGE3, and provides historical data with date-based indexing.

## **Key Features:**
- Import and organization of raw B3 data.
- Conversion of financial values to decimal scale.
- Filtering by market types, such as spot, call options, and put options.
- Date indexing for temporal analysis.

## **How to use:**
1. Replace the COTAHIST_A2024.TXT file with the desired file in the same format.
2. Run the notebook to load and process the data.
3. Customize filters and selections based on the desired asset and market type.




# **brazil_cds_scraper.ipynb**

This code scrapes historical Credit Default Swap (CDS) data for Brazil from the Investing.com website. CDS data is available for various maturities, ranging from 1 to 10 years, and is a key indicator of sovereign credit risk.

The script uses BeautifulSoup to parse HTML pages and pandas to structure the extracted data into a consolidated DataFrame. Each column represents a CDS maturity term, and the rows are indexed by date.

## **Key Features:**
- Automated extraction of historical CDS data from Investing.com.
- Consolidation of CDS data for different maturities (1 year, 2 years, up to 10 years).
- Date-indexed DataFrame for easy analysis and visualization.

## **How it works:**

### **1. CDS Maturities List:**
A list of CDS maturities is defined (cds-1-year, cds-2-years, etc.).

### **2. Data Fetching:**
The script iterates through each maturity, constructs the corresponding URL, and fetches the data.

### **3. HTML Parsing:**
HTML parsing is performed to locate the data table, and the results are formatted and indexed by date.

### **4. Data Consolidation:**
Data for all maturities is combined into a single DataFrame for further analysis.


# **cvm_financial_data_scraper.ipynb**

This code automates the extraction and processing of financial data from the Brazilian Securities and Exchange Commission (CVM) for publicly traded companies. It focuses on downloading, unzipping, and structuring data from the CVM's DFP (Standardized Financial Statements) files for years ranging from 2010 to 2023.

## **Key Features:**
- Downloads financial statement data in `.zip` format directly from the CVM's public repository.
- Extracts and consolidates CSV files into a unified DataFrame.
- Provides pre-processing to clean and organize data, facilitating financial analysis.
- Enables targeted data extraction, such as revenue information for specific companies (e.g., WEG S.A.).

## **How it works:**

### **1. Data Download:**
The script iterates over a range of years (2010–2023) and fetches `.zip` files containing financial data from the CVM's repository.

### **2. Unzipping and Parsing:**
Each `.zip` file is unzipped, and its CSV contents are read into a pandas DataFrame using chunked reading for efficiency.

### **3. Data Cleaning:**
- Columns are split, renamed, and stripped of unnecessary data.
- Filters are applied to remove redundant or invalid rows, such as non-final data versions.

### **4. Targeted Analysis:**
A specific example extracts the revenue data (`Receita de Venda de Bens e/ou Serviços`) for WEG S.A. from its consolidated financial statements.

## **Notes:**
- The script fetches data from the CVM's repository, which is publicly available but subject to periodic updates.
- Ensure sufficient storage space and permissions in the specified directory.
- CSV files use ISO-8859-1 encoding and `;` as the delimiter, typical for Brazilian datasets.


# **investment_funds_analysis_cvm_july_2024.ipynb**

This code downloads, processes, and analyzes investment fund data from the Brazilian Securities and Exchange Commission (CVM) for July 2024. It retrieves daily data files from the CVM's website, extracts relevant fund information, and merges it with registration details to provide a comprehensive dataset for analysis.

The script automatically downloads the ZIP file containing the daily fund data, extracts the contents, and processes them. It then cleans the dataset by removing unnecessary columns and combines it with fund registration information for a detailed overview.

## **Key Features:**
- **Web scraping** to automatically download the ZIP file containing daily fund data.
- **Extraction and processing** of the ZIP file contents.
- **Merging and refining** the dataset to focus on the most relevant information for analysis.


## **How to Use:**
1. **Run the script** to automatically download and extract the ZIP file from the CVM website.
2. The script will **process and merge the data** into a detailed dataset.
3. **Customize** the code to analyze specific funds or time periods as needed.


# **fake_market_report_pdf.ipynb**

This script generates a fake market report in PDF format using the `FPDF` library. The report includes various financial data points, such as market closures, performance charts, and economic indicators, and is structured into sections with tables and images.

## Key features:
- Custom header and footer with company logo and page numbers.
- Automated generation of financial data for different assets (Ibovespa, S&P500, and Dólar).
- Randomized performance data for monthly returns and volatility.
- Visualization of asset performance with charts embedded directly in the PDF.
- Data sections include: market closures, month-to-month performance, annual returns, volatility, and economic indicators such as interest rates, inflation, and the Selic rate.

## How it works:

### Header and Footer:
- The header includes the company logo and the market report title.
- The footer includes page numbers.

### Market Data:
- The script generates random market performance data for Ibovespa, S&P500, and Dólar, formatted into tables.
- Monthly returns for each asset are presented in a table format, with values generated randomly.
- The annual return and volatility for each asset are also calculated and displayed.

### Charts:
- Charts for **Ibovespa**, **S&P500**, and **Dólar** are included, which are assumed to be saved as images (`ibov.png`, `sp.png`, `dolar.png`).
- Other economic indicators, such as interest rates and inflation, are represented by their respective graphs (`juros.png`, `inflacao.png`, `selic.png`).

### Final Output:
- The final report is saved as `fake_market_report.pdf`.

## Notes:
- This is a mock report, useful for testing and demonstrating PDF generation.
- Ensure you have the necessary image files (e.g., `ibov.png`, `sp.png`) in the same directory as the script for the charts to be embedded correctly.
- The report includes randomized data for illustrative purposes and is not linked to real-world financial data.


# **markowitz_optimization.ipynb**

This script performs portfolio optimization using the *Markowitz Efficient Frontier* model. It utilizes historical stock price data from Yahoo Finance and computes the optimal portfolio weights based on the Sharpe ratio, with the goal of maximizing returns for a given level of risk (volatility).

## Key features:
- Downloads historical stock price data for selected assets using `yfinance`.
- Calculates log returns for each asset and computes the expected returns and covariance matrix.
- Generates a large number of random portfolios to simulate different asset allocations.
- Optimizes the portfolio to maximize the Sharpe ratio (return per unit of risk).
- Computes and plots the efficient frontier, showing the risk-return trade-off for different portfolios.
- Highlights the portfolio with the highest Sharpe ratio on the graph.

## How it works:

### Data Download and Preprocessing:
- The script downloads adjusted closing prices for a list of selected assets (e.g., AAPL, NKE, GOOGL, AMZN, NVDA, MSFT) from Yahoo Finance using `yfinance`.
- Logarithmic returns are calculated for each asset to normalize the data and ensure consistency in calculations.
- The expected return and covariance matrix for the assets are computed.

### Portfolio Simulation:
- The script generates **100,000 random portfolios** by assigning random weights to each asset, ensuring that the sum of the weights equals 1.
- For each portfolio, the expected return and volatility (risk) are calculated.
- The **Sharpe ratio** for each portfolio is computed, and the portfolio with the highest Sharpe ratio is selected as the optimal portfolio.

### Efficient Frontier:
- The script calculates the **efficient frontier** by optimizing portfolios for different levels of expected return.
- It minimizes portfolio volatility for each level of return and plots the efficient frontier curve, which shows the optimal trade-off between risk and return.

### Final Output:
- The script generates a scatter plot of expected return vs. expected volatility for all simulated portfolios.
- The portfolio with the maximum Sharpe ratio is marked in red.
- The efficient frontier is plotted, representing the set of optimal portfolios.
  
## Notes:
- The data used is historical and does not represent future performance.
- Ensure the correct dependencies (`yfinance`, `numpy`, `matplotlib`, `scipy`) are installed to run the script.
- The efficient frontier and the optimal portfolio are useful for understanding the trade-off between risk and return in portfolio management.


# **max_drawdown_calculator.ipynb**

This script calculates the **maximum drawdown** for a selected stock (PETR4.SA in this case) using historical price data from Yahoo Finance. The script plots the drawdown over time and identifies the largest drawdown during the specified period.

## Key features:
- Downloads historical adjusted closing prices for a selected stock using `yfinance`.
- Calculates the cumulative maximum price (`cummax`) and the drawdown (the percentage decline from the peak) over time.
- Identifies the maximum drawdown value.
- Plots the drawdown over time using a "cyberpunk" style for the graph.

## How it works:

### Data Download and Preprocessing:
- The script downloads the historical adjusted closing prices of the stock **PETR4.SA** for the last 1050 days (approximately 3 years) from Yahoo Finance using `yfinance`.
- It calculates the **cumulative maximum price** (`cummax`) to identify the peak value at each point in time.
- The drawdown is then computed as the percentage decline from the peak, represented by the formula:

### Maximum Drawdown:
- The **maximum drawdown** is identified by finding the minimum value in the drawdown series, representing the largest decline from peak to trough during the time period.

### Plotting:
- The drawdown over time is plotted using **matplotlib**, with a "cyberpunk" theme applied for the graph's style.
- The y-axis is formatted as a percentage using `PercentFormatter`, and the x-axis is set to display yearly intervals.

### Final Output:
- The script displays a plot of the drawdown over time, with the maximum drawdown value printed in the console.

## Notes:
- The data used is historical and may not represent future performance.
- The plot uses a "cyberpunk" style, which can be customized by changing the plotting style.
- Ensure the required dependencies (`yfinance`, `matplotlib`, `mplcyberpunk`) are installed to run the script.

# **monte_carlo_simulation_for_VaR_and_profit.ipynb**

This notebook performs a **Monte Carlo simulation** to predict the potential future value of a portfolio and calculate **Value at Risk (VaR)**. The portfolio consists of five stocks: **WEGE3**, **PCAR3**, **PRIO3**, **VALE3**, and **ITUB4**, with data fetched from Yahoo Finance.

## Key Features:
- **Monte Carlo Simulations**: 10,000 simulations to forecast portfolio outcomes for the next year.
- **Risk Analysis**: Calculates the **50th**, **95th**, and **99th** percentiles of final portfolio values.
- **Profitability**: Percentage of scenarios where the portfolio results in a profit.
- **VaR Calculation**: Analyzes portfolio risk over the next year.

## How It Works:
- **Data Download**: Historical prices are retrieved from Yahoo Finance.
- **Return Calculation**: Daily returns are computed and used to estimate the portfolio’s risk (covariance matrix).
- **Simulations**: Synthetic returns are generated using Cholesky decomposition to simulate potential portfolio paths.
- **Results**: Final values are calculated and percentiles (50%, 95%, 99%) are computed.

## Results:
- Prints the expected portfolio value with 50%, 95%, and 99% confidence levels.
- Displays the percentage of profitable scenarios.

## VaR Visualization:
- A histogram is plotted to show the distribution of final portfolio values, helping visualize potential risk.

### Example Output:
Investing R$ 1000 in the portfolio ['WEGE3.SA', 'PCAR3.SA', 'PRIO3.SA', 'VALE3.SA', 'ITUB4.SA'], the Monte Carlo simulation (10,000 runs) gives:

With 50% probability, the final amount will exceed R$ 1184.96.

With 95% probability, the final amount will exceed R$ 859.40.

With 99% probability, the final amount will exceed R$ 752.12.

In 81.01% of scenarios, a profit is expected.


# **read_pdf_tables.ipynb**

This notebook extracts and processes data from a PDF report using the **PyPDF2** and **Tabula** libraries to read and analyze financial data.

## Key Features:
- **Extracts Text**: Extracts text data from a PDF file (`weg.pdf`).
- **Tabular Data Extraction**: Uses **Tabula** for parsing tables from PDF pages.
- **Text Preprocessing**: Cleans and formats the extracted text for further analysis.

## How It Works:
1. **PDF Parsing**: The code opens and reads the `weg.pdf` file.
2. **Text Extraction**: The text content from the first page is extracted, providing details on financial data and key performance indicators.
3. **Table Extraction**: **Tabula** is used to detect and extract tabular data from the PDF.
4. **Formatted Output**: The raw text from the PDF is cleaned and formatted for readability and analysis.

## Example Output:
Extracted text includes financial highlights such as:
Jaraguá do Sul, Brazil, 31 July 2024

Highlights:

Net Revenue (ROL) was R$ 9,274.4 million in 2T24, 13.5% higher than 2T23 and 15.4% higher than 1T24.
EBITDA reached R$ 2,120.8 million, 15.7% higher than 2T23 and 19.8% higher than 1T24.
ROIC reached 37.4% in 2T24, an increase of 3.0 percentage points compared to 2T23. ...


## Requirements:
- Install `PyPDF2`, `re`, and `tabula-py` to run the PDF extraction.


# **regression_beta_calculator.ipynb**

This notebook calculates the **beta** of a Brazilian stock relative to the **Bovespa index** (^BVSP) using linear regression, leveraging the **yfinance** and **statsmodels** libraries.

## Key Features:
- **Data Collection**: Downloads historical adjusted closing price data for the stock and the Bovespa index.
- **Daily Returns Calculation**: Computes daily percentage returns for both the stock and the index.
- **Linear Regression**: Performs a linear regression to calculate the stock's beta relative to the Bovespa index.
- **Regression Results**: Outputs the **beta**, **R²**, and detailed regression statistics.

## How It Works:
1. **Data Download**: The code fetches adjusted closing prices for the stock and the Bovespa index using **yfinance**.
2. **Returns Calculation**: Calculates daily returns by computing the percentage change of the adjusted closing prices.
3. **Regression Analysis**: Uses **statsmodels** to perform an Ordinary Least Squares (OLS) regression, where the stock's returns are regressed against the Bovespa index's returns.
4. **Output**: Displays the **beta**, **R²**, and regression summary, which includes statistical metrics like p-values and confidence intervals.

## Example Output:
- **Beta**: 1.059
- **R²**: 0.204
- **Regression Summary**: The output includes the detailed regression statistics such as coefficients, p-values, and confidence intervals.

This tool helps in assessing the risk (beta) of a stock in relation to the market, providing insights into how the stock moves relative to the broader market index.

# **words_cloud.ipynb**

This notebook generates a **word cloud** from the extracted text of a PDF file, using the **PyPDF2** and **WordCloud** libraries. It is designed to visualize the most frequent words in the document, excluding common stopwords.

## Key Features:
- **PDF Text Extraction**: Extracts the text content from each page of the specified PDF document.
- **Stopwords Filtering**: Custom stopwords are defined and excluded from the word cloud, including common words and specific terms like company names and financial indicators.
- **Word Cloud Generation**: Creates a visually appealing word cloud image, with customizable background color and dimensions.
- **Visualization**: Uses **matplotlib** to display the word cloud image.

## How It Works:
1. **PDF Reading**: The code loads the PDF (`klabin.pdf`) using **PyPDF2**'s **PdfReader**.
2. **Text Extraction**: Iterates through the pages of the PDF and extracts all the text content.
3. **Stopwords Customization**: A set of predefined stopwords (common words) is created to exclude irrelevant terms from the word cloud.
4. **Word Cloud Creation**: The **WordCloud** class is used to generate the word cloud from the extracted text, with the background color set to black and custom dimensions for the image.
5. **Display**: **matplotlib** is used to display the generated word cloud, with axis removed for a cleaner presentation.

## Example Output:
A word cloud visualizing the most frequent terms in the `klabin.pdf`, excluding the specified stopwords. Common terms like "Klabin" and financial indicators are removed, allowing the more relevant terms to stand out.

This tool is useful for quickly summarizing the key terms in a document and identifying important topics or themes.



# **yield_curve_interpolation.ipynb**

This notebook retrieves and processes data from a financial website, specifically the DI1 (Interbank Deposit) interest rate data, to perform **yield curve interpolation** using various interpolation methods, including linear, cubic, and cubic splines.

## Key Features:
- **Web Scraping**: Uses **Selenium** and **webdriver_manager** to scrape DI rates from the BM&F Bovespa website for a given date.
- **Data Cleaning and Preparation**: Extracts and formats the data for further processing and interpolation.
- **Interpolation Methods**: Implements linear, cubic, and cubic spline interpolation to estimate interest rates for future dates.
- **Visualization**: Plots the yield curve and interpolated points using **matplotlib** with a cyberpunk-style theme.

## How It Works:
1. **Data Retrieval**: Scrapes the DI rates from the BM&F Bovespa website using **Selenium** by navigating to a specific URL.
2. **Data Processing**: The data is cleaned, indexed by date, and prepared for interpolation. Specific date labels are mapped to actual date values.
3. **Interpolation**: Different interpolation methods are applied to estimate the DI rate for a specific future date (e.g., April 18, 2028). Methods used include:
    - **Linear Interpolation**: Straight-line estimates between known points.
    - **Cubic Interpolation**: Smooth curve estimates using cubic polynomials.
    - **Cubic Spline**: More sophisticated spline-based interpolation.
4. **Visualization**: The interpolated points are visualized on a plot, showing the original data and the interpolation results.

## Example Output:
The output includes a scatter plot with the original DI rates and interpolated values for various future dates (e.g., 18/04/2028), using different interpolation methods. For example, the interpolated DI rate for 18/04/2028 is estimated to be **11.755%** using linear interpolation, **11.689%** using cubic interpolation, and **11.690%** using cubic splines.

This analysis is useful for understanding the yield curve and estimating interest rates for future periods.








