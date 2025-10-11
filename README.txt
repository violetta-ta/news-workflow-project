# 🧠 AI News Digest Workflow (n8n)

This project demonstrates how an **AI-powered workflow** can automatically fetch, summarize, and deliver personalized news using the **n8n** automation framework.  
It was created as part of my exploration of different types of AI agents (workflow-based, coding, and autonomous) described in my Medium article:  
➡️ [Read the full story on Medium](https://medium.com/@marina.polupanova/three-ways-to-build-ai-agents-and-how-i-put-them-to-the-test-2990914f2922)

---

## 🚀 Overview

The workflow connects several APIs and LLM functions to generate a personalized news digest twice a day.  
It was built in **n8n Community Edition (self-hosted)** and uses OpenAI’s GPT-4o-mini model for summarization.

**Workflow steps:**
1. Fetch latest articles from **GNews API** for multiple topics.  
2. Merge articles into a single dataset.  
3. Use an **LLM node** to generate concise summaries.  
4. Filter out empty or irrelevant summaries.  
5. Save articles for further queries using similarity comparison in a vector database (Weaviate).  
6. Send the summarized digest to the user via email.  

The workflow is fully visual — no custom coding required.

---

## 🧩 Files

n8n_workflow/
├── News workflow 2.json 
└── News retrieval.json 


You can import the JSON file directly into your n8n instance from the main dashboard.

---

## ⚙️ Requirements

- [n8n](https://n8n.io) (Community or Cloud edition)  
- Free or paid [GNews API](https://gnews.io/) key  
- [OpenAI API](https://platform.openai.com/) key  
- SMTP connection for email delivery (Gmail, Outlook, or custom)

---

## 🪄 Setup Instructions

1. Install n8n and Weaviate in the same docker using the instruction on their web-sites:
- https://docs.weaviate.io/deploy/installation-guides/docker-installation
-https://docs.n8n.io/hosting/installation/docker/

2. Create a .env files with the keys, and make it available inside the docker (you can insert respective variable references in the n8n docker's "environment" section)

-N8N_SENDER_EMAIL
-N8N_USER_EMAIL
-N8N_GNEWS_KEY
-N8N_WEAVIATE_KEY
-N8N_OPENAI


3. Create the credentials in your n8n instance with the respective keys, import the workflow

