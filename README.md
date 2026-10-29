<!--
  Name     : README.md
  Purpose  : Overview of SQL Studio (GitHub repository)
  Author   : Eric PERRET
  Date     : 2026-10-27
  Version  : 2.3
-->

# SQL Studio

🇫🇷 [Version française : LISEZMOI.md](LISEZMOI.md)

▶️ **[Launch SQL Studio](https://ericperret.github.io/sql_studio/sql_studio.html)** — ready to use, demo database included.

**A complete SQL interpreter running in your browser — no server, no dependency, one single HTML file.**

![SQL Studio v2.3: Training mode, level 5 INNER JOIN, query accepted](screenshot.png)

User interface in French. Detailed documentation (French): [sql_studio_doc.odt](sql_studio_doc.odt) (LibreOffice Writer).

---

## Origin

The embedded database is a small teaching database freely copied from the picture of a DGSE (French intelligence service) quiz. Three tables, natural joins, deliberate NULLs — everything needed to learn SQL without friction.

---

## What it is

A teaching tool to learn and practise SQL, fully standalone. No Node.js. No Python. No CDN. No framework. Open the file in Firefox or Chrome — it is ready.

---

## Features

| Feature | Description |
|---|---|
| SQL engine | SQL interpreter in plain JavaScript, in-memory data |
| Table explorer | Columns, types and data preview; SELECT * and DROP buttons per table |
| Keyword palette | One-click insertion of keywords and functions, grouped by family |
| Editor | Run with the button or Ctrl+Enter |
| Training mode | 15 exercises over 10 levels, progressive hints and solutions, a lesson per level |
| Import / export | Import a CSV as a table, export the last result as CSV |
| Persistence | Database and progress kept in the browser's `localStorage` |

---

## The SQL engine

This is the centrepiece. A SQL interpreter written in plain JavaScript that runs real queries on real in-memory data.

**Supported queries:**

- `SELECT` with named columns, `AS` aliases, `*`
- `SELECT DISTINCT`
- `FROM` with table aliases
- `INNER JOIN` and `LEFT JOIN` (with `ON` and NULL handling)
- Multiple joins (3 tables or more)
- `WHERE` with `AND`, `OR`, `NOT`, `IN`, `NOT IN`, `BETWEEN`, `IS NULL`, `IS NOT NULL`, operators `=` `!=` `>` `<` `>=` `<=`
- `CASE WHEN ... THEN ... ELSE ... END` with arithmetic (`+`)
- Multi-column `ORDER BY` `ASC` / `DESC`
- `LIMIT`

**Functions:**

- `COALESCE`, `CONCAT`
- `DATE`, `STRFTIME`
- Spatial: `ST_MakePoint(lon, lat)`, `ST_X`, `ST_Y`, `ST_SRID`, `ST_GeometryType`, `ST_IsEmpty`

**Supported DDL/DML:**

- `CREATE TABLE`
- `DROP TABLE`
- `INSERT INTO ... VALUES`
- `UPDATE ... SET ... WHERE`
- `DELETE FROM ... WHERE`

**What the engine does well:**

NULLs are handled correctly. A `LEFT JOIN` on a NULL foreign key keeps the row with the right-hand columns set to NULL — exactly like a real DBMS. `CASE WHEN` scoring adds several expressions cleanly. Table aliases are resolved in `ON` and `WHERE` conditions without ambiguity.

---

## Training mode

15 progressive exercises over 10 levels:

| Level | Topic | Questions |
|-------|-------|-----------|
| 1 | SELECT | 1 |
| 2 | WHERE | 1 |
| 3 | AND / OR / IS NULL | 1 |
| 4 | DISTINCT · ORDER BY | 2 |
| 5 | INNER JOIN | 2 |
| 6 | LEFT JOIN | 2 |
| 7 | 3 tables | 2 |
| 8 | CASE WHEN | 2 |
| 9 | INSERT | 1 |
| 10 | CREATE TABLE | 1 |

**Checking is done on the result, not on the syntax.** Two different queries giving the same output are both accepted.

Levels 4 to 8: after 5 errors → hint. After 10 errors → solution + the question rephrased differently.

Progress is saved in `localStorage` — it survives a reload.

Each level has a lesson bubble (💡 button) with examples.

---

## Import / Export

- **⬇ démo**: loads the DGSE database (3 tables)
- **↑ CSV**: imports any `.csv` file as a new table, types detected automatically
- **↓ CSV**: exports the result of the last SELECT query
- **✕ reset**: clears everything

---

## Usage

Open the link above, or download `sql_studio.html` and open it in a browser.

No installation. No server. Works offline.

---

## History

| Version | Change |
|---|---|
| 2.1 | Published version: SQL engine, Training mode, CSV import / export |
| 2.2 | Old copy pasted at the end of the file removed (duplicated interface and script) |
| 2.3 | AZS visual identity (slate / amber / cyan palette, AZS mark linking back to www.azs.fr, system fonts); stacked layout on small screens |

---

## License

**Free for non-commercial use** — [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/), with mandatory credit of the source and the author:

> sql_studio — Eric PERRET — https://github.com/ericperret/sql_studio

Any commercial use is forbidden without the author's written permission, requested by e-mail: **eperret@azs.fr**.
Full terms (French / English): [LICENSE](LICENSE).
