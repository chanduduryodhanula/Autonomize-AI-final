**Project Summary**

This project is about building an Intelligent Form Agent that can read different types of forms, pull out useful information, answer questions about them, and create short summaries.
It works with both PDFs and images, so whether the form is scanned or typed, the agent can still extract the text and analyze it.

My goal in this assignment was to create a simple but functional pipeline that includes:

* Extracting text from PDFs and images
* Finding key details in the text
* Breaking long text into readable chunks
* Answering questions based on the form
* Summarizing the form
* Handling more than one form together

Everything runs through Python, and I kept it flexible so new features can be added later.

**How the Project Is Organized**
IntelligentFormAgent.py   # Main file with all required functions
requirements.txt
environment.yml
data/                     # Sample forms (PDFs/images)
docs/                     # Any extra notes (optional)
tests/                    # Built-in tests inside main file
README.md
```

The main file creates the modules (`src.ocr`, `src.extractor`, `src.qa`, etc.) in memory so that tests can run smoothly even without a full folder structure.

## **Setting Up the Environment**

### **Option 1: Using Conda**

```
conda env create -f environment.yml
conda activate intelligent-form-agent
```

### **Option 2: Using pip**

```
pip install -r requirements.txt
```

Both methods install OCR tools, PDF reading libraries, and basic NLP tools.

---

## **How to Run the Agent**

### **Basic command (PDF or image)**

```
python IntelligentFormAgent.py --file path/to/your/form.pdf
```

This will:

1. Extract text
2. Try to pull out details like Name or DOB
3. Create a short summary (if models available)
4. Attempt QA on the text

---

## **Examples**

### **1. Summarize a form**

```python
from src.summarizer import Summarizer
from src.ocr import read_pdf_text

text = read_pdf_text("data/form1.pdf")
summ = Summarizer()
print(summ.summarize(text))
```

### **2. Question answering**

```python
from src.qa import QAEngine
qa = QAEngine()

context = "Your extracted form text here..."
qa.answer("What is the applicant's name?", context)
```

### **3. Working with more than one form**

```python
texts = []
for f in ["form1.pdf", "form2.pdf"]:
    texts.append(read_pdf_text("data/" + f))

combined = "\n".join(texts)
qa.answer("What is the total amount mentioned?", combined)
```

---

## **Running Tests**

Tests are included inside the main Python file.
Run them with:

```
pytest
```

They check chunking, regex extraction, and basic error handling.

---

## **Main Libraries Used**

* pytesseract (OCR)
* pillow (image processing)
* pdfplumber (PDF text extraction)
* transformers (QA and summarization)
* torch (model backend)
* pytest (testing)
* numpy / regex (utilities)

These are all included in the requirements.

---

## **Notes**

* If transformers or large models are not installed, the agent still runs and skips those parts gracefully.
* The code is designed to be simple and readable so the entire flow is easy to understand.
* You can extend the agent later by adding semantic search, vector databases, or even a web UI.

---

## **What I Am Submitting**

* Fully working code
* requirements.txt
* environment.yml
* This README
* Example forms in the data folder
* Built-in tests
* Demonstration outputs if needed


