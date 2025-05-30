# Snippet Lab

A living, copy‑paste‑ready encyclopaedia of everyday commands, one‑liners and boiler‑plate that DevOps engineers, SREs and developers reach for daily.

---

## 0  Prerequisites

| Tool               | Why you need it               | macOS (Homebrew)                                       | Ubuntu/Debian                         | Fedora/RHEL            | Arch                 | Windows (Chocolatey)                       |
| ------------------ | ----------------------------- | ------------------------------------------------------ | ------------------------------------- | ---------------------- | -------------------- | ------------------------------------------ |
| **git**            | clone & update the lab        | *built‑in* / `brew install git`                        | `sudo apt install git`                | `sudo dnf install git` | `sudo pacman -S git` | `choco install git`                        |
| **less**           | quick paging through snippets | *built‑in*                                             | *built‑in*                            | *built‑in*             | *built‑in*           | `choco install less`                       |
| **fzf**            | fuzzy search across files     | `brew install fzf && $(brew --prefix)/opt/fzf/install` | `sudo apt install fzf`                | `sudo dnf install fzf` | `sudo pacman -S fzf` | `choco install fzf` or `scoop install fzf` |
| **bat** (optional) | colourful preview inside fzf  | `brew install bat`                                     | `sudo apt install bat` (aka `batcat`) | `sudo dnf install bat` | `sudo pacman -S bat` | `choco install bat`                        |

> **Tip** Run the bundled `fzf/install` script after installing to enable shell key‑bindings (`Ctrl‑R` history search, `Ctrl‑T` file search, etc.).

If you can’t add extra tools right now, skip `fzf` + `bat` and use plain `grep` / your editor.

---

## 1  Project Layout

```
/
├── README.md                      – project overview (this file)
├── languages/                     – top‑level directory for every tech/tool
│   ├── kubectl/                   – Kubernetes CLI cheats
│   │   ├── 01_basics.md
│   │   ├── 02_deployments.md
│   │   └── 99_troubleshooting.md
│   └── terraform/                 – Terraform CLI & HCL patterns
│       ├── 01_init_and_workspace.md
│       ├── 02_plan_apply.md
│       └── 03_state.md
└── CONTRIBUTING.md                – style guide & PR checklist
```

### Naming convention

* Prefix files with a **two‑digit ordinal** (`01_`, `02_`, …) so GitHub renders them logically.
* Snake‑case filenames and keep them self‑descriptive.

---

## 2  Philosophy

* **Single purpose per file** – one theme per snippet file.
* **≤ 20 lines per snippet** – trim boiler‑plate; link out for context.
* **Production‑safe defaults** – no `--force`, `-y`, or `--disable-validation` unless absolutely required *and* documented.
* **Copy‑pastable** – everything should run as‑is or explain prerequisites inline.

---

## 3  Installation & Getting Started

```bash
# 1. Clone the repo
$ git clone https://github.com/<org>/snippet‑lab.git && cd snippet‑lab

# 2. Open a cheatsheet quickly
$ less languages/kubectl/01_basics.md  # uses built‑in pager

# 3. Fuzzy‑search across all snippets (requires fzf + bat)
$ fzf --preview 'bat --style=plain --color=always {}' \
      --bind "change:reload:grep -R --line-number --color=always {q} languages" \
      <<<""

# 4. No fzf? Fall back on grep
$ grep -R --line-number "rollout" languages/
```

---

## 4  Contributing at a Glance

1. **Fork → branch → commit**.
2. Place new snippets under `languages/<tool>/` using the naming convention.
3. Follow the Markdown template:

   ````md
   ## Short Title (≤ 50 chars)
   > One‑sentence *what/why* description.
   ```bash
   # command goes here
   ````

   *Optional contextual tips.*

   ```
   ```
4. Run `./scripts/lint.sh` (Markdown‑lint + terraform‑fmt).
5. Open a **PR** and tag a maintainer.

---

## 5  Roadmap

* [ ] Migrate existing `kubectl` & `terraform` examples from the initial README into their new files.
* [ ] Add directories for **docker**, **git**, **helm**, **aws‑cli**, **az‑cli**, **ansible**, **bash**, **powershell**.
* [ ] Provide a small shell wrapper `snip <keyword>` powered by `ripgrep` & `fzf`.
* [ ] Publish a searchable GitHub Pages site.

Happy hacking! 🔧✨
