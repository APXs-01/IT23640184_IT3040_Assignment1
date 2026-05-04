# IT3040 – ITPM Assignment 1
## Transliteration Accuracy Testing – Option 1

**Student:** L.P.S Liyanage (IT23640184)  
**Module:** IT3040 – IT Project Management  
**Year:** 3 | Semester 1  
**Institution:** SLIIT (Sri Lanka Institute of Information Technology)

---

## Overview

This project automates the testing of the **Chat Sinhala transliteration** function available at [https://www.pixelssuite.com/chat-translator](https://www.pixelssuite.com/chat-translator).

The automation script uses **Playwright** to:
- Input 50 chat-style Singlish test cases into the translator
- Capture the actual Sinhala output produced by the site
- Compare it against the expected correct Sinhala output
- Record the result (PASS/FAIL) in the Excel file automatically

---

## Project Structure

```
test_automation/
│
├── test_automation.py          # Main Playwright automation script
├── Assignment 1 - Test cases.xlsx   # Test cases with results
└── README.md                   # This file
```

---

## Prerequisites

Make sure the following are installed on your machine:

- **Python 3.11 or 3.12** – [Download here](https://www.python.org/downloads/)
- **Google Chrome** (recommended) or Chromium

---

## Installation

### Step 1 – Clone the repository

```bash
git clone https://github.com/APXs-01/IT23640184_IT3040_Assignment1.git
cd IT23640184_IT3040_Assignment1/test_automation
```

### Step 2 – Install dependencies

Run the following commands in your terminal:

```bash
pip install -U pip
pip install playwright openpyxl
playwright install
```

---

## Running the Tests

Make sure you are inside the `test_automation` folder, then run:

```bash
python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 3000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

### Command Options

| Option | Description | Default |
|---|---|---|
| `--excel` | Path to the Excel test cases file | Auto-detected |
| `--url` | URL of the transliteration app | pixelssuite.com |
| `--wait-ms` | Wait time (ms) after each transliteration | 5000 |
| `--type-delay-ms` | Delay between keystrokes (ms) | 30 |
| `--slow-mo-ms` | Playwright slow motion delay (ms) | 0 |
| `--save-every` | Save Excel after every N rows | 0 |
| `--keep-open` | Keep browser open after test completes | false |
| `--headless` | Run browser in headless mode | false |

---

## Test Cases

The Excel file contains **50 negative test cases** (Neg_0001 – Neg_0050) where the transliterator fails to correctly convert chat-style Singlish to Sinhala.

All **24 Singlish input types** from Appendix 1 are covered with at least 2 test cases each:

| # | Input Type |
|---|---|
| 1 | Question forms |
| 2 | Command forms |
| 3 | Greetings |
| 4 | Requests |
| 5 | Responses |
| 6 | Repeated Words |
| 7 | Inputs with Punctuation Marks |
| 8 | Romanization / Spelling Variants |
| 9 | Isolated English Word Insertions in Singlish |
| 10 | Multi-Word English Phrases in Singlish |
| 11 | English Digital Terms in Singlish |
| 12 | Platform/App Names in Singlish |
| 13 | English Abbreviations/Acronyms in Singlish |
| 14 | English Clipped Forms in Singlish |
| 15 | Place Names Embedded in Singlish |
| 16 | Person Names Embedded in Singlish |
| 17 | Inputs with Numbers and Numeric Suffixes |
| 18 | Inputs with Currency |
| 19 | Inputs with Time Formats |
| 20 | Inputs with Dates |
| 21 | Inputs with Unit of Measurements |
| 22 | Inputs with Slang and Casual Phrasing |
| 23 | Online Identifiers in Singlish |
| 24 | Inputs Containing Emojis |

### Input Length Categories

| Code | Range |
|---|---|
| S | ≤ 30 characters |
| M | 31 – 299 characters |
| L | 300 – 450 characters |

---

## Excel File Columns

| Column | Description |
|---|---|
| TC ID | Test case ID (Neg_XXXX) |
| Input length type | S / M / L |
| Input | Chat-style Singlish input |
| Expected output | Correct Sinhala translation |
| Actual output | Output captured by automation |
| Status | PASS or FAIL |
| Singlish input types covered | Which of the 24 types apply |
| Evidence or rationale | Justification for type classification |

---

## Notes

- Only the **Chat Sinhala** transliteration function is tested — not Standard Sinhala, backend APIs, or performance/security testing
- None of the test inputs are taken from Appendix 1 or Appendix 2 of the assignment
- The script requires an active internet connection to access the transliteration site
- Press `CTRL+C` to stop the browser after testing is complete
