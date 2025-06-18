# TDS Virtual TA 🤖📚

**Automated Teaching Assistant for IITM's Tools in Data Science Course (May 2025 Batch)**

## 💡 Overview

**TDS Virtual TA** is a virtual assistant designed to help students enrolled in the **Tools in Data Science** (TDS) course of the **IIT Madras Online BS in Data Science** program.
It automatically answers student questions by referencing:

* **Official course content** (as of April 15, 2025)
* **Discourse forum posts** (from January 1, 2025 to April 14, 2025)

The assistant is accessible via a public API endpoint and responds with relevant answers and source links from the forum.

---

## 🚀 Features

* Accepts a student question and optional screenshot (as base64)
* Searches scraped TDS Discourse posts and course materials
* Returns a relevant answer along with supporting forum links
* Fully deployable with a working public API
---

## 📦 API Usage

### **POST** `/api/`

**Endpoint**
`https://ambidextrous-n7qm.onrender.com/query`

**Request Body (JSON)**:

```json
{
  "question": "Your question here",
  "image": "<optional base64-encoded image>"
}
```

**Example CURL request**:

```bash
curl "https://ambidextrous-n7qm.onrender.com/query" \
  -H "Content-Type: application/json" \
  -d "{\"question\": \"Should I use gpt-4o-mini or gpt-3.5 turbo?\", \"image\": \"$(base64 -w0 project-tds-virtual-ta-q1.webp)\"}"
```

**Example Response**:

```json
{
  "answer": "You must use `gpt-3.5-turbo-0125`, even if the AI Proxy only supports `gpt-4o-mini`. Use the OpenAI API directly for this question.",
  "links": [
    {
      "url": "https://discourse.onlinedegree.iitm.ac.in/t/ga5-question-8-clarification/155939/4",
      "text": "Use the model that’s mentioned in the question."
    },
    {
      "url": "https://discourse.onlinedegree.iitm.ac.in/t/ga5-question-8-clarification/155939/3",
      "text": "You just have to use a tokenizer, similar to what Prof. Anand used, to get the number of tokens and multiply that by the given rate."
    }
  ]
}
```
---

## 🛠️ Tech Stack

* **Backend**: FastAPI
* **Deployment**: Render
* **Language**: Python 3.10+
* **Libraries**: BeautifulSoup
---

## 📑 Scraping Script

This repo includes a script to scrape Course Contents and Discourse posts (over a date range).

```bash
python scrape_discource.py
```

```bash
python scrape_cource.py
```

---

## 📁 Project Structure

```
.
├── scraping/
│   ├── scrape_cource.py            # Scraper for TDS course content
│   └── scrape_discource.py         # Scraper for Discourse posts
├── app.py                          # FastAPI app exposing the /query/ endpoint
├── knowledge_base.db               # SQLite DB built from scraped data
├── requirements.txt                # Python dependencies
├── LICENSE                         # MIT License
└── README.md                       # Project documentation
```

---

## 📜 License

This project is licensed under the **MIT License**.
See the [LICENSE](./LICENSE) file for details.

---

## 📬 Submission Details

* **GitHub Repository**: https://github.com/THEPETTA/TDS-Project-1
* **API Endpoint**: https://ambidextrous-n7qm.onrender.com/query

---

## 🌟 Bonus Criteria

*  ✅ Includes Discourse scraping script
*  ✅ MIT license included
*  ✅ Publicly hosted API

---
