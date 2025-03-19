# 📈 Findata Downloader

A powerful professional CLI for downloading financial data from Yahoo Finance

## 📥 Installation

### Prerequisites
- Python 3.8+
- Uptated pip 

### Installation methods

**1. From PyPI (recommended):**
```bash
pip install findata-downloader
```

**2. From repository Git:**
```bash
pip install git+https://github.com/cabersdev/findata-downloader.git
```

**3. Local development:**
```bash
git clone https://github.com/cabersdev/findata-downloader
cd findata-downloader
pip install -e .
```

## 🚀 Basic usage

### Minimal comand:
```bash
findata TICKER --period INTERVALLO
```
Example to download 1 year od Apple datas:
```bash
findata AAPL --period 1y
```

### Advanced examples:

**1. Intraday data with a 15 minutes interval:**
```bash
findata TSLA --period 5d --interval 15m --format csv
```

**2. Historical data with compression:**
```bash
findata MSFT --period 10y --interval 1d --compress --format parquet
```

**3. Personalized output:**
```bash
findata BTC-USD -p max -i 1d -o ~/financial_data -fn bitcoin_full_history.feather
```

**4. With proxy and verbose mode:**
```bash
findata AMZN -p 1y -i 1wk --proxy socks5://localhost:9050 -v
```

## 🔧 Main options

| Flag               | Description                                  | Accepted values               |
|---------------------|----------------------------------------------|---------------------------------|
| `-p/--period`       | Historical period                             | 1d, 5d, 1mo, 1y, max          |
| `-i/--interval`     | Data frequency                              | 1m, 15m, 1h, 1d, 1wk          |
| `-f/--format`       | Output format                              | csv, json, parquet, feather    |
| `-o/--output`       | Output directory                         | Absolute/relative path     |
| `--compress`        | Gzip compression ability                  | Boolean flag                  |
| `-v/--verbose`      | Detailed output                         | Boolean flag                  |

## 🛠 Common Troubleshooting 

### Error 429 (Too Many Requests)
```bash
# Soluzione 1: Usa un proxy
findata AAPL --period 1y --proxy http://proxy-server:port

# Soluzione 2: Aumenta timeout e retries
findata TSLA --timeout 60 --retries 10
```

### Missing data
```bash
# Verifica la validità del ticker
findata CHECK_TICKER --period 1d

# Prova con intervalli diversi
findata PROBLEMATIC_TICKER --interval 1h
```

### Dependency issues
```bash
# Aggiorna pacchetti chiave
pip install --upgrade yfinance pandas requests
```

## 📚 Supported intervals

| Interval | Maximum period | Notes                           |
|------------|-----------------|--------------------------------|
| 1m         | 7 days        | It requires recent data         |
| 15m        | 60 days       |                                |
| 1h         | 730 days      |                                |
| 1d         | Historical maximum |                                |
| 1wk        | Historical maximum     |                                |

## 📦 Supported formats

| Format   | Compression | Typical sizes | Speed |
|-----------|--------------|--------------------|----------|
| CSV       | gzip         | Medium              | 🟢🟢🟢     |
| Parquet   | Snappy       | Small            | 🟢🟢🟢🟢   |
| Feather   | Non support. | Large             | 🟢🟢🟢🟢🟢 |
| JSON      | gzip         | Large             | 🟢        |

## 📜 License
MIT License - [License details](LICENSE)

## 👥 Contribute
1. Repository fork
2. Create a branch for the features (`git checkout -b feature/awesome-feature`)
3. Changes commit (`git commit -am 'Add awesome feature'`)
4. Branch push (`git push origin feature/awesome-feature`)
5. Open a Pull Request

**Happy data mining!** 🚀
