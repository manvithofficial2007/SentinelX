# SentinelX

> **A Privacy-Preserving Cyber Fraud Detection and Digital Evidence Integrity Platform Using Threat Intelligence**

**IBM SkillsBuild Cyber Security BootCamp 2026 — BharatCares**  
**Author:** Manvith  
**Submission Files:** `Manvith_SentinelX.ipynb` · `requirements.txt` · `Manvith_ProjectReport.docx` · `README.md`

---

## Problem Statement

Cyber fraud — phishing URLs, smishing, vishing, and social-engineering attacks — causes significant financial and reputational harm to individuals and organisations worldwide. Most threat-intelligence tools require paid subscriptions or external API keys, making them inaccessible to students, small organisations, and first-responders. SentinelX addresses this gap with a fully offline, privacy-preserving, open-source educational prototype.

---

## Features

| Feature | Description |
|---------|-------------|
| **URL Analysis** | Validates URL format; detects IP-based hosts, URL shorteners, suspicious TLDs, brand impersonation, @ symbol tricks, and more. |
| **Message Analysis** | Analyses SMS/email text for urgency language, prize/reward lures, threat language, sensitive-data requests, impersonation, and OTP mentions. |
| **Risk Scoring** | Transparent Low / Medium / High classification with documented thresholds and per-indicator weights. |
| **Evidence Integrity** | Computes SHA-256 hash of local files; re-hash to detect tampering. |
| **Incident Records** | Assembles structured incident records from analysis results, with recommendations. |
| **Report Export** | Exports incident reports as plain text and JSON. |
| **Test Suite** | 20 automated test cases covering all major features. |

---

## Technologies Used

- **Python 3.8+** — all application logic
- **Jupyter Notebook** — interactive implementation and demonstration
- **Standard library only for core logic:** `re`, `hashlib`, `json`, `os`, `datetime`, `textwrap`, `urllib.parse`, `pathlib`
- **No Node.js, Express, PHP, Java, or paid API keys required**

---

## Project File Structure

```
project-root/
├── Manvith_SentinelX.ipynb      # Main Jupyter Notebook (complete implementation)
├── requirements.txt             # Python package requirements
├── Manvith_ProjectReport.docx   # Formal project report (Microsoft Word)
├── README.md                    # This file
├── sentinelx_report.txt         # Generated at runtime — plain-text incident report
├── sentinelx_report.json        # Generated at runtime — JSON incident report
└── synthetic_evidence.txt       # Generated at runtime — synthetic evidence demo file
```

> Files prefixed with `sentinelx_report.*` and `synthetic_evidence.txt` are **generated when the notebook is run** and are not included in the repository by default.

---

## Python Version Requirements

- **Minimum:** Python 3.8
- **Recommended:** Python 3.10 or higher
- Verify your version: `python --version`

---

## Installation Instructions

### 1. Clone or download the project

```bash
git clone <repository-url>
cd sentinelx
```

Or download and unzip the project archive, then `cd` into the folder.

### 2. (Recommended) Create a virtual environment

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

This installs `jupyter`, `notebook`, and `ipykernel`. All core logic uses the Python standard library only.

---

## Instructions to Run the Jupyter Notebook

```bash
jupyter notebook Manvith_SentinelX.ipynb
```

In the browser interface that opens:

1. Select **Kernel → Restart & Run All** to execute all cells from top to bottom.
2. The notebook will print demonstration outputs and test results directly below each cell.
3. Two report files (`sentinelx_report.txt`, `sentinelx_report.json`) and one synthetic evidence file are created in the working directory.

**The notebook requires no secret credentials, API keys, or internet access.**

---

## Dataset Information

SentinelX uses **synthetic, hand-crafted examples** for all demonstration and testing:

- **Synthetic URLs** — fabricated strings that represent common phishing URL patterns. They are never fetched or visited.
- **Synthetic messages** — manually written SMS/email samples that mimic known phishing language patterns.
- **Synthetic evidence file** — a plain-text file generated at runtime to demonstrate SHA-256 hashing.

### Synthetic-Data Disclosure

> **All data in this project is synthetic.** No real phishing URLs, real victim messages, or real personal information are included. The synthetic examples are designed to exercise the heuristic detection logic and do not represent any real incident, real person, or real organisation.

### Optional Real-World Dataset

If you wish to extend SentinelX with a real phishing URL dataset, the following publicly available research datasets are recommended:

- **PhishTank** — <https://www.phishtank.com/developer_info.php> (free API, registration required)
- **OpenPhish** — <https://openphish.com/> (community feed available)
- **UCI Phishing Websites Dataset** — available on the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/phishing+websites)

> SentinelX does not download or depend on any of these datasets. Integration is left as a future enhancement.

---

## Expected Outputs

After running all notebook cells:

1. **URL analysis output** — risk level, score, and per-indicator descriptions for each demo URL.
2. **Message analysis output** — risk level, score, and per-indicator descriptions for each demo message.
3. **Evidence integrity demo** — SHA-256 hash before and after synthetic file modification.
4. **Incident report** — printed to the notebook and saved as `sentinelx_report.txt` and `sentinelx_report.json`.
5. **Test results** — 20 test cases with PASS/FAIL status and a summary line.

---

## Test Instructions

Tests are embedded directly in the notebook (Section 11). To run them:

1. Open the notebook in Jupyter.
2. Run all cells (Kernel → Restart & Run All).
3. Scroll to Section 11 — the test output shows individual PASS/FAIL for each of the 20 test cases.
4. The final summary line shows total passed / total failed.

To run just the tests outside the notebook (if you extract the code to a `.py` file):

```bash
python sentinelx_tests.py
```

---

## Limitations and Ethical Considerations

- **Heuristic only** — pattern matching cannot guarantee detection of all phishing attempts. A passing score does not mean a URL or message is safe.
- **No URL fetching** — SentinelX never opens or fetches URLs. Structural analysis cannot detect page-level phishing content.
- **False positives** — legitimate messages and URLs can trigger indicators (e.g., a real bank SMS may mention "OTP").
- **Static threat lists** — suspicious TLD and brand-keyword lists are static and may become outdated.
- **Not for legal use** — SHA-256 hashing establishes content consistency but does not satisfy chain-of-custody requirements for legal proceedings.
- **Educational prototype only** — do not use SentinelX as the sole tool for security enforcement or legal decisions.
- **Privacy** — the tool does not store, log, or transmit any user input, URLs, or message content.

---

## References

1. Anti-Phishing Working Group (APWG). *Phishing Activity Trends Reports*. <https://apwg.org/resources/apwg-reports/>
2. CERT-In. *Indian Computer Emergency Response Team*. <https://www.cert-in.org.in/>
3. NIST. *FIPS PUB 180-4: Secure Hash Standard (SHS)*. <https://csrc.nist.gov/publications/detail/fips/180/4/final>
4. PhishTank. *Community Phishing URL Database*. <https://www.phishtank.com/>
5. OpenPhish. *Phishing Intelligence*. <https://openphish.com/>
6. Python Software Foundation. *Python 3 Standard Library Documentation*. <https://docs.python.org/3/library/>
7. OWASP. *Phishing Prevention Cheat Sheet*. <https://cheatsheetseries.owasp.org/cheatsheets/Phishing_Prevention_Cheat_Sheet.html>
8. IBM. *IBM SkillsBuild Cyber Security BootCamp 2026*. Conducted by BharatCares.

---

*SentinelX — IBM SkillsBuild Cyber Security BootCamp 2026, BharatCares. All examples are synthetic.*
