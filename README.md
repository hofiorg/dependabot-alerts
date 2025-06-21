# dependabot-alerts

Script to fetch [Dependabot](https://github.com/dependabot) alerts for all repositories.

## Usage

### Create a GitHub Token
  
Create a fine-grained or classic token at 👉 <https://github.com/settings/tokens> with the following permissions:

- repo (for private repositories, if applicable)
- security_events (for Dependabot alerts)

### Set Token as Environment Variable

```sh
export GH_TOKEN=your_github_token_here
```

### Run the Script

```sh
./dependabot-alerts your_github_username
```

#### Example

```sh
./dependabot-alerts hofiorg
```
