# Threat model

## What this project does and where untrusted input enters
A web administration tool for PostgreSQL (Python/Flask). Untrusted input: the web API (SQL
execution, server/connection management, user auth), uploaded files, and connection strings.
SQL handling and the auth/session layer are the main surfaces.

## Components that matter most / least
- most: the auth/session logic, the SQL-execution and connection handling, and file upload.
- less: the frontend, docs.

## How to exercise it
Exercise the web API with crafted SQL and connection parameters; test auth boundaries; upload
crafted files.

## How you rate severity
- Auth bypass or RCE (e.g., via SQL or file handling): critical.
- Authorization bugs (accessing another server/role): high. XSS: medium.

## Anything to leave alone
- Do not report the frontend assets; focus on the Python backend.
