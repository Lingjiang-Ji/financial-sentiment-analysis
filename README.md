Financial Sentiment Analysis
🎯 Objective

Perform a comprehensive sentiment analysis of SEC 10-K and 10-Q filings from 2015–2024,
examining how textual tone and disclosure sentiment correlate with firm stock performance over time.

💡 Research Motivation

SEC filings contain detailed narratives reflecting management’s perspective on performance, risks, and outlook.
By quantifying the sentiment embedded in these filings, we can capture shifts in corporate tone and market expectations.
Understanding this relationship helps identify how financial narratives influence investor behavior and valuation dynamics.

📊 Data Summary

The analysis uses public filings from the U.S. SEC EDGAR database for selected tickers (e.g., AMD) between 2015–2024.
It also integrates daily stock price data retrieved via the yfinance API for correlation analysis.

Data components include:

10-K and 10-Q filings (raw HTML and text format)

Loughran–McDonald Financial Sentiment Dictionary (1993–2024)

Historical stock prices for the analyzed firms

All filings are downloaded programmatically using the sec-edgar-downloader package.

🧮 Methodology

Filing Retrieval — Collect 10-K and 10-Q documents for a target company using the SEC EDGAR API.

Text Extraction & Cleaning — Use BeautifulSoup and regex to remove HTML tags, numbers, and formatting noise.

Tokenization — Split the cleaned text into word-level tokens for dictionary lookup.

Sentiment Scoring — Apply the Loughran–McDonald dictionary to compute positive and negative word counts,
then calculate sentiment as:
(Positive − Negative) / (Positive + Negative)

Temporal Labeling — Assign each filing to its corresponding quarter or year (e.g., 2019Q2, 2021K).

Stock Integration — Merge sentiment time series with stock closing prices to explore co-movement patterns.

Visualization — Plot sentiment trends versus price trajectories and highlight correlation regimes.

📊 Key Results

Average sentiment across AMD filings: approximately −0.6, indicating a generally cautious tone.

Between 2018–2022, sentiment and stock prices move in the same direction, reflecting positive alignment.

After 2022Q3, sentiment diverges from price performance, suggesting optimism decoupled from fundamentals.

Filing tone becomes progressively neutral in recent years, indicating reduced volatility in disclosure sentiment.

📈 Visualization

Below is a visualization of AMD’s sentiment score compared with its stock price (2015–2024),
with shaded regions indicating correlation shifts between textual tone and market performance.

The results reveal a period of strong co-movement (2018–2022),
followed by a decoupling phase (2022–2024), where sentiment weakens as prices continue to rise.

Additional figures, including quarterly filing sentiment trends, are available in
results/
.

🧠 Insights

SEC textual sentiment serves as a leading indicator of corporate tone and risk disclosure.

Positive tone tends to align with stock appreciation during expansion phases.

Divergence between sentiment and market prices may signal information inefficiency or speculative pricing.

Extending this analysis across firms enables sector-level sentiment tracking and market-wide tone aggregation.
