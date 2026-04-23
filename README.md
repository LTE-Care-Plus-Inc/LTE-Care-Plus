# LTE-Care-Plus

Streamlit apps with Docker. From the repo root, build and run each app with plain Docker (no Compose).

**Billing remittance text parser** (`Dockerfile.billing-scraper`):

```text
docker build -f Dockerfile.billing-scraper -t lte-billing-scraper .
docker run --rm -p 8501:8501 lte-billing-scraper
```

**LBA / auth / PT compliance** (`Dockerfile.lba-checker`):

```text
docker build -f Dockerfile.lba-checker -t lte-lba-checker .
docker run --rm -p 8501:8501 lte-lba-checker
```

Open `http://localhost:8501` in your browser. Run one container at a time if both use port `8501` on the host, or change the host port, e.g. `-p 8502:8501`.

Optional: mount Streamlit secrets, e.g. `-v /path/to/secrets.toml:/app/.streamlit/secrets.toml:ro`. The LBA checker Dockerfile notes that full PDF support would need a derived image (wkhtmltopdf + `pdfkit`).
