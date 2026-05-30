# Monday Check-In
## CS411 — Computer Networks — Summer 2026

This document is your reference for every Monday of the course.
It tells you exactly what to install, how to set up your environment,
how to get your project repo, and how to work with Git every day.

**Keep this page open every session.**

---

## Part 1 — Install everything (do this before the first Monday)

You need four tools installed on your machine. Do this at home
before the course starts — do not wait until Monday morning.

---

### 1. Python 3

All projects are written in Python 3. You need version **3.8 or higher**.

**Check if you already have it:**
```bash
python3 --version
# Should print: Python 3.x.x
```

**Install if missing:**

| System | Command |
|--------|---------|
| Ubuntu / Debian | `sudo apt update && sudo apt install python3 python3-pip` |
| macOS (with Homebrew) | `brew install python3` |
| Windows | Download from [python.org/downloads](https://python.org/downloads) — check **"Add to PATH"** during install |

**Verify:**
```bash
python3 --version
python3 -c "import socket; print('socket OK')"
```

---

### 2. Git

Git is the version control tool you will use to submit your work
and collaborate with your teammate.

**Check if you already have it:**
```bash
git --version
# Should print: git version 2.x.x
```

**Install if missing:**

| System | Command |
|--------|---------|
| Ubuntu / Debian | `sudo apt install git` |
| macOS | `brew install git` — or run `git` in terminal and macOS will prompt you |
| Windows | Download from [git-scm.com](https://git-scm.com) — use all default options during install |

**Configure Git with your identity (do this once):**
```bash
git config --global user.name "Firstname Lastname"
git config --global user.email "your.email@example.com"

# Verify:
git config --list
```

> Use the same email address as your GitHub account.

---

### 3. Wireshark

Wireshark is a network packet analyser. You will use it every week
to verify that your code is doing what you think it is doing.
**It is required for every demo.**

**Install:**

| System | Instructions |
|--------|-------------|
| Ubuntu / Debian | `sudo apt install wireshark` — when asked, select **Yes** to allow non-root users |
| macOS | Download from [wireshark.org/download](https://wireshark.org/download) |
| Windows | Download from [wireshark.org/download](https://wireshark.org/download) — install with all default options |

**After installing on Linux — add yourself to the wireshark group:**
```bash
sudo usermod -aG wireshark $USER
# Log out and log back in for this to take effect
```

**Verify:**
```bash
# Launch Wireshark — it should open without errors
wireshark
```

> If Wireshark asks for a password every time on Linux, the group
> change above did not take effect yet. Log out and back in.

---

### 4. A code editor

You need a text editor that understands Python. We recommend VS Code.

**Install VS Code:**
- Download from [code.visualstudio.com](https://code.visualstudio.com)
- After installing, open VS Code and install the **Python extension**:
  - Press `Ctrl+Shift+X` → search "Python" → Install

**Useful VS Code shortcuts:**
| Shortcut | What it does |
|----------|-------------|
| `` Ctrl+` `` | Open integrated terminal |
| `Ctrl+S` | Save file |
| `Ctrl+Shift+P` | Command palette |

> VS Code has a built-in terminal. You can run `python3 server.py`
> and have your code open side by side. Use this.

---

### 5. Create a GitHub account

You need a GitHub account to receive and submit your project.

1. Go to [github.com](https://github.com) → **Sign up**
2. Choose a username that is recognisable — ideally `firstname-lastname`
   or your institution username
3. **Send your GitHub username to your instructor before the first session**

---

## Part 2 — Monday morning workflow (repeat every week)

Every Monday at the start of the session, you do these steps in order.
They take about 10 minutes. Do not skip them.

---

### Step 1 — Accept your GitHub invitation

Your instructor creates a private repository for your team before class.
GitHub sends an invitation to your email.

1. Check your email for a message from GitHub:
   *"[instructor] invited you to collaborate on cs411-summer-2026/project1-..."*
2. Click **"View invitation"** → **"Accept invitation"**
3. You now have access to your team's repo

> If you did not receive an email, check your GitHub notifications:
> click the bell icon at the top of github.com

---

### Step 2 — Clone your repo

Open a terminal and run:

```bash
# Replace lastname1-lastname2 with your actual team names
git clone https://github.com/cs411-summer-2026/project1-lastname1-lastname2.git

# Enter the folder
cd project1-lastname1-lastname2

# List the files — you should see:
# README.md   server.py   test_server.py   www/
ls
```

> **Clone only once per project.** After this, you just `git pull`
> at the start of each session to get your teammate's latest changes.

---

### Step 3 — Open in your editor

```bash
code .       # opens VS Code in the current folder
```

Or open VS Code manually and use **File → Open Folder**.

---

### Step 4 — Read the README

Every project repo has a `README.md` file with:
- The full project brief
- Concepts you need to understand
- A step-by-step build guide
- The demo checklist

**Read it completely before writing a single line of code.**
It renders nicely on GitHub — open
`github.com/cs411-summer-2026/project1-lastname1-lastname2`
in your browser to read it with formatting.

---

### Step 5 — Make your first commit before leaving Monday

At the end of every Monday session, commit whatever you have —
even if it is just the echo server running:

```bash
git add server.py
git commit -m "step 1: echo server running, browser GET visible in terminal"
git push
```

Your instructor checks that every team has at least one commit
from Monday. This is your proof that you started.

---

## Part 3 — Daily Git workflow (Tuesday, Wednesday, Thursday)

Use these commands every session. Both teammates should pull at the
start and push at the end.

---

### Start of every session — pull your teammate's changes

```bash
cd project1-lastname1-lastname2   # make sure you are in the right folder
git pull
```

> Always pull before you start writing. If you and your teammate
> both edit the same file without pulling, you will get merge conflicts.

---

### During the session — commit after every working step

Do not wait until the end. Commit each time something new works.

```bash
# See what files you changed
git status

# Stage the files you want to commit
git add server.py

# Commit with a clear message
git commit -m "step 3: files served from www/ with correct Content-Type"

# Push so your instructor and teammate can see it
git push
```

---

### End of every session — push everything

```bash
git add .                          # stage all changed files
git commit -m "end of tuesday: 404 and 405 working"
git push
```

---

### Good commit messages

Your commit history is visible to your instructor.
It shows when you worked and what you built.

| Good ✅ | Bad ❌ |
|---------|--------|
| `step 1: echo server running` | `fix` |
| `step 3: files served with correct MIME type` | `wip` |
| `step 4: 404 and 405 responses implemented` | `aaaaaa` |
| `step 5: threading added, 2 concurrent clients work` | `final` |
| `final: all tests pass, optional feature done` | `final2` |

> A single commit on Thursday morning tells your instructor
> you built nothing during the week.
> **5+ commits spread across the week is what is expected.**

---

## Part 4 — Testing your code

Every project includes a `test_server.py` file.
Run it before your demo to catch problems early.

```bash
# Terminal 1 — start your server
python3 server.py

# Terminal 2 — run the tests
python3 test_server.py
```

You should see output like:
```
Running tests against http://localhost:8080

1. GET / → 200 OK
  PASS  Status code is 200
  PASS  Content-Type is text/html
  PASS  Body is not empty
  PASS  Content-Length header is present
  PASS  Content-Length matches body length
...
Results: 8/8 passed  ✓ All tests pass
```

**All tests must pass before you stand up to demo on Thursday.**
If a test fails, read the error message — it tells you exactly what is wrong.

---

## Part 5 — Wireshark quick-start

You will use Wireshark every week. Here is the minimum you need to know.

### Capture your own traffic

1. Open Wireshark
2. Select the **Loopback** interface
   - Linux / macOS: called `lo`
   - Windows: called `Loopback`
   - *(not Wi-Fi, not Ethernet — your browser and server are on the same machine)*
3. Click the blue shark fin to **start capture**
4. Make a request in your browser or with curl
5. Click the red square to **stop capture**

### Filter to see only your traffic

In the filter bar at the top, type:
```
tcp.port == 8080
```
Press Enter. You now see only packets going to/from your server.

### Read a full HTTP exchange

Right-click any packet → **Follow** → **TCP Stream**

This shows the full request and response as readable text.
You will use this in every demo.

### Essential filters

| Filter | What it shows |
|--------|--------------|
| `tcp.port == 8080` | All traffic on port 8080 |
| `http` | HTTP packets only |
| `tcp.flags.syn == 1` | TCP handshake SYN packets |
| `ip.addr == 127.0.0.1` | Loopback traffic only |

---

## Part 6 — Useful terminal commands

### Python

```bash
python3 --version                  # check version
python3 server.py                  # run your server
python3 test_server.py             # run the tests
Ctrl + C                           # stop a running program
```

### curl — test your server from the terminal

```bash
curl -v http://localhost:8080/              # GET / with verbose output
curl -v http://localhost:8080/index.html   # request a specific file
curl -v http://localhost:8080/missing      # test your 404 response
curl -v -X POST http://localhost:8080/     # test your 405 response
```

`-v` means verbose — it shows the full request and response headers,
which is exactly what you need to verify your HTTP implementation.

### Port troubleshooting

```bash
# See what is listening on port 8080
ss -tlnp | grep 8080        # Linux
lsof -i :8080               # macOS / Linux

# Kill whatever is holding port 8080
kill -9 <PID>               # replace <PID> with the number you found above
```

If you get `Address already in use` when starting your server,
it means a previous run is still alive. Use the commands above to kill it.

### Git

```bash
git status                  # see what changed
git add <filename>          # stage a file
git add .                   # stage all changed files
git commit -m "message"     # commit with a message
git push                    # push to GitHub
git pull                    # pull your teammate's changes
git log --oneline           # see your commit history
```

---

## Part 7 — Getting help

### Before asking the instructor

1. Read the error message carefully — Python errors tell you the file
   and line number
2. Re-read the relevant section of `README.md`
3. Run the tests: `python3 test_server.py` — the output says what is failing
4. Check Wireshark — is your server sending what you think it is?

### GitHub Issues

Each project repo has an **Issues** tab. If you have a question
that is not urgent, open an issue — your instructor will respond there.
This is better than a message that gets lost.

1. Go to your team repo on GitHub
2. Click **Issues** → **New issue**
3. Describe the problem: what you tried, what you expected, what happened
4. Include the error message or a Wireshark screenshot

### During class

Raise your hand. The instructor will come to you.
Show your terminal output and your Wireshark capture —
do not just say "it does not work."

---

## Summary — what to do every single day

| When | What |
|------|------|
| Before Monday | Install Python, Git, Wireshark, VS Code. Create GitHub account. Send username to instructor. |
| Monday morning | Accept GitHub invitation. Clone repo. Read README. Build step 1. Commit before leaving. |
| Tuesday start | `git pull`. Build steps 2–4. Commit after each working step. Push at the end. |
| Wednesday start | `git pull`. Finish implementation. Run tests. Prepare demo. Commit and push. |
| Thursday morning | `git push` your final state. Run tests one last time. Demo is 8 minutes. |

---

*CS411 — Computer Networks — Summer 2026*
*Questions? Open an issue in your team repo.*
