# Deep Learning Labs

This repository is your workspace for the semester. Over the labs, you will build **`minitorch`** — a small, PyTorch-style deep learning library — from scratch using mostly NumPy, and use it to train models on datasets like MNIST. By the end of the semester, you should have built a hands-on understanding of how modern deep learning libraries work and be ready to start using pytorch.

**If this is your first time here, follow the setup guide below before doing anything else** — you need it to even open the first lab notebook. Once you're set up, `labs/lab01_onboarding.ipynb` picks up from there.

## Project structure

```
.
├── README.md
├── minitorch/              # the library you are building, week by week
│   ├── __init__.py
│   └── utils.py
├── tests/                  # automated tests for minitorch
│   └── test_utils.py
└── labs/                   # one notebook per week: instructions + exercises
    └── lab01_onboarding.ipynb
```

**`minitorch/` is the library, `labs/` is where you *use* the library.** Code you write in `minitorch/` is meant to be reused across labs and your final project. Each week's notebook in `labs/` imports from `minitorch`, runs experiments, and explains what's happening — the actual implementation lives in the library, not scattered across notebook cells.

## First-time setup

Do this once, before Lab 1. Every step below is a **checkpoint**: if you already have something installed and working, verify it with the given command and skip to the next step.

### 1. Open a terminal

A **terminal** (also called a shell or command line) is a text-based way to interact with your computer: instead of clicking through folders and double-clicking programs, you type commands. Almost all deep learning tooling — installing packages, running training scripts, using version control — is built around the terminal rather than a graphical interface, so getting comfortable with it now pays off all semester.

- **Windows**: open **Windows Terminal** or **PowerShell** (search for either in the Start menu). This course uses PowerShell, not Command Prompt, Git Bash, or WSL — every command below works as written in PowerShell.
- **macOS**: open the `Terminal` app (`Cmd+Space`, then type "Terminal").
- **Linux**: open your distribution's terminal application.

You'll use a handful of commands to navigate folders. These all work in PowerShell and in the default terminal on macOS/Linux:

| Command | What it does | Example |
|---|---|---|
| `pwd` | print current folder | `pwd` |
| `ls` | list files in current folder | `ls` |
| `cd <folder>` | move into a folder | `cd Desktop` |
| `cd ..` | move up one folder | `cd ..` |
| `mkdir <name>` | create a new folder | `mkdir dl-course` |

Try it now: run `pwd`, then navigate to wherever you'd like to keep your coursework (e.g. `cd Desktop`), and create a folder for it: `mkdir dl-course` then `cd dl-course`. You'll clone this repository into that folder in step 3.

### 2. Install git and create a GitHub account

**git** is version control software: it tracks every change you make to your files over time, lets you go back to earlier versions, and — most importantly for this course — lets you submit your work by sending your changes to a server. **GitHub** is that server: a website that hosts git repositories online. You'll use git locally (in your terminal) to record your changes, and GitHub to store and submit them.

**Checkpoint:** run `git --version` — if it prints a version number, skip to creating your GitHub account below.

Install git:
- **Windows**: download and install [Git for Windows](https://git-scm.com/download/win), accepting the default options. This makes `git` available directly from PowerShell.
- **macOS**: usually preinstalled — verify with `git --version`. If missing, run `xcode-select --install`.
- **Linux**: `sudo apt install git` (Debian/Ubuntu) or your distro's equivalent.

**Important:** after installing, close and reopen your terminal, then verify with `git --version`.

Create a GitHub account at [github.com](https://github.com) if you don't already have one — use an email you check regularly, you'll need it all semester.

You'll also need to set up your account in your terminal:
```powershell
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```
(use the same email as your GitHub account)

### 3. Clone the repository

With git installed, you can now download a copy of this repository to your machine — this is called "cloning". From the folder you created in step 1:
```powershell
git clone PSL-DL-Labs
cd PSL-DL-Labs
```
Your repository URL was shared with you separately (e.g. via GitHub Classroom). Running `ls` afterward should show `README.md`, `minitorch/`, `tests/`, and `labs/`.

### 4. Install conda

**conda** manages Python **environments**: isolated installations of Python and a specific set of packages, kept separate from each other and from whatever Python your operating system might already have. This matters for two reasons: it means this course's packages can't clash with anything else on your machine, and it means everyone in the course runs compatible versions of everything, so "it works on my machine" problems disappear. We'll use **Miniconda**, a minimal installer for conda, *not* the full Anaconda Distribution, which bundles hundreds of packages we don't need.

**Checkpoint:** run `conda --version`. If it prints a version number, skip to step 5.

Go to the [official installation guide](https://www.anaconda.com/docs/getting-started/installation), pick your operating system, and follow the steps for **Miniconda** (not Anaconda Distribution, the page covers both, so make sure you're on the Miniconda instructions).

On Windows, during installation it's fine to leave "Add Miniconda to PATH" unchecked. Instead use the "Anaconda Prompt" that gets installed, or run `conda init powershell` from it once so `conda` becomes available directly in PowerShell.

**Important:** after installing, close and reopen your terminal, then verify with `conda --version`.

### 5. Create the environment and launch Jupyter

Now we'll use conda to build the isolated environment described above. You'll create the environment and add packages to it yourself. This is deliberate: environment management (creating environments, installing packages into the right one, knowing what's installed) is a skill you'll keep using all semester, since we'll be installing new packages in most upcoming labs.

```powershell
# create a new environment named "dl-labs" with Python 3.13
conda create --name dl-labs python=3.13

# activate it -- do this every time you start working, in every new terminal window
conda activate dl-labs

# install this week's packages into the active environment
conda install -c conda-forge numpy matplotlib notebook pytest
```

After `conda activate dl-labs`, your terminal prompt should show `(dl-labs)` at the start of the line: that's your confirmation the environment is active. The `-c conda-forge` flag tells conda which package channel to install from; we'll use `conda-forge` consistently all semester.

Then launch Jupyter:
```powershell
jupyter notebook
```
This opens Jupyter in your browser. Navigate to `labs/lab01_onboarding.ipynb` and open it, the notebook picks up from here.

## Weekly workflow

Each week, once you're set up:

1. `git checkout labXX` to switch to the new branch.
2. `git pull` to get the new lab.
3. Open a terminal, `conda activate dl-labs`, then `jupyter notebook`, and open that week's notebook in `labs/`.
4. If the notebook asks you to install a new package, run `conda install -c conda-forge <package-name>` with `dl-labs` activated.
5. Work through the notebook and implement whatever's asked in `minitorch/`.
6. Run the tests: `python -m pytest tests/ -v` (with `dl-labs` still activated).

## Running tests

With the `dl-labs` environment activated:
```powershell
python -m pytest tests/ -v
```

