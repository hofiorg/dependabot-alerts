# dependabot-alerts

Script to fetch dependabot alerts for all repositories.

## Usage

### GitHub Token erstellen
  
Erstelle unter 👉 <https://github.com/settings/tokens> einen fine-grained oder classic token mit diesen Rechten:

- repo (für private Repos, falls vorhanden)
- security_events (für Dependabot Alerts)

### Token in Umgebungsvariable setzen

```sh
export GH_TOKEN=your_github_token_here
```

### Script ausführen

```sh
./dependabot-alerts your_github_username
```

#### Beispiel

```sh
./dependabot-alerts hofiorg
```
