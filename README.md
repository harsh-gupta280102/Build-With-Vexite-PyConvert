# ⚡ PyConvert — JavaScript to TypeScript AI Studio

> A powerful Python-powered (FastAPI + Modern Web UI) application that ingests JavaScript project folders, visualizes the directory tree and code files, and uses the **Google Gemini API** (with Bring-Your-Own-Key support) to convert your codebase into clean, strictly-typed **TypeScript**.

![PyConvert Studio](https://img.shields.io/badge/Python-3.12+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.110+-009688.svg)
![Gemini AI](https://img.shields.io/badge/Gemini_API-2.5_Flash_%2F_Pro-8b5cf6.svg)
![TypeScript](https://img.shields.io/badge/TypeScript-Ready-3178c6.svg)

---

## ✨ Features

- 📂 **Folder Ingestion & Visual File Tree**:
  - Upload entire JavaScript project folders via browser folder picker or Drag-and-Drop.
  - Scan local directory paths directly from disk.
  - Interactive collapsible directory hierarchy with file-type badges and real-time conversion status indicators (`Pending`, `Converting...`, `Converted`, `Error`).
- ⚡ **Built-in Sample Playground Projects**:
  - **Express & Node.js REST API (JS)**: Test routes, controllers, middleware, JWT auth, and models.
  - **React Dashboard UI (JSX)**: Test components, custom hooks, props interfaces, and state typing.
- 🤖 **Google Gemini API Engine (BYOK - Bring Your Own Key)**:
  - User enters their personal Gemini API Key securely in the UI (stored locally in browser storage).
  - Supports **Gemini 2.5 Flash** (fastest & recommended), **Gemini 2.5 Pro**, **Gemini 1.5 Pro**, and **Gemini 1.5 Flash**.
  - Built-in connection tester & quota validator.
- 🔍 **Side-by-Side Code Studio & Visual Diff Mode**:
  - Split View: JavaScript on the left, converted TypeScript on the right.
  - Visual Diff View: Line-by-line colored diffs highlighting added types, interfaces, generics, and imports.
  - In-place TypeScript editor allowing you to tweak code on the fly before exporting.
  - Prism syntax highlighting with line numbers and quick copy buttons.
- ⚙️ **Smart Config & Dependency Enhancer**:
  - Automatically analyzes dependencies to detect whether the project is React, Express, Vite, Next.js, or Vanilla JS.
  - Generates tailored `tsconfig.json`.
  - Automatically updates `package.json` with appropriate `@types/*` and `typescript` devDependencies.
- 📦 **One-Click Export**:
  - Download the entire converted TypeScript project as a `.zip` archive preserving exact directory layouts and renamed extensions (`.js` → `.ts`, `.jsx` → `.tsx`).
  - Export directly to a target directory on disk.

---

## 🚀 Quick Start

### 1. Installation
Ensure you have Python 3.10+ installed:

```bash
# Clone or navigate to the project directory
cd PyConvert

# Install required Python dependencies
pip install -r requirements.txt
```

### 2. Launch the Application

#### On Windows:
Double-click `run.bat` or run:

```bash
python main.py
```

The app will start the FastAPI backend on `http://127.0.0.1:8000` and **automatically open your web browser**.

---

## 🔑 Entering Your Gemini API Key

1. Click the **"Set API Key"** button in the top right navigation bar.
2. Enter your personal Google Gemini API Key.
   - *Get a free API key at [Google AI Studio](https://aistudio.google.com/app/apikey).*
3. Click **"Test Key Connection"** to verify that your key is active.
4. Click **"Save & Apply Key"**.

---

## 🛠️ How to Convert a Project

1. **Upload or Load a Project**:
   - Click **"Upload Folder"** or drag-and-drop your JavaScript codebase folder into the sidebar.
   - Or click **"Scan Path"** to load a local folder directly from your disk (e.g. `C:/Projects/my-app`).
   - Or click one of the sample buttons (**"⚡ Express API"** or **"⚛️ React UI"**) to test immediately.
2. **Inspect the Code**:
   - Click on any file in the visual explorer tree to view the JavaScript source.
3. **Convert to TypeScript**:
   - **Convert Single File**: Click **"Convert File"** in the top toolbar to convert only the active file.
   - **Convert Entire Project**: Click **"Convert Entire Project (JS → TS)"** in the sidebar to convert all files concurrently with live progress tracking.
4. **Inspect Diff & Edit**:
   - Switch to **"Diff Mode"** to see added interfaces and types highlighted in green.
   - Click **"✏️ Edit"** if you want to tweak any TypeScript code manually.
5. **Download Converted Project**:
   - Click **"Download .ZIP"** to download the complete TypeScript project archive with `tsconfig.json` and updated `package.json`.

---

## 📁 Project Structure

```
PyConvert/
├── main.py                  # Entry point (FastAPI server + auto-browser launch)
├── requirements.txt         # Dependencies (FastAPI, Uvicorn, Requests, etc.)
├── run.bat                  # Windows 1-click launcher
├── README.md                # Documentation
├── app/
│   ├── __init__.py
│   ├── config.py            # Model definitions & specialized prompt templates
│   ├── server.py            # FastAPI REST routing & endpoints
│   ├── services/
│   │   ├── __init__.py
│   │   ├── gemini_service.py # Direct Gemini API client with BYOK & prompt engineering
│   │   ├── project_scanner.py# Local folder scanner, file tree generator, metrics
│   │   ├── analyzer.py       # Framework detector & tsconfig.json generator
│   │   ├── exporter.py       # In-memory ZIP archive builder & disk exporter
│   │   └── sample_projects.py# Built-in sample Express and React JavaScript datasets
└── static/
    ├── index.html           # Single-page Studio web interface
    ├── css/
    │   └── style.css        # Dark glassmorphic design system
    └── js/
        ├── api.js           # REST communication client
        ├── diff.js          # Myers LCS visual diff engine
        ├── editor.js        # Split-pane & Prism syntax highlighter
        ├── tree.js          # Collapsible tree viewer & search filter
        └── app.js           # Main app controller & batch conversion manager
```

---

## 🔒 Security & Privacy

- **Bring Your Own Key (BYOK)**: Your API key is stored only in your local browser storage (`localStorage`) and used for direct requests.
- No source code or keys are transmitted to third-party databases.
