# Python Data Scraper

Python script that scrapes selected data (long/short positions) from IG and Plus500 web pages and appends results to an .ods spreadsheet. It is designed to run hourly (08:00–20:00, local time), capturing timestamped values for later analysis.

Configuration:
- ODS_PATH – target .ods file (default: file.ods)
- RUN_HOURS – which hours to run (default: 8:00 to 20:00)
- IG_URL – IG page to scrape
- PLUS500_URL – Plus500 page to scrape
- CSS selectors / parsing logic used to extract the needed fields
  
Requirements:
- Python 3.9+
- beautifulsoup4
- lxml
- requests
- ezodf
