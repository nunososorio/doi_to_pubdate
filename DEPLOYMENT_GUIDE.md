# Streamlit App Deployment Guide

## Quick Start (Local Testing)

To test the app locally first:

```bash
streamlit run app.py
```

This will open the app in your default browser at `http://localhost:8501`

## Deploy to Streamlit Cloud

Follow these steps to deploy to streamlit.io:

### 1. Push Code to GitHub
The app needs to be in a GitHub repository. If not already done:

```bash
cd c:\Users\nunoo\Documents\GitHub\doi_to_pubdate
git init
git add .
git commit -m "Add Streamlit app for DOI paper sorter"
git remote add origin https://github.com/YOUR_USERNAME/doi_to_pubdate.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Deploy via Streamlit Cloud

1. Go to https://share.streamlit.io/
2. Sign in with your GitHub account (create one if needed)
3. Click "New app" button
4. Select your repository: `doi_to_pubdate`
5. Select branch: `main`
6. Set main file path: `app.py`
7. Click "Deploy!"

The app will be available at: `https://share.streamlit.io/YOUR_USERNAME/doi_to_pubdate/main/app.py`

### 3. Understanding the App

**Features:**
- Upload CSV or Excel files with DOI data
- Automatically extracts DOI identifiers from any column
- Queries Crossref API for publication dates (Print, Online, Issued)
- Determines the earliest available date for accurate chronological sorting
- Generates a formatted Word document organized by month/year
- Allows download of both the Word document and updated CSV with date columns

**Input Requirements:**
- CSV or Excel file with DOI information
- Email address for Crossref API (pre-filled with generic academic email)

**Output Files:**
- `Chronological_Papers.docx` - Sorted Word document grouped by publication month
- `Papers_with_Dates.csv` - Updated spreadsheet with extracted dates

## File Structure

```
doi_to_pubdate/
├── app.py                    # Main Streamlit app
├── requirements.txt          # Python dependencies
├── .streamlit/
│   └── config.toml          # Streamlit configuration
├── 1302_2025_ICVS_PUBS.csv  # Test data
└── README.md                # This file
```

## Troubleshooting

**App loads slowly:**
- Normal with Streamlit Cloud on first load
- The Crossref API queries add processing time (~0.1s per DOI per Polite Pool rate limits)

**API endpoint returns errors:**
- Check your email address is valid Format
- Crossref requires valid User-Agent with email for Polite Pool access
- Built-in default email should work for most cases

**CSV encoding issues:**
- App defaults to 'latin-1' encoding (handles special characters in publication names)
- Can be adjusted in the `pd.read_csv()` line if needed

## Additional Notes

- The app respects Crossref API rate limits (0.1s delay between requests)
- Processing 100 papers takes about 15-20 seconds
- All processing happens server-side; uploaded files are not stored
- DOI patterns extracted: Format like "10.1234/example"
