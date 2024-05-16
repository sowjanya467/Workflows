import requests
import json
 
token = os.getenv("TOKEN")
 
headers = {
    'Authorization': f'token {token}',
    'Accept': 'application/vnd.github.v3+json'
}
 
repos_url = 'https://api.github.com/sowjanya467/repos'
response = requests.get(repos_url, headers=headers)
repos = response.json()
 
alerts = []
for repo in repos:
    # Fetch code scanning alerts for each repository
    alerts_url = f"https://api.github.com/repos/{repo}/code-scanning/alerts"
    response = requests.get(alerts_url, headers=headers)
    repo_alerts = response.json()
    
    alerts.extend(repo_alerts)
 

with open('scanning_alerts.json', 'w') as file:
    json.dump(alerts, file)
 
print("Code scanning alerts saved to code_scanning_alerts.json")
