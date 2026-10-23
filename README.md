# 0. AI: Scaffolding a Robust API Integration

## Overview
This task demonstrates the integration of Artificial Intelligence into a software development workflow using **Contextual Prompting**. By providing an existing codebase as context along with explicit non-functional requirements, we refactored a Python command-line utility to incorporate secure authentication scaffolding and comprehensive, granular error handling.

---

## Files Included
- `initial_sentiment_analyzer.py`: The original baseline Python script connecting to the public sentiment analysis API without authentication headers or advanced exception handling.
- `sentiment_analyzer.py`: The AI-refactored version incorporating:
  - Secure environment variable credential retrieval (`TEXT_PROCESSING_API_KEY`).
  - Standard HTTP Bearer token authorization headers (`Authorization: Bearer <key>`).
  - Granular exception handling for `requests.exceptions.Timeout` and `requests.exceptions.ConnectionError`.

---

## Key Engineering Enhancements
1. **Secure Credential Management**: Eliminated hardcoded secrets by leveraging the `os` module to read API keys from environment variables (`TEXT_PROCESSING_API_KEY`), failing fast with a clear message to `sys.stderr` if the key is missing or empty.
2. **Robust Error Taxonomy**: Added explicit timeout parameters (`timeout=10`) to network requests and ordered exception handlers from most specific (`Timeout`, `ConnectionError`, `HTTPError`) to most general (`RequestException`), preventing unreachable code blocks and ensuring clear diagnostic feedback.

---

## Usage Instructions

### 1. Set Permissions
Make the script executable from your terminal:
```bash
chmod +x sentiment_analyzer.py
