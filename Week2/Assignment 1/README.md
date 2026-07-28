# 🛠️ W2 · A1 — Build Your First CRUD API (Python / FastAPI)
 
> Backend Track, Week 2, Assignment 1
 
---
 
## 🎯 What This Assignment Asks
 
Build a small API that manages a to-do list — **Create, Read, Update, Delete (CRUD)** — using an in-memory list (no database yet). Test it through Swagger UI, and publish everything to GitHub with ≥6 honest commits, one per stage.
 
Data lives only in memory for now — it resets every time the server restarts. That's intentional at this stage, not a bug.
 
---

## 🧰 Setup — Python Lane
 
| Step | Command |
|---|---|
| Check Python version | `python --version` |
| Create a virtual environment | `python -m venv venv` |
| Activate it (Windows) | `.\venv\Scripts\Activate` |
| Install the framework | `pip install fastapi` |
| Install the server | `pip install uvicorn` |
| Upgrade pip | `python.exe -m pip install --upgrade pip` |
 
**Framework:** FastAPI — handles routing, JSON parsing, and request/response formatting.
**Server:** Uvicorn — the program that actually runs FastAPI and listens for requests on `localhost`.
**Swagger UI:** Built in for free at `/docs` — no extra setup needed in the Python lane (the JS lane has to install and wire this up manually).
 
---

## 🔑 The Big Idea: Endpoints = Path + Method
 
An **endpoint** is one "door" into the server — defined by a **path** (e.g. `/tasks`) and an **HTTP method** (what kind of action it performs).
 
| CRUD operation | HTTP method | Example endpoint | Meaning |
|---|---|---|---|
| Create | `POST` | `POST /tasks` | Add a new task |
| Read | `GET` | `GET /tasks` · `GET /tasks/3` | List all tasks / get task 3 |
| Update | `PUT` | `PUT /tasks/3` | Change task 3 |
| Delete | `DELETE` | `DELETE /tasks/3` | Remove task 3 |
 
**`{id}` — path parameter:** the changing part of the URL, like the `3` in `/tasks/3`. In FastAPI it's written `{id}` in the route and captured as a function argument — it tells the server *which* task to act on, instead of acting on the whole list.
 
---
## 🪜 The Stages (in order)
 
| Stage | What it builds | Checkpoint |
|---|---|---|
| **0 — Hello, server** | Start FastAPI on `localhost:8000` | `curl -i http://localhost:8000/` returns `200` |
| **1 — First real endpoint** | `GET /` (API description) + `GET /health` (`{"status": "ok"}`) | Both return JSON |
| **2 — Read** | In-memory list of 3 example tasks; `GET /tasks`; `GET /tasks/{id}` | Valid id → `200` + task, unknown id → `404` + error JSON |
| **3 — Create** | `POST /tasks` — client sends `{"title": "..."}`, server assigns `id` + `done: false` | Valid title → `201` + new task, missing/empty title → `400` |
| **4 — Update & Delete** | `PUT /tasks/{id}` (replace), `DELETE /tasks/{id}` (remove) | `200`/`204` on success, `404` on unknown id |
| **5 — Swagger UI** | View & test all endpoints interactively at `/docs` | Full CRUD cycle works via "Try it out" |
| **6 — Publish to GitHub** | Public repo, ≥6 commits, README with run instructions + endpoint table + `curl -i` output + Swagger screenshot | A stranger could run it in under 5 minutes |
| **7 — Bonus: AI rematch** | Prompt an AI to build the same API from a written spec, compare outputs | README has an "AI vs me" section |
 
---
