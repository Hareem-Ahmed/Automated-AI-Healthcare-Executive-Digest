# 🤖 Automated AI Healthcare Executive Digest

An end-to-end automated pipeline that ingests multi-source healthcare news feeds (RSS), filters and summarizes key industry developments using Google Gemini (via system instructions enforced for HTML rendering), and delivers a cleanly structured, responsive email digest via Gmail.

---

## 📸 Final Output Preview

![Email Preview](assets/email_preview.png)

---

## 🏗️ System Architecture & Workflow

```
[ 📡 RSS Feeds ] ──► [ 🧩 Text Aggregator ] ──► [ 🧠 Gemini 3.5 Flash ] ──► [ 📧 Gmail API ]
```

1. **Trigger & Aggregation:** Fetches fresh industry articles from curated RSS feeds and aggregates title, link, and metadata payloads using Make.com's Text Aggregator.
2. **AI Processing:** Generates structured executive summaries using Google Gemini, leveraging system prompt constraints to force output directly as native HTML tags (`<h2>`, `<h3>`, `<strong>`, `<ul>`, `<a>`).
3. **Delivery:** Sends responsive, styled HTML emails to subscribers via Gmail API integration without requiring external converter nodes.

---

## 💡 Prompt Engineering & Technical Highlights

* **Direct HTML Encodings:** Solved plain-text rendering issues by constraining Gemini via System Instructions to output semantic HTML tags instead of standard Markdown, ensuring native rendering across all major web and mobile email clients.
* **Deterministic Output Parsing:** Formatted prompt templates with explicit section delineations to maintain consistent categorization:
  1. *Big Tech & Global Trends*
  2. *New Startups & Launch Activity*
  3. *Accelerators & VC Investments*
* **Fault Tolerance:** Managed empty RSS payload states by implementing strict variable checks prior to invoking LLM inference calls.

---

## 🛠️ Tech Stack & Integration

* **Orchestration:** Make.com
* **LLM Engine:** Google Gemini API (`gemini-3.5-flash`)
* **Integrations:** RSS / Webhook feeds, Gmail API
* **Formatting Language:** Native Semantic HTML5 / CSS inline styles

---

## 🚀 How to Replicate

1. Clone this repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/ai-healthcare-newsletter-automation.git](https://github.com/YOUR_USERNAME/ai-healthcare-newsletter-automation.git)
   ```
2. Import `blueprint.json` into your [Make.com](https://make.com) account.
3. Re-authorize your Google Gemini API key and Gmail connection modules.
4. Copy the prompts from `/prompts/system_prompt.md` into your Gemini module's System Instructions parameter.
5. Enable scenario scheduling.
