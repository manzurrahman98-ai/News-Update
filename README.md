# News-Update
News update created with API
import requests

# Your API key from newsapi.org
api_key = "05f0d89d293242a6ae1bb0fd01f6edd9"

# Define endpoint and parameters
url = "https://newsapi.org/v2/top-headlines"
params = {
    "country": "us",      # you can change to "gb", "in", "bd", etc.
    "category": "technology",  # or "business", "sports", etc.
    "apiKey": api_key
}

# Make the GET request
response = requests.get(url, params=params)

# Parse JSON response
data = response.json()

# Print articles
if data["status"] == "ok":
    for i, article in enumerate(data["articles"], start=1):
        print(f"{i}. {article['title']}")
        print(f"   {article['url']}\n")
else:
    print("Error:", data.get("message"))
