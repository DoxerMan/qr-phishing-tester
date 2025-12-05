# QR Phishing Tester (Web)

A simple web-based tool that lets you upload an image containing a QR code, decodes the QR content, and performs basic phishing-risk analysis on the URL.  
It is intended **for educational and defensive security awareness purposes only**, not for creating or delivering phishing content.

## Features

- Upload a PNG/JPEG image containing a QR code.
- Decode the QR code into text using `pyzbar`.
- Detect whether the QR content is a URL.
- Apply a small, rule-based analyzer that looks for:
  - Non-HTTPS URLs.
  - Suspicious top-level domains (e.g., `.zip`, `.xyz`).
  - Use of raw IP addresses instead of domain names.
  - Very long URL paths.
  - Login-related keywords in the URL path.
- Return a risk score (0–100) and a verdict:
  - 0–30: Likely safe
  - 31–70: Suspicious
  - 71–100: Likely phishing

These heuristics are inspired by common "quishing" and phishing patterns described in modern QR security and phishing awareness articles.  

## Installation

```bash
git clone https://github.com/DoxerMan/qr-phishing-tester.git
cd qr-phishing-tester
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
```

## Usage

```bash
python app.py
```

Then open your browser and go to:

- http://127.0.0.1:5000/

Upload an image that contains a QR code.  
If the QR code contains a URL, you will see:

- The decoded URL.
- A risk score (0–100).
- A verdict (Likely safe / Suspicious / Likely phishing).
- A list of rules that contributed to the score.

## Limitations

- This is **not** a production-grade phishing detector.
- It uses a simple, transparent rule-based engine only.
- It does not contact any external reputation or threat-intelligence services.
- False positives and false negatives are expected.

## Ethics and legal notice

This project is provided strictly for:

- Learning about QR code risks.
- Demonstrating basic URL analysis techniques.
- Security awareness and testing in controlled environments.

You are responsible for ensuring that any use of this project complies with applicable laws and policies.  
Do not use it to create, host, or deliver phishing content of any kind.
