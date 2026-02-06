
# OWASP Threat Dragon

## Overview
OWASP Threat Dragon is an open-source threat modeling tool designed to help security professionals, developers, and architects identify and address potential security risks in their applications. The tool assists in modeling threats in software systems through a visual interface and structured methodology. Threat Dragon supports both **web-based** and **desktop-based** applications for ease of use across different environments.

## Available Versions
- **Web App**: Accessible via a web browser, it provides an easy-to-use interface to design and analyze threat models.
- **Desktop App**: Built using **Electron**, this version provides the same functionality in a standalone application that can be run on Windows, macOS, and Linux.

## Steps to Run Locally

### 1. Install OpenSSL (If Needed)
If you don't have **OpenSSL** installed, you can install it using **PowerShell**. Run the following commands in **PowerShell** (as Administrator):
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
choco install openssl -y
```

### 2. Clone the Repository
Clone the project from GitHub and install dependencies:
```bash
git clone repo

```

### 3. Install Dependencies
In your project directory, run:
```bash
npm install
```

## Setting Up Environment Variables

### 1. Generate Tokens using OpenSSL
You need to generate two random 16-byte tokens for encryption keys. Run the following commands in your terminal:
```bash
openssl rand -hex 16
```
This will generate a 32-character hexadecimal string. Run this command **twice** to generate two keys.

### 2. Configure the `.env` File
Rename example.env to .env and use keys generated from openssl.
Update the `.env` file with the following values:
- Replace the generated keys in `ENCRYPTION_KEYS`, `ENCRYPTION_JWT_SIGNING_KEY`, and `ENCRYPTION_JWT_REFRESH_SIGNING_KEY`.

Example:
```bash
ENCRYPTION_KEYS=your_generated_key_1
ENCRYPTION_JWT_SIGNING_KEY=your_generated_key_2
ENCRYPTION_JWT_REFRESH_SIGNING_KEY=your_generated_key_2
```

- If you're using **GitHub Authentication**, replace the `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` values as well:
```bash
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret
```

### 3. Running the Desktop App

#### **Development Mode (Desktop App)**:
To run **OWASP Threat Dragon** as a desktop application in **development mode**, use the following command:
```bash
npm run start:desktop
```

#### **Build Desktop Installer**:
To create an installer for the desktop version, run:
```bash
npm run build:desktop
```

---

### 4. Running the Front-End and Back-End Separately (For Windows Users)

On **Windows**, the front-end and back-end are started separately. Run the following two commands in separate terminal windows:

1. Start the back-end server:
```bash
npm run dev:server
```

2. Start the Vue.js front-end:
```bash
npm run dev:vue
```

### 5. Accessing the Application
Once the server and front-end are running, open your browser and navigate to:
```
http://localhost:8080
```
You should see the application running.

---

## Troubleshooting
- If you encounter issues with `npm run start:desktop`, ensure you have the correct dependencies installed.
- For GitHub OAuth authentication issues, double-check your **client ID** and **client secret** in the `.env` file.
