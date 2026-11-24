# ⚡ PowerShell Pro

[![PowerShell 7.4+](https://img.shields.io/badge/PowerShell-7.4%2B-5391FE?style=flat-square&logo=powershell&logoColor=white)](https://github.com/PowerShell/PowerShell)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
[![Release](https://img.shields.io/badge/release-v2.4.0-blueviolet?style=flat-square)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)]()

**Supercharge your terminal workflow.** PowerShell Pro is a modular productivity framework, profile manager, and curated toolkit of high-utility cmdlets designed for developers, DevOps engineers, and sysadmins who live in the CLI.

---

## ✨ Key Features

* **🚀 Sub-150ms Startup:** Built-in asynchronous lazy-loading ensures heavy modules (Azure, AWS, Docker) only load when you actually call them.
* **🧠 Predictive IntelliSense & Fuzzy Search:** Pre-configured `PSReadLine` bindings paired with `fzf` integration for instant command history, file jumping, and process killing.
* **🛠️ 50+ Production-Ready Cmdlets:** Intuitive wrappers and Unix-inspired aliases for networking, Git workflows, JSON/YAML parsing, and system diagnostics.
* **🎨 Context-Aware Prompt:** Clean, zero-lag prompt telemetry displaying active Git branch, Kubernetes context, Python venv, and last command execution time.
* **📦 Declarative Config:** Manage plugins, aliases, and themes from a single `~/.pspro.json` file—easy to version-control in your dotfiles.

---

## 📋 Prerequisites

* [PowerShell 7.4+](https://github.com/PowerShell/PowerShell/releases) (Cross-platform: Windows, macOS, Linux)
* A [Nerd Font](https://www.nerdfonts.com/) installed and enabled in your terminal (e.g., *JetBrainsMono Nerd Font* or *CaskaydiaCove*)
* Optional: [`fzf`](https://github.com/junegunn/fzf) and [`ripgrep`](https://github.com/BurntSushi/ripgrep) for enhanced search cmdlets

---

## 📦 Installation

### Option 1: Quick Bootstrap (Recommended)
Run the following command in your PowerShell terminal:

```powershell
irm https://get.pspro.dev/install.ps1 | iex
```

### Option 2: PowerShell Gallery
```powershell
Install-Module -Name PowerShellPro -Scope CurrentUser -Force
Initialize-PSProProfile
```

Restart your terminal, and you're good to go!

---

## 🚀 Quick Start & Examples

PowerShell Pro ships with dozens of ergonomics-first commands right out of the box:

```powershell
# Find what's occupying a port and optionally kill it
Get-PortUsage -Port 8080 -Kill

# Fuzzy-find and checkout a local or remote Git branch
git-switch

# Clean up all merged local branches safely
Clear-GitBranches -DryRun

# Quick JSON/REST inspection with syntax-highlighted output
Invoke-ProRest https://api.github.com/users/octocat | Select-Json "name, public_repos"

# Live-watch any command (like Linux `watch`)
Watch-Command -Seconds 2 { kubectl get pods }

# Switch between cloud & environment profiles seamlessly
Use-ProContext -Env "staging-eu"
```

### Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + R` | Interactive fuzzy history search |
| `Ctrl + T` | Fuzzy-find files and insert path at cursor |
| `Alt + C` | Fuzzy-cd into any subdirectory |
| `Ctrl + Space` | Open interactive parameter/menu completion |

---

## ⚙️ Configuration

Customize your setup without touching your `$PROFILE` script. Edit `~/.pspro.json`:

```json
{
  "theme": "tokyo-night",
  "telemetry": {
    "showGitStatus": true,
    "showKubeContext": true,
    "execTimeThresholdMs": 500
  },
  "lazyLoadModules": [
    "Az.Accounts",
    "DockerCompletion",
    "posh-git"
  ],
  "aliases": {
    "ll": "Get-ChildItemPro",
    "k": "kubectl"
  }
}
```

Run `Update-PSPro` anytime to pull the latest modules and community cmdlets.

---

## 🤝 Contributing

Contributions are what make the open-source community thrive. Got a killer script or productivity alias?

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/amazing-cmdlet`)
3. Run Pester tests (`Invoke-Pester ./tests`)
4. Commit your changes (`git commit -m 'feat: add amazing cmdlet'`)
5. Push to the branch and open a Pull Request

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.

---

<p align="center">
  Built with 💙 by terminal enthusiasts. If PowerShell Pro saves you time, give it a ⭐!
</p>
