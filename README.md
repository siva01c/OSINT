# OSINT Tools

This repository now includes a **Python script version** of the original Jupyter notebook (`linkedin.ipynb`).

## 1) Setup environment variables

Copy `.env.default` to `.env` and fill in your credentials/API key:

```bash
cp .env.default .env
```

Required variables in `.env`:

- `LINKEDIN_USER`
- `LINKEDIN_PASSWORD`
- `LINKEDIN_TARGET_USERNAME`
- `LINKEDIN_TARGET_NAME`
- `OPENAI_API_KEY`

> Keep `.env` private. It is already ignored by git.

---

## 2) Run as Python script

Main script: `linkedin_tool.py`

### Scrape LinkedIn posts

```bash
python linkedin_tool.py scrape
```

If you need a visible browser window (instead of headless):

```bash
python linkedin_tool.py scrape --headed
```

This generates `posts.json`.

### Start RAG chat UI (Gradio)

```bash
python linkedin_tool.py chat --host 0.0.0.0 --port 7860
```

### Run scrape + chat in sequence

```bash
python linkedin_tool.py all
```

---

## 3) Run with Docker Compose

Build and start the services:

```bash
docker compose up --build
```

Docker Compose now starts:

- `osint` (Python app)
- `selenium` (Selenium + Chrome browser infrastructure)

By default, chat is available at http://localhost:7860 and Selenium Grid at http://localhost:4444.

### Run scraping inside container

```bash
docker compose run --rm osint python linkedin_tool.py scrape
```

The `osint` container is preconfigured to use the Selenium browser service via `SELENIUM_REMOTE_URL=http://selenium:4444/wd/hub`.

### Start chat after scraping

```bash
docker compose up
```

---

## Notes

- Cookies are stored under `cookies/`.
- Embedded vector data is stored under `chromadb/`.
- Scraped posts are saved to `posts.json`.
- LinkedIn may trigger checkpoint/verification challenges. If that happens, complete verification and rerun.
