# DOI to Publication Date Converter

A Streamlit web application that transforms research paper data by extracting DOIs and mapping them to publication dates from the Crossref API.

## Features

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

## Quick Start

### Local Testing
```bash
pip install -r requirements.txt
streamlit run app.py
```

### Deploy to Streamlit Cloud
See [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) for detailed deployment instructions.

## How It Works

1. **Upload** - Provide a CSV or Excel file containing DOI information
2. **Process** - App extracts DOIs and queries Crossref API
3. **Enrich** - Three date columns are added to your data
4. **Export** - Download formatted Word document and/or updated CSV

## CSV Format Example

| DOI | PUBLICATIONS 2025 |
|-----|---|
| https://doi.org/10.1111/jnc.70160 | Abbondanza, A., Kim, N., ... (2025). Journal of Neurochemistry, 169(7), Article e70160. |
| https://doi.org/10.3390/jcm14248811 | Abreu Marques, I., ... (2025). Journal of Clinical Medicine, 14(24), Article 8811. |

The app will extract and enhance this data with publication dates.

## Technical Details

- **Framework:** Streamlit
- **APIs:** Crossref REST API
- **Python Version:** 3.11+
- **Rate Limiting:** 0.1s between requests (respects Crossref Polite Pool)

## Dependencies

- streamlit - Web application framework
- pandas - Data manipulation
- requests - HTTP client
- python-docx - Word document generation
- openpyxl - Excel file support

## Notes

- Processing 100 papers takes approximately 15-20 seconds
- Crossref API works best with valid email addresses
- DOI pattern extracted: `10.XXXX/XXXXX` (standard DOI format)
- All file uploads are temporary and not stored

## Author

Created for efficient research paper chronological organization.

## License

MIT License
