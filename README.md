# DOI to Publication Date Converter

A Streamlit web application that transforms research paper data by extracting DOIs and mapping them to publication dates from the Crossref API.

## ✨ Features

✅ **File Upload Support** - Accepts both CSV and Excel (.xlsx) files  
✅ **DOI Extraction** - Automatically extracts DOI identifiers from any column  
✅ **Multi-Date Support** - Fetches three date types:
- Published Print (journal issue date)
- Published Online (early online publication)
- Issued (Crossref metadata issue date)

✅ **Smart Date Selection** - Determines the earliest available date for accurate chronological sorting  
✅ **Word Document Export** - Generates formatted .docx file organized by publication month  
✅ **CSV Export** - Downloads updated spreadsheet with all date columns  
✅ **Progress Tracking** - Live progress bar showing API processing status

## 🚀 Quick Start

### Local Testing
```bash
pip install -r requirements.txt
streamlit run app.py
```
App opens at `http://localhost:8501`

### Deploy to Streamlit Cloud

1. **Push to GitHub** (already done ✓)

2. **Go to:** https://share.streamlit.io/
   - Sign in with your GitHub account
   - Click "New app"
   - Select: **nunososorio/doi_to_pubdate**
   - Branch: **main**
   - File path: **app.py**
   - Click "Deploy!"

3. **Access your live app** at: `https://share.streamlit.io/nunososorio/doi_to_pubdate/main/app.py`

The app automatically redeploys on every push to GitHub.

## 📊 How It Works

1. **Upload** - Provide a CSV or Excel file with DOI data
2. **Process** - App extracts DOIs and queries Crossref API
3. **Enrich** - Adds 4 date columns to your data:
   - `Extracted_DOI` - Clean DOI identifier
   - `Published_Print` - Print publication date
   - `Published_Online` - Online publication date
   - `Issued_Any` - General issue date
   - `Best_Available_Date` - Earliest date (used for sorting)
4. **Export** - Download formatted Word document and/or updated CSV

## 📋 Input Format

Expects CSV or Excel with DOI information in any column:

| DOI | Citation |
|-----|---|
| https://doi.org/10.1111/jnc.70160 | Abbondanza, A., et al. (2025). Journal of Neurochemistry... |

## 📥 Output Formats

1. **Word Document (.docx)**
   - Organized by publication month/year
   - Includes full citation, DOI, and date
   - Formatted with headings and bullet points

2. **CSV Export**
   - Original data + all date columns
   - Ready for further analysis

## ⚙️ Technical Details

| Aspect | Details |
|--------|---------|
| Framework | Streamlit |
| API | Crossref REST API |
| Python | 3.11+ |
| Rate Limit | 0.1s between requests (respects Crossref Polite Pool) |
| Processing Speed | ~0.15-0.2s per DOI |

## 📚 Dependencies

Install with: `pip install -r requirements.txt`

- **streamlit** - Web application framework
- **pandas** - Data manipulation
- **requests** - HTTP client for API calls
- **python-docx** - Word document generation
- **openpyxl** - Excel file support

## 🔧 Configuration

- Default email for Crossref API: `researcher.data@academic-institution.edu`
- Change in app UI for better rate limits
- Max upload size: 200MB
- All uploads processed temporarily, not stored

## 💡 Usage Tips

- Processing 100 papers takes ~15-20 seconds
- Not all papers have all date types (missing dates are OK)
- DOI pattern: `10.XXXX/XXXXX` (standard DOI format)
- Works with DOI URLs or raw identifiers
- File uploads are never permanently stored

## 🎯 Test Data

Included: `1302_2025_ICVS_PUBS.csv` - 9 sample papers to test the app

## 📄 License

MIT License

## 👤 Author

Created for efficient research paper chronological organization.
