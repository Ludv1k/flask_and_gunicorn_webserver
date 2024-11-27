# Flask Web Server with Gunicorn

This guide shows how to quickly set up a web server using Flask and Gunicorn.

---

## Prerequisites

- Python 3.6 or newer installed.
- `pip` (Python package manager) installed.

---

## 1. Set Up a Virtual Environment

A virtual environment keeps your project's dependencies isolated.

```bash
python3 -m venv venv  # Create a virtual environment
source venv/bin/activate  # Activate it (Linux/macOS)
venv\Scripts\activate  # Activate it (Windows)

## 2. Install Flask and Gunicorn

Install the required packages:

```bash
pip install flask gunicorn