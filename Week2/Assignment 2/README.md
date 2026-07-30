# 🗣️ Week 2 · Assignment 2 — Frame It as Cases: Work That Speaks for Itself
 
> AI Fluency Course
 
---
 
## 🎯 Brief
 
Write a voice card, get interviewed about real work one question at a time, draft each piece into a three-beat case study (problem → what you did → outcome), add bio + CTA, then show a before/after of a generic AI line vs. an edited version in your own voice.
 
---

## 🎙️ Voice Card
 
> **Clear, honest, practical, simple, no buzzwords**
 
Added to my Claude Project as a standing instruction for how I want project write-ups and posts to sound going forward.
 
---
 
## 🎤 Interview — FastAPI Task API
 
**Why did you build this API?**
I wanted to understand how REST APIs actually work beyond just reading about them — building a full CRUD app end to end was the fastest way to make it click.
 
**Why did you choose FastAPI?**
It's beginner-friendly, and it generates interactive Swagger documentation automatically — I got a testable UI for free without building any frontend.
 
**What was the hardest part?**
Understanding the difference between reading data from query parameters versus a JSON request body. My first `POST`/`PUT` endpoints technically ran, but silently expected the wrong kind of input — I only caught it by testing with the exact `curl` command the assignment specified and seeing a `422` error.
 
**Why did you store data in memory instead of a database?**
That's what this stage of the assignment asked for — a plain Python list. It's simple, and losing the data on restart was actually the point: a lesson about why databases exist, not a bug to avoid yet.
 
**How did you generate IDs?**
Took the last task's `id` and added 1, so every new task gets the next free number.
 
**How did you handle missing tasks?**
Loop through the list looking for a matching `id`; if nothing matches by the end of the loop, raise a `404` with a message naming the exact id that wasn't found — instead of silently returning nothing.
 
---

 ## 📋 Case Study — FastAPI Task API
 
### Problem
I wanted to understand how REST APIs work beyond theory by building a complete CRUD application using FastAPI.
 
### What I Did
- Built `GET /tasks` and `GET /tasks/{id}`, with a proper 404 when an id doesn't exist
- Added `POST /tasks` with input validation — empty titles get rejected with a 400
- Generated new task IDs automatically instead of hardcoding them
- Implemented `PUT /tasks/{id}` and `DELETE /tasks/{id}`, matching each to the correct status code (200 and 204)
- Fixed a real bug where my endpoints were reading query parameters instead of JSON bodies, by learning how Pydantic models define a request body's shape
- Added Swagger UI documentation, testable directly in the browser
- Built a bonus `/stats` endpoint that computes totals instead of just storing them
### Outcome
A fully functional CRUD API with automatic documentation, published on GitHub. Along the way I learned how FastAPI handles routing, validation, HTTP methods, and status codes — and picked up the habit of testing with the exact request format a real client would send, not just whatever ran without crashing.
 
---
 
## 👤 Bio
 
I'm an IT graduate learning backend development and AI engineering through hands-on projects.
 
## 📣 CTA
 
Feel free to connect, or check out my GitHub.
 
---
