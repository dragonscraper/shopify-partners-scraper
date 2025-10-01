# 🛍️ Shopify Partners Directory Scraper

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Async](https://img.shields.io/badge/Async-Await-green.svg)](https://docs.python.org/3/library/asyncio.html)
[![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4.0+-orange.svg)](https://www.crummy.com/software/BeautifulSoup/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-red.svg)](https://pandas.pydata.org/)

A powerful, asynchronous web scraper designed to extract comprehensive data from the Shopify Partners Directory. This tool efficiently scrapes partner profiles, contact information, social media links, and business details, saving everything to a structured CSV format.

## ✨ Features

- 🚀 **Asynchronous Processing**: High-performance concurrent scraping with configurable batch sizes
- 🎯 **Comprehensive Data Extraction**: Captures 13+ data points per partner profile
- 🛡️ **Rate Limiting**: Built-in throttling to respect website policies
- 🔄 **Proxy Support**: Optional proxy rotation for enhanced reliability
- 📊 **CSV Export**: Clean, structured data output with UTF-8 encoding
- 🎨 **Beautiful UI**: Clean console output with progress tracking
- ⚡ **Batch Processing**: Efficient handling of large datasets
- 🔍 **Error Handling**: Robust error management and logging

## 📋 Data Extracted

| Field            | Description                          |
| ---------------- | ------------------------------------ |
| **Name**         | Partner company/service name         |
| **Description**  | Detailed business description        |
| **Phone Number** | Contact phone number                 |
| **Website**      | Official website URL                 |
| **Email**        | Contact email address                |
| **Location**     | Primary business location            |
| **Languages**    | Supported languages                  |
| **LinkedIn**     | LinkedIn profile URL                 |
| **Instagram**    | Instagram profile URL                |
| **Facebook**     | Facebook page URL                    |
| **Twitter**      | Twitter/X profile URL                |
| **Youtube**      | YouTube channel URL                  |
| **URL**          | Original Shopify partner profile URL |

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/dragonscraper/shopify-partners-scraper
   cd shopify-partners-scraper
   ```

2. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Run the scraper**
   ```bash
   python main.py
   ```

## 📦 Dependencies

```txt
aiofiles>=23.0.0
asyncio
beautifulsoup4>=4.12.0
httpx>=0.24.0
pandas>=2.0.0
```

## 🏗️ Project Structure

```
shopify-partners-scraper/
├── main.py              # Main application entry point
├── scraper.py           # Core scraping engine
├── urls.txt             # Scraped URLs storage (auto-generated)
├── data.csv             # Output data file (auto-generated)
├── requirements.txt     # Python dependencies
└── README.md           # This file
```

## 🔧 Configuration

### Scraper Settings

The scraper can be customized through the `Scraper` class initialization:

```python
scraper = Scraper(
    timeout=30,                    # Request timeout in seconds
    proxies=None,                  # List of proxy URLs
    requests_per_second=5,         # Rate limiting
    proxy_usage_limit=10          # Max requests per proxy
)
```

### Batch Processing

Control concurrent processing in `main.py`:

```python
# Adjust batch size for your needs
results = await run_in_batches(tasks, max_concurrent_tasks=15)
```

## 📊 Usage Examples

### Basic Usage

```python
from main import Shopify

# Initialize the scraper
shopify = Shopify()

# Run the scraper
import asyncio
asyncio.run(shopify.main())
```

### Custom Configuration

```python
from scraper import Scraper
from main import Shopify

# Create custom scraper with proxies
proxies = [
    "http://proxy1:port",
    "http://proxy2:port"
]

scraper = Scraper(
    timeout=60,
    proxies=proxies,
    requests_per_second=3,
    proxy_usage_limit=5
)

# Use with Shopify class
shopify = Shopify()
shopify.scraper = scraper
```

## 🎯 How It Works

1. **URL Discovery**: Scrapes the Shopify Partners directory page by page
2. **Profile Extraction**: Visits each partner profile and extracts detailed information
3. **Data Processing**: Parses and structures the extracted data
4. **CSV Storage**: Saves data incrementally to prevent data loss
5. **Progress Tracking**: Provides real-time feedback on scraping progress

## 📈 Performance

- **Concurrent Processing**: Up to 15 simultaneous requests
- **Rate Limiting**: Configurable requests per second
- **Memory Efficient**: Processes data in batches
- **Fault Tolerant**: Continues processing even if individual requests fail

## 🛠️ Advanced Features

### Proxy Support

```python
# Add proxy rotation for better reliability
proxies = [
    "http://username:password@proxy1:port",
    "http://username:password@proxy2:port"
]

scraper = Scraper(proxies=proxies)
```

### Custom Headers

```python
# Customize request headers
headers = {
    "User-Agent": "Your Custom User Agent",
    "Accept": "text/html,application/xhtml+xml",
    "Accept-Language": "en-US,en;q=0.9"
}
```

## 📝 Output Format

The scraper generates a CSV file with the following structure:

```csv
Name,Description,Phone Number,Website,Email,Location,Languages,LinkedIn,Instagram,Facebook,Twitter,Youtube,URL
"Company Name","Business description...","+1234567890","https://company.com","contact@company.com","New York, NY","English, Spanish","https://linkedin.com/company","https://instagram.com/company","https://facebook.com/company","https://twitter.com/company","https://youtube.com/company","https://shopify.com/partners/..."
```

## ⚠️ Important Notes

- **Respect Rate Limits**: The scraper includes built-in rate limiting to be respectful to Shopify's servers
- **Legal Compliance**: Ensure you comply with Shopify's Terms of Service and robots.txt
- **Data Usage**: Use scraped data responsibly and in accordance with applicable laws
- **Error Handling**: Monitor the console output for any errors or failed requests

## 🐛 Troubleshooting

### Common Issues

1. **Connection Timeouts**

   - Increase the timeout value in the Scraper configuration
   - Check your internet connection

2. **Rate Limiting**

   - Reduce the `requests_per_second` parameter
   - Increase delays between requests

3. **Proxy Issues**

   - Verify proxy credentials and availability
   - Test proxies individually

4. **Data Quality**
   - Some fields may return "X" if not available
   - Check the website structure for changes

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Shopify for providing the Partners Directory
- BeautifulSoup for HTML parsing
- httpx for async HTTP requests
- pandas for data manipulation

## 📞 Support

If you encounter any issues or have questions, please open an issue on GitHub or contact the maintainers.

---

**Happy Scraping! 🚀**

_Built with ❤️ for the Shopify ecosystem_
