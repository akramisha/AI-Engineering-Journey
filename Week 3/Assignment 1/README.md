# Task API — SQLite Edition

A simple CRUD API for managing tasks, backed by a real SQLite database instead of an in-memory list. This project builds on an earlier in-memory version of the same API — the endpoints stay the same, but the data now survives a server restart.

> 🚧 **Status: Work in progress.** The database and endpoints are still being built out. See the [Progress](#progress) section below for what's done so far.

## Why SQLite

SQLite was chosen because it's a lightweight, file-based database that requires no separate server or installation. The entire database lives in a single file (`tasks.db`), which makes it easy to set up, easy to inspect, and perfect for a small project like this one.

## Where the database lives

The database file is created automatically at:

```
tasks.db
```

in the project root, the first time the app runs. If the file or the `tasks` table doesn't exist yet, they're created automatically — no manual setup required.

## Tech stack

- **Language:** Python
- **Database:** SQLite
- **Library:** `sqlite3` (or `SQLModel`)

## Database schema

**Table:** `tasks`

| Column | Type              | Notes                  |
|--------|-------------------|-------------------------|
| id     | integer, primary key | Auto-generated          |
| title  | text              | Required                |
| done   | boolean           | Defaults to `false`     |

## API endpoints (planned)

| Method | Endpoint       | Description                     |
|--------|----------------|----------------------------------|
| GET    | `/tasks`       | Get all tasks                    |
| GET    | `/tasks/{id}`  | Get a single task by id          |
| POST   | `/tasks`       | Create a new task                |
| PUT    | `/tasks/{id}`  | Update an existing task          |
| DELETE | `/tasks/{id}`  | Delete a task                    |

Unknown ids return `404`, invalid requests return `400`.

## How to run the project

```bash
# 1. Clone the repository
git clone <your-repo-url>
cd <your-repo-folder>

# 2. Install dependencies
pip install -r requirements.txt

# 3. Start the server
python app.py
```

On first run, `tasks.db` and the `tasks` table are created automatically, and three example tasks are inserted.

## Example SQL query

```sql
SELECT * FROM tasks WHERE done = 1;
```

This returns every task that has been marked as completed.

## Progress

- [x] Repository set up
- [ ] Database and `tasks` table created automatically
- [ ] Example tasks seeded on first run
- [ ] `GET /tasks` and `GET /tasks/{id}` reading from the database
- [ ] `POST /tasks` inserting into the database
- [ ] `PUT` / `DELETE` updating and removing rows
- [ ] Manual SQL queries explored via a database viewer
- [ ] Screenshot of database viewer added
- [ ] Final documentation pass

## Notes

This project focuses on separating the **API layer** (what the app does) from the **data layer** (where the app stores its data). Once the SQLite version works, swapping in a different database like PostgreSQL later should require minimal changes to the API itself.