# dependabot-alerts

[![Shell Script](https://img.shields.io/badge/Bash-Script-blue?logo=gnubash)](https://github.com/hofiorg/dependabot-alerts/blob/main/dependabot-alerts)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/hofiorg/dependabot-alerts/blob/main/LICENSE)
[![ShellCheck](https://github.com/hofiorg/dependabot-alerts/actions/workflows/lint-bash.yml/badge.svg)](https://github.com/hofiorg/dependabot-alerts/actions/workflows/lint-bash.yml)

A script to fetch [Dependabot](https://github.com/dependabot) alerts for all repositories of a GitHub user.

## 🛠️ Prerequisites

This script requires the following tools to be installed on your system:

- [`curl`](https://curl.se/) — for making HTTP requests to the GitHub API  
- [`jq`](https://stedolan.github.io/jq/) — for parsing JSON responses in Bash

### ☑️ Check if they are installed

Run the following commands to verify:

```sh
which curl
which jq
```

If either command returns no path, you need to install the missing tools.

## 📥 Installation

### On Ubuntu (including WSL)

```sh
sudo apt update
sudo apt install -y curl jq
```

### 🔐 Set up the GitHub Personal Access Token
  
Create a fine-grained or classic token at 👉 <https://github.com/settings/tokens> with the following permissions:

- `repo` (for private repositories, if applicable)
- `security_events` (for Dependabot alerts)

### 🌍 Set the token as Environment Variable

```sh
export GH_TOKEN=your_github_token_here
```

To make this persistent, add the above line to your `~/.bashrc` or `~/.zshrc`.

### 🚀 Usage

Run the script as follows:

```sh
./dependabot-alerts [github_username]
```

If no username is provided, it defaults to `hofiorg`.

#### 🧪 Examples

```sh
./dependabot-alerts
./dependabot-alerts octocat
```

#### 📊 Output Example

When you run the script, you'll see a table like this:

```txt
📦 Fetching repository list for user 'hofiorg'...
Repository                     Status
------------------------------ ------
angular-boilerplate            ✅
graphql_react_example          ❌ 2
java_websockets                ✅
react-input-calendar           -
utils                          ✅
```

**Legend:**

- ✅ – No open Dependabot alerts  
- ❌ *n* – *n* open, undismissed alerts found  
- `-` – Alerts not accessible (e.g., archived or insufficient permissions)
