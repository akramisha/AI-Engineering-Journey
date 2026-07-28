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

## 📦 The Data Shape
 
Each task is a dictionary with three fields:
 
```python
{"id": 1, "title": "Learn FastAPI", "done": True}
```
 
Pre-filled with 3 example tasks to start, stored as a **list of dictionaries** — a container (`[ ]`) holding multiple task objects (`{ }`), each with its own key-value pairs.
 
---
 
## 📚 What I'm Learning Today
 
- **`app = FastAPI()`** — FastAPI is a class; `app` is an object (instance) of that class. Calling `app.post(...)` or `app.get(...)` is calling a method on that object, the same way `list.append()` or `string.upper()` work.
- **Decorators (`@app.get("/")`)** — a decorator tells FastAPI "this function answers requests to this path + method." Without it, the function below is just an ordinary Python function FastAPI doesn't know about.
- **Why `/docs` works without me building it** — FastAPI automatically creates a few of its own routes (`/docs`, `/redoc`, `/openapi.json`) the moment `app = FastAPI()` runs, separate from the routes I define myself.
- **List vs. Dictionary** — a list (`[ ]`) is a container holding many things; a dictionary (`{ }`) is one object made of key-value pairs (like one task's `id`, `title`, `done`).
- **Query parameter vs. request body** — a plain function argument like `title: str` is read by FastAPI as a query parameter (`?title=...`), not JSON sent in the body. Getting `POST /tasks` to read `{"title": "..."}` from the actual request body needs a separate model describing that shape — still working through this for Stage 3.
---
 
## 📝 Status
 
Currently on **Stage 3 (Create)** — building `POST /tasks` so a client can add a new task by sending only a `title`, with the server auto-assigning the `id` and defaulting `done` to `false`. Code and full explanation for this stage will go in a separate file once it's working correctly.
 
