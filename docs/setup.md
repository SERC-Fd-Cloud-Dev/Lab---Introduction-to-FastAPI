# Setup and repository access

Do this before the practical: allow about 10–15 minutes if the tools are already
available. Choose either GitHub Codespaces or a local clone. Package installation
needs internet access or a tutor-supplied cache.

## Get your own repository

Use the personal repository supplied by your lecturer or created through their
GitHub Classroom link. If the lecturer gives you a template repository, select
**Use this template → Create a new repository**, then create your own copy.
Use only the default starter branch. If neither route is available, ask the
lecturer for the correct starter copy. Do not edit the shared class template.

## Option A: GitHub Codespaces

1. Open **your** repository on GitHub and select **Code → Codespaces**.
2. Select **Create codespace on [the default branch]**. Wait for the editor to
   open in your browser.
3. Open the integrated terminal. Your repository is already checked out in the
   Codespace; do not run `git clone` again.

## Option B: Local setup (clone)

You need Git, Python 3.14, an editor and a terminal installed on your computer.
On **your** repository, open **Code** and copy its HTTPS clone URL. Replace the
example below with that real URL; do not type the angle brackets.

```bash
git clone <your-repository-HTTPS-URL>
```

Open the resulting clone in your editor. If the lecturer imported the exercise
into a subdirectory, use that subdirectory as the Python working folder; Git uses
the enclosing repository's existing history.

If you already have a clone, use it. Check `git status` and follow the lecturer's
instructions to obtain the starter update without overwriting your work.
Do not run `git init` in an existing clone or create a nested repository.

## Continue in either environment

Run Python and Git commands from the folder containing `requirements.txt` and
`app/`. In the Codespace, use its integrated terminal; locally, use your editor's
terminal.

Create a working branch:

```bash
git switch -c week05-fastapi
```

If that branch already exists, switch to it with `git switch week05-fastapi`.

## Create and select the environment

In the terminal, check that `python --version` selects Python 3.14, then create
the environment:

```bash
python -m venv .venv
```

Windows users can use `py -3.14 -m venv .venv`; macOS/Linux users can use
`python3.14 -m venv .venv` if needed. Activate using your terminal's command:

| Terminal | Activation command |
|---|---|
| Windows PowerShell | `.\.venv\Scripts\Activate.ps1` |
| Windows Command Prompt | `.venv\Scripts\activate.bat` |
| macOS/Linux bash or zsh | `source .venv/bin/activate` |

```bash
python --version
python -m pip install -r requirements.txt
python -m pip check
```

Select `.venv` as the interpreter in your editor. If PowerShell blocks activation,
use Command Prompt or the environment's Python directly, for example
`.\.venv\Scripts\python.exe -m pip install -r requirements.txt`.
No machine-wide execution-policy change is needed.

## Check the starter

Start from the Python working folder:

```bash
python -m uvicorn app.main:app --reload
```

Open `http://127.0.0.1:8000/docs` and `http://127.0.0.1:8000/openapi.json`.
The application initially has no student-defined operations. A 404 from
`/health` is expected until Exercise 01; it is not a failed installation.
If Swagger UI assets are blocked by your network, use `/openapi.json` and
Postman/direct requests instead. Stop the server with Ctrl+C.

## Save and share increments

At each checkpoint, inspect `git status`, stage the named files and commit a
short message describing the working change. Also stage the corresponding
learning-log update. Avoid staging `.venv` or cache files.

```bash
git add app evidence/learning-log.md
git commit -m "Add initial health and equipment routes"
git push -u origin week05-fastapi
```

The first push connects your branch to your own repository. Later use `git push`.
Commit examples assume you are in the exercise folder; Git finds the enclosing
repository when the exercise lives in a subdirectory. Use `git add tests ...`
for test increments. Share your repository/branch link for formative review
using the lecturer's normal course route. No pull request or deployment is required.
