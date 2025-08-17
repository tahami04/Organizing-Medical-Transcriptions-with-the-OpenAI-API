
# 📋 Organizing Medical Transcriptions with the OpenAI API

This project leverages the power of large language models to extract structured medical information from unstructured natural language transcriptions using the OpenAI API.

> 🔬 Built as part of a portfolio project for the **Lakeside Healthcare Network**.

---

## 🚀 Project Overview

Medical professionals often document patient encounters in free-text transcriptions that include symptoms, diagnoses, and treatment plans. These are difficult to process automatically for downstream applications like insurance or medical record keeping.

This project aims to:
- Extract key information such as **age**, **medical specialty**, and **recommended treatment/procedure**
- Match the treatment to its **ICD-10 code**
- Store results in a structured **pandas DataFrame**

---

## 🧠 What This Project Does

✅ Load and parse anonymized medical transcriptions  
✅ Use the OpenAI Function Calling API to extract structured fields  
✅ Map treatments to appropriate ICD-10 codes using GPT  
✅ Save results as a structured DataFrame (`df_structured`)

---

## 📁 Files & Structure

```
.
├── OptimizingMedicalRecord.ipynb             # Main notebook containing the implementation
├── transcriptions.csv     # Input dataset (anonymized)
├── README.md                  # Project documentation
```

---

## 📦 Requirements

- Python 3.9+
- OpenAI SDK v1.x
- pandas

Install via:

```bash
pip install openai pandas
```

---

## 🔐 OpenAI API Key Setup

To use the OpenAI API, you'll need to provide your own API key.

1. Get your API key from [https://platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys)
2. Set your key as an environment variable:

### For macOS/Linux:
```bash
export OPENAI_API_KEY='your-api-key-here'
```

### For Windows (CMD):
```cmd
set OPENAI_API_KEY=your-api-key-here
```

Or use a `.env` file and load it using `python-dotenv`.

In the notebook, the API is accessed like this:

```python
import os
from openai import OpenAI

api_key = os.getenv("OPENAI_API_KEY")
if api_key is None:
    raise ValueError("❌ OPENAI_API_KEY environment variable not set. Please add your API key.")
client = OpenAI(api_key=api_key)
```

---

## 🧪 How to Run

1. Clone this repo:
```bash
git clone https://github.com/tahami04/Organizing-Medical-Transcriptions-with-the-OpenAI-API
cd medical-transcription-structuring
```

2. Open the notebook:

```bash
jupyter notebook OptimizingMedicalRecord.ipynb
```

3. Run all cells to:
- Load the transcription data
- Extract key fields using OpenAI
- Match ICD-10 codes
- View or export `df_structured`

---

## 📊 Example Output (df_structured)

| age | medical_specialty       | recommended_treatment                                     | icd_code                        |
|-----|--------------------------|------------------------------------------------------------|----------------------------------|
| 23  | Allergy                  | Zyrtec, loratadine, Nasonex                                | ICD-10: J30.1 – Allergic rhinitis |
| 41  | Orthopedic               | Operative fixation for Achilles rupture                    | ICD-10: S86.0 – Achilles injury   |

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).
