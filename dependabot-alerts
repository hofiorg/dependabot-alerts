#!/bin/bash 

USERNAME="${1:-hofiorg}"
GH_TOKEN="${GH_TOKEN:?Bitte GH_TOKEN Umgebungsvariable setzen}"

echo "📦 Lade Repository-Liste für Benutzer '$USERNAME'..."
repos=$(curl -s -H "Authorization: Bearer $GH_TOKEN" \
  "https://api.github.com/users/$USERNAME/repos?per_page=100" | jq -r '.[].name')

# Tabellenüberschrift
printf "%-30s %s\n" "Repository" "Status"
printf "%-30s %s\n" "------------------------------" "------"

for repo in $repos; do
  response=$(curl -s -H "Authorization: Bearer $GH_TOKEN" \
    -H "Accept: application/vnd.github+json" \
    "https://api.github.com/repos/$USERNAME/$repo/dependabot/alerts")

  is_array=$(echo "$response" | jq 'if type == "array" then true else false end' 2>/dev/null)

  if [ "$is_array" != "true" ]; then
    printf "%-30s %s\n" "$repo" "-"
    continue
  fi

  alert_count=$(echo "$response" | jq '[.[] | select(.state == "open" and .dismissed == false)] | length')

  if [ "$alert_count" -eq 0 ]; then
    status="✅"
  else
    status="❌ $alert_count"
  fi

  printf "%-30s %s\n" "$repo" "$status"
done
