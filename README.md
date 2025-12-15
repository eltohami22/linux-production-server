# Linux Production Server Project

## 📌 Project Overview
This project simulates a real production Linux server running an application
using systemd service with security best practices.

## 🧱 Architecture
- Linux Server (Rocky / Ubuntu)
- Non-root user (appuser)
- Python application
- systemd service
- Auto restart after failure or reboot

## ⚙️ Implementation Steps
1. Created a dedicated user for the application
2. Disabled root login via SSH
3. Deployed application under /opt
4. Created systemd service
5. Enabled auto-start on boot
6. Verified logs using journalctl

## 🛠 systemd Service File:

[Unit]
Description=My Production App
After=network.target

[Service]
User=appuser
ExecStart=/usr/bin/python3 /opt/myapp/app.py
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
