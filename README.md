# Intelligent PDF Summarizer

This project demonstrates an **AI-powered PDF summarization pipeline** using **Azure Durable Functions**, **Azure AI Services**, and **Blob Storage**.

When a PDF is uploaded to Azure Blob Storage, the system:

1. **Extracts text** using **Azure Document Intelligence (Form Recognizer)**
2. **Summarizes the content** using **Azure OpenAI GPT**
3. **Saves the summary** as a `.txt` file back to Blob Storage

> **Demo Video:** [Watch on YouTube](https://youtu.be/Mf24fIWuZaA)

---

## Project Architecture

```
Blob Upload (.pdf)
        ⬇
[Blob Trigger Function]
        ⬇
[Durable Orchestration]
    ├─ analyze_pdf (Document Intelligence)
    ├─ summarize_text (Azure OpenAI)
    └─ write_doc (Save .txt to blob)
```

---

## Key Technologies

- **Azure Blob Storage** – file upload & output container
- **Azure Durable Functions** – orchestrates processing steps
- **Azure Document Intelligence (Form Recognizer)** – PDF text extraction
- **Azure OpenAI** – GPT-based content summarization
- **Python** – function logic

---

## Deployment Status

> Due to **Azure OpenAI quota limitations**, the final infrastructure was **not deployed via `azd up`**.

---

## Local Testing

To test locally, set the following environment variables:

```env
BLOB_STORAGE_ENDPOINT=your-connection-string
COGNITIVE_SERVICES_ENDPOINT=https://<form-recognizer>.cognitiveservices.azure.com/
AZURE_OPENAI_ENDPOINT=https://<openai-service>.cognitiveservices.azure.com
AZURE_OPENAI_KEY=your-openai-key
AZURE_OPENAI_DEPLOYMENT=
AZURE_OPENAI_API_VERSION=
```

Then run the functions host locally:

```bash
func start --verbose
```

---

[![Watch the demo](https://img.youtube.com/vi/Mf24fIWuZaA/0.jpg)](https://youtu.be/Mf24fIWuZaA)