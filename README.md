# MediScan AI
### AI-Powered Prescription & Lab Report Reader

MediScan AI is an OCR-powered medical document information extraction application that converts prescription images and laboratory reports into structured JSON.

Built using Python, Streamlit, Tesseract OCR, and optional LLM integration, the application extracts important medical information and provides a human-review interface to verify and correct extracted fields.

**Key principle:** Extract information, preserve uncertainty, and keep humans in control.

## Features

- Upload prescription images and PDF documents.
- Extract text using Tesseract OCR.
- Identify medicine names, strengths, doses, and medication timings.
- Extract start dates and end dates when explicitly stated.
- Extract laboratory test names, values, units, and reference ranges.
- Generate structured JSON output.
- Provide field-level confidence estimates.
- Review and correct extracted information.
- Optional Groq-powered LLM extraction.
- Rule-based fallback without an API key.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend processing |
| Streamlit | Interactive application |
| Tesseract OCR | Text recognition |
| Regex | Rule-based extraction |
| Groq API | Optional LLM extraction |
| Llama 3.3 70B Versatile | Optional language model |
| JSON | Structured output |

## Application Workflow

1. Upload a prescription or lab report.
2. Process the document using OCR.
3. Extract and classify the document text.
4. Identify relevant medical fields.
5. Calculate field-level confidence estimates.
6. Display extracted information for human verification.
7. Correct and review the information before saving.

## Installation

**1. Clone the repository**

```bash
git clone https://github.com/YOUR_USERNAME/mediscan-ai.git
cd mediscan-ai
```

**2. Create a virtual environment**

```bash
python -m venv .venv
```

**3. Activate the environment**

Windows:

```powershell
.\.venv\Scripts\Activate.ps1
```

**4. Install dependencies**

```bash
pip install -r requirements.txt
```

**5. Install Tesseract OCR**

Windows installation:
https://github.com/UB-Mannheim/tesseract/wiki

Verify:

```bash
tesseract --version
```

**6. Configure environment variables**

Copy `.env.example` to `.env` and add your own Groq API key if LLM extraction is enabled.

```env
GROQ_API_KEY=your_api_key_here
LLM_BASE_URL=https://api.groq.com/openai/v1
LLM_MODEL=llama-3.3-70b-versatile
```

**7. Run the application**

```bash
python -m streamlit run app.py
```

Open: http://localhost:8501

## Example Output

```json
{
  "document_type": "prescription",
  "medicines": [
    {
      "name": "Paracetamol",
      "strength": "500 mg",
      "dose": "1 tablet",
      "times": ["08:00", "20:00"],
      "food": "after",
      "startDate": "2026-11-17",
      "endDate": "2026-11-19"
    }
  ]
}
```

Example values are illustrative and must be verified against the source document.

## Testing and Evaluation

The application is intended to be tested against at least 20 synthetic, public, or self-created medical document samples.

Evaluation metrics:
- Field-level accuracy
- Precision
- Recall
- F1-score
- Date normalization accuracy

Actual evaluation results will be documented after testing.

## Medical Safety

- No automatic invention of missing medication information.
- No automatic AM/PM assumptions.
- No inference of medication start dates from prescription dates.
- Human verification before medical information is used.
- No real patient records used for testing.

**Disclaimer:** This application supports medical document information extraction. It does not diagnose diseases, recommend treatment, or replace professional medical judgement.

## Future Improvements

- Handwritten prescription recognition.
- Indian language support.
- Improved abbreviation recognition.
- Better OCR accuracy.
- Firebase integration.
- Secure storage of verified records.
- Medication reminder integration after human approval.

## AI Tools Used

- ChatGPT: Development assistance, debugging, and documentation.
- Claude Code: AI-assisted coding, where used.
- Groq API: Optional structured information extraction.
- Llama 3.3 70B Versatile: Optional LLM model.

Only tools actually used should remain in this list.

## Security

- Keep `.env` out of Git.
- Never commit API keys or passwords.
- Never upload real patient records.
- Use `.env.example` for configuration documentation.

## Author

**Kopparthi Lokesh**

Computer Science Engineering | AI & ML

[LinkedIn](https://www.linkedin.com/in/kopparthilokesh/)

## License

Developed as an internship assignment for TheCarePal AI-04.
