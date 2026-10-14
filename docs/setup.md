# Setup and repository access

Do this before the practical: allow about 10–15 minutes if the tools are already
installed. You need Git, Python 3.12, an editor/terminal and access to the teaching
repository. Package installation needs internet access or a tutor-supplied cache.

## Get your own working copy

Use the personal repository supplied by your lecturer or created through their
GitHub Classroom link. If the lecturer gives you a template repository, select
**Use this template → Create a new repository**, then create your own copy.
Use only the default starter branch. If neither route is available, ask the
lecturer for the correct starter copy. Do not edit the shared class template.

On **your** repository, open **Code** and copy its HTTPS clone URL. Replace the
example below with that real URL; do not type the angle brackets.

```bash
git clone <your-repository-HTTPS-URL>
```

Open the resulting clone in your editor. If the lecturer imported the exercise
into a subdirectory, open that subdirectory as the Python working folder.
All Python commands below run from the folder containing `requirements.txt`
and `app/`; Git uses the enclosing repository's existing history.

If you already have a clone, use it. Check `git status` and follow the lecturer's
instructions to obtain the starter update without overwriting your work.
Do not run `git init` in an existing clone or create a nested repository.

Create a working branch:

```bash
git switch -c week05-fastapi
```

If that branch already exists in your clone, switch to it instead:

```bash
git switch week05-fastapi
```

## Create and select the environment

Check that `python --version` selects Python 3.12, then run:

```bash
python -m venv .venv
```

Windows users can use `py -3.12 -m venv .venv`; macOS/Linux users can use
`python3.12 -m venv .venv` if needed. Activate using your terminal's command:

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

Select `.venv` as the interpreter in your editor. If you do not activate the
environment, use its Python executable in place of `python` in the commands
below: `.\.venv\Scripts\python.exe` in PowerShell,
`.venv\Scripts\python.exe` in Command Prompt, or `.venv/bin/python` on macOS/Linux.
For example, run
`.\.venv\Scripts\python.exe -m pip install -r requirements.txt` in PowerShell.
If PowerShell blocks activation, use this direct-Python option; no machine-wide
execution-policy change is needed.

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
