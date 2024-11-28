# Flask Web Server with Gunicorn

This guide shows how to quickly set up a web server using Flask and Gunicorn.

---

## Prerequisites

- Python 3.6 or newer installed.
- `pip` (Python package manager) installed.

---
<>
## 1. Set Up a Virtual Environment

A virtual environment keeps your project's dependencies isolated.

```bash
python3 -m venv venv  # Create a virtual environment
source venv/bin/activate  # Activate it (Linux/macOS)
venv\Scripts\activate  # Activate it (Windows)
```

## 2. Install Flask and Gunicorn

Install the required packages:

```bash
pip install flask gunicorn
```

## 3. Create a Flask 

make a file called ```app.py``` and add this code:

```bash
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello, Flask!"

if __name__ == "__main__":
    app.run()
```

## 4. Run the App with Gunicorn
Use Gunicorn to run the app:

```bash
gunicorn -w 2 -b 0.0.0.0:8000 app:app
```

### What this does:
* ```-w 2```: Uses 2 worker processes.
* ```-b 0.0.0.0:8000```: Runs on port 8000 and allows connections from any IP.

## 5. Test the Server
Open a browser and go to ```http://<your-IP>:8000```

## 6. (Optional) Run as a Linux Service
### 6.1. Create a Service File
Make a file at ```/etc/systemd/system/flaskapp.service```:
```bash
[Unit]
Description=Flask App
After=network.target

[Service]
User=<your-username>
WorkingDirectory=/path/to/your/project #Note: this is not an actual path, and you will need to write the actual path yourself.
ExecStart=/path/to/your/project/venv/bin/gunicorn -w 2 -b 0.0.0.0:8000 app:app #Note: Again, this isn't an actual path.
Restart=always

[Install]
WantedBy=multi-user.target
```
### 6.2. Start the Service
```bash
sudo systemctl daemon-reload
sudo systemctl enable flaskapp
```