# TAS_Lucent

*TAS Lucent* — clarity and transparency Trade Intelligence & Capital Analytics

TAS - Lucent is a browser-based trade analytics dashboard for reviewing trading performance, risk, attribution, execution quality, and capital efficiency from CSV trade data or manually entered trades.

The project is designed as a single-page HTML application with a dark institutional-style dashboard. Trade data is processed in the browser; the application describes itself as local and data-only, with no external API used for the analysis workflow.

Features:
📊 Overview
The Overview tab provides the main decision dashboard, including:
Net P&L
Win rate
Profit factor
Sharpe
NAV / capital path
Drawdown
ROC per day
Cumulative P&L
Win / loss by day
Direction mix
P&L by instrument
Drawdown from peak
Capital / NAV path
Period filters such as Today, This Week, MTD, QTD, YTD, 30D, 90D, and All

💡 Insights:
The Insights tab breaks performance into actionable dimensions:

Profit factor

Sharpe / Sortino

Calmar / Recovery

Long vs short performance

Win / loss streaks

Time-underwater analysis

Cost drag

Payoff ratio

Top-5 P&L concentration

P&L by hour

P&L by weekday

Monthly P&L

Edge attribution by setup, session, and plan

Contribution analysis using top winners and losers

Local AI-style decision insights based on the calculated dataset

⚖️ Risk Desk

The Risk Desk focuses on portfolio and capital protection:

Daily loss halt

Maximum drawdown halt

Concentration monitoring

Historical 95% VaR

CVaR / expected shortfall

Worst trading days

Worst weeks

Daily P&L volatility

Underwater curve

Instrument concentration

NAV-based risk limits

Risk settings can be configured directly from the desk bar.

📋 Trade Log

The Trade Log provides a searchable and sortable transaction-level view.

Displayed fields include:

Trade ID

Date

Symbol

Direction

Exit

Lots

Gross P&L

Net P&L

Return %

Result

Source

Comment

Pagination and filtering are supported for larger datasets.

✏️ Trade Entry

Manual trades can be entered directly into the application.

Supported fields include:

Symbol

Direction

Date

Entry price

Exit price

Lot size

P&L

Commission

Session

Setup tags

Mood

Plan

Risk managed

Notes

The application includes symbol presets and automatic P&L calculation for supported instruments.

Supported preset categories include crypto, metals/indices, Indian options, and stock options.

📑 Reports

The Report tab provides a more formal performance pack with selectable data sources:

Combined

CSV

Manual

It includes performance KPIs, instrument attribution, execution/trading journal information, and data-driven AI Insights / Needed Action guidance.

🖨️ PDF Export

PDF/print export is available for the dashboard tabs.

Exports are designed to preserve the TAS dashboard visual language and can be used for reporting or review.

The export title follows the format:

TAS OVERVIEW on

with the equivalent tab name for other exports.

CSV Import

The application supports CSV/TXT imports and is designed to work with MT5-style trade exports.

A typical MT5-style structure is:

Time,Deal,Symbol,Type,Direction,Volume,Price,Order,Commission,Fee,Swap,Profit,Balance,Comment 2026.08.24 16:33:08,1508524787,BTCUSD,buy,in,0.01,78 692.61,1837458368,0.00,0.00,0.00,0.00,66.73, 2026.08.24 16:51:51,1508805352,XAUUSD,sell,out,0.01,4 670.06,1838112378,0.00,0.00,0.00,-1.84,64.89,[sl 4670.06]

The importer auto-detects and normalizes supported source formats before analytics are calculated.

Multiple source files can be imported and combined.

Manual P&L Presets

The current manual-entry presets include:

Crypto

BTCUSD

ETHUSD

SOLUSD

Metals / Indices

XAUUSD

XAGUSD

NAS100

US30

SPX500

Indian Options

NIFTY

BANKNIFTY

FINNIFTY

MIDCPNIFTY

SENSEX

Stock Options

RELIANCE

HDFCBANK

ICICIBANK

INFY

TCS

SBIN

Custom symbols are supported as well. For unsupported custom instruments, P&L can be entered manually.

How to Run

This project does not require a build system.

Option 1 — Open locally

Download or clone the repository and open the HTML file in a modern browser.

git clone <YOUR_REPOSITORY_URL> cd <YOUR_REPOSITORY_FOLDER>

Then open:

TAS_v5_layout_optimized_v2.html

in Chrome, Edge, Firefox, or another modern browser.

Option 2 — GitHub Pages

Because the application is a client-side HTML project, it can be published through GitHub Pages.

Create a GitHub repository.

Upload the HTML file and this README.md.

Enable GitHub Pages from the repository settings.

Select the branch/folder containing the HTML file.

Open the generated Pages URL.

Data & Privacy

Trade CSV data is processed in the browser by the application.

The project is intended as a local, data-only analytics tool and its interface explicitly states that data does not leave the machine through an external API workflow.

Do not upload sensitive trade files to a public GitHub repository. A public repository should contain the application source, documentation, and example/sanitized datasets only.

Project Structure

A simple repository can be structured as:

TAS-v5/ ├── TAS_v5_layout_optimized_v2.html ├── README.md └── sample-data/ └── example_mt5.csv

If you later split the application into modules, a more maintainable structure could become:

TAS-v5/ ├── index.html ├── css/ │ └── tas.css ├── js/ │ ├── data.js │ ├── analytics.js │ ├── charts.js │ ├── risk.js │ ├── reports.js │ └── export.js ├── sample-data/ └── README.md

Technical Notes

Frontend: HTML, CSS, JavaScript

Charts: Chart.js

Storage: browser localStorage is used for manual trade persistence

No server/database is required for the current single-file application

Analytics are calculated client-side from imported/manual trade records

The application includes responsive layouts for desktop, tablet, and mobile screens

Important Calculation Notes

The dashboard includes institutional-style metrics such as Sharpe, Sortino, Calmar, Recovery Factor, VaR, CVaR, concentration, expectancy, and t-statistics.

These are analytics derived from the supplied trade history, not guaranteed forecasts of future performance.

The NAV/risk-capital input is particularly important: if the source file contains demo or otherwise unrepresentative account balances, the desk-bar NAV should be overridden with the actual risk capital used for decision-making.

Automatic manual-trade P&L uses the symbol assumptions defined in the application. For instruments with different contract specifications, verify the preset assumptions or enter P&L manually.

Limitations
The application is designed for realized trade analysis and is not a live market data terminal.
It does not provide broker execution.

Risk metrics depend on the quality and completeness of the imported trade history.
Statistical metrics become more meaningful with larger, independent samples.
Browser-local persistence depends on the browser's local storage being available.

PDF export uses the browser print workflow.
Recommended GitHub Repository Setup

For a clean public repository, use:
Repository name: ProTraders

Suggested description:
Institutional-style browser dashboard for trading performance, risk, attribution, trade logging, and report generation.

Suggested topics:
trading trade-analyzer portfolio-analytics risk-management performance-analysis mt5 forex crypto javascript html chartjs

Disclaimer: 
TAS v5 is an analytics and decision-support tool. It is not investment advice, financial advice, or a guarantee of future trading performance.
Always validate imported data, contract assumptions, NAV, risk limits, and calculations before using the dashboard for real capital decisions.

Author: Repository: License:
