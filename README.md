# DataScience
IMPORTENT POINT FOR DATA ANALYSIS
# Q AND A
asking importent question.
1. How big is the data
    df.shape
2. How does the data look like.
    df.sample(),df.head(),df.tail()
3. What is the data type of cols.
    df.info()
4. Are there any missing values.
     df.isnull().sum()
5. How does the data look mathemamatically
   df.describe()
6. Are there duplicate values.
   df.duplicated().sum()
7. How is the correlation between cols
   df.corr()

# PANDAS FOR WEB CSV
url="https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"
response = requests.get(url)

# Check if the request was successful (status code 200)
if response.status_code == 200:
    # Save the content of the response to a local CSV file
    with open("downloaded_data.csv", "wb") as f:
        f.write(response.content)
    print("CSV file downloaded successfully")
else:
    print("Failed to download CSV file. Status code:", response.status_code)

# Read the CSV file into a Pandas DataFrame
df = pd.read_csv("downloaded_data.csv")

# JSON TO CSV OR DATAFRAME
import requests
import pandas as pd

url = "https://api.themoviedb.org/3/person/popular?language=en-US"

headers = {
    "accept": "application/json",
    "Authorization": "Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI5ZDVmYTExYWMzNWFkOTY1ODcwZGE5ODU5NjMwNDZjOCIsInN1YiI6IjY1YWY2MGRmM2UyZWM4MDBlYmYwNzY1NCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.zUz-NA2S3IfGudnnF16nrmiPDmtzxAm5O8VmJ7qlrAA"
}

response = requests.get(url, headers=headers)
data = response.json()

# Use pd.json_normalize to flatten the "known_for" field
df = pd.json_normalize(data.get('results', []), 'known_for', errors='ignore')

# Display the resulting DataFrame
df


