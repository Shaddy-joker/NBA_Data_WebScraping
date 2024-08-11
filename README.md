# NBA Data Scraping Project

## Overview
This project focuses on scraping NBA player statistics data from the official NBA stats website using Python. It collects data for multiple seasons and both regular season and playoff games, providing a comprehensive dataset for analysis.


## Tools Used
- **Python**: The primary programming language used for this project.
- **pandas**: Used for data manipulation and creating DataFrames.
- **requests**: A library for making HTTP requests to fetch web pages.
- **numpy**: Used for numerical operations, particularly for generating random wait times.
- **time**: Used for introducing delays between requests to avoid overloading the server.
- **Jupyter Notebook**: Used for interactive development and running the scraping script.

## Data Source
The data is scraped from the official NBA stats website: `https://stats.nba.com`

## Implementation Details

### Headers
Custom headers are used in the HTTP requests to mimic a browser and avoid being blocked:

```python
header = {
    'accept':'*/*',
    'accept-encoding' : 'gzip, deflate, br, zstd',
    'accept-language': 'en-GB-oxendict,en-US;q=0.9,en-IN;q=0.8,en;q=0.7',
    'connection' : 'keep-alive',
    'host': 'stats.nba.com',
    'origin' : 'https://www.nba.com',
    'referer': 'https://www.nba.com/',
    'user-agent': 'Mozilla/5.0 (Linux; Android 13; SM-G981B) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Mobile Safari/537.36'
    # ... (other headers)
}
```

### Data Collection
- The script iterates through multiple NBA seasons (from 2012-13 to 2023-24) and collects data for both regular season and playoffs.
- For each season and type, it makes an API request to the NBA stats website.
- The data is then parsed from the JSON response and stored in a pandas DataFrame.

### Rate Limiting
To avoid overwhelming the server and potentially getting blocked, the script implements a random delay between requests:

```python
lag = np.random.uniform(low=5, high=40)
time.sleep(lag)
```

## Data Structure
The collected data includes various player statistics such as:
- Player ID, Name, Team
- Games Played, Minutes Played
- Field Goals (Made, Attempted, Percentage)
- 3-Point Field Goals (Made, Attempted, Percentage)
- Free Throws (Made, Attempted, Percentage)
- Rebounds (Offensive, Defensive, Total)
- Assists, Steals, Blocks, Turnovers
- Points, Efficiency Rating

## Output
The final dataset is saved as an Excel file named 'nba_player_data.xlsx'.

## What I Learned

### Web Scraping Techniques
- How to navigate and parse JSON responses from an API
- Implementing custom headers to mimic browser behavior
- Handling rate limiting to avoid being blocked by the server

### Data Processing with pandas
- Creating and manipulating DataFrames
- Concatenating data from multiple API calls into a single DataFrame

### API Interaction
- Constructing API URLs with different parameters for seasons and game types
- Parsing JSON responses from an API

### Python Skills
- Working with libraries like requests, pandas, and numpy
- Implementing loops to iterate through multiple seasons and game types
- Error handling and logging (though not explicitly shown in the provided code)

### Project Management
- Organizing code in a Jupyter Notebook for easy execution and documentation
- Implementing a systematic approach to collect data over multiple seasons

## Future Improvements
- Implement error handling for failed requests
- Add more detailed logging of the scraping process
- Expand the dataset to include more advanced statistics or player information
- Create visualizations or analysis tools to explore the collected data
- Implement an automated update system to keep the dataset current

## Conclusion
This project demonstrates the process of collecting comprehensive NBA player statistics through web scraping techniques. It provides a valuable dataset for basketball analytics and showcases important skills in data collection, API interaction, and Python programming.

## Credits
This project was implemented following the tutorial and guidance provided by Alex Sington in his YouTube video on NBA data scraping (https://www.youtube.com/watch?v=nHtlRlWmTV4). His clear explanations and step-by-step instructions were instrumental in the development of this script.
