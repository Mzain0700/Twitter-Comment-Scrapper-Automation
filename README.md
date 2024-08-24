# Twitter Scraper Automation Script
## Introduction
This project is a pioneering implementation of a Twitter comment scraping automation script, designed and developed entirely by me. The script enables efficient extraction of comments from specific tweets, a task that has not been addressed in this exact manner before. The code is tailored to interact with Twitter's dynamic web content, automating the process of logging into a Twitter account, navigating to individual tweet URLs, and systematically collecting user comments along with associated metadata such as user IDs, timestamps, and tweet content.

The goal of this project is to create a robust and reusable solution for researchers, data analysts, and developers who need to gather large volumes of Twitter data without relying on the official Twitter API. By leveraging Selenium for browser automation, this script can handle Twitter's web interface in real time, ensuring that all comments, including those loaded dynamically as the user scrolls, are captured accurately.

It allows for the organization and storage of data in CSV format, facilitating easy analysis and integration into other workflows. The codebase is fully original, representing a unique contribution to the field of web scraping and automation.

## Prerequisites
Before running the scripts, ensure that you have the following installed:

- Python (version 3.7 or higher)
- Selenium (pip install selenium)
- Google Chrome and ChromeDriver (Make sure ChromeDriver is compatible with your version of Chrome)
- ntscraper (pip install ntscraper)
- pandas (pip install pandas)

## Steps to Generate Tweets Link and Text CSV
### 1.  Setting Up the Tweet Scraper Script :
   - To extract tweets and save their links and texts into a CSV file, you will use the **"Tweets_scrapper.ipynb"** script. This script utilizes the ntscraper library to fetch tweets based on a specific username or hashtag.

### 2.  Install the required package
   - ntscraper (pip install ntscraper)
   - pandas (pip install pandas)
### 4.   Running the Script
  - Run the script to generate a CSV file of your username or hashtag provided in code containing the following columns:

    - link: The URL of the tweet
    - text: The content of the tweet
    - user: The username of the tweet author
    - likes: The number of likes on the tweet
    - quotes: The number of quotes of the tweet
    - retweets: The number of retweets
    - comments: The number of comments on the tweet
This CSV file will be used as input for the next step.

## Steps to Scrape Comments from Tweets
### 1. Preparing the Comment Scraper Script
   - Once you have generated the tweets CSV file, you can use the **Tweets_comment_scrapper.ipynb** script to scrape comments from those tweets. This script automates the process of opening each tweet URL, scrolling through the comments, and saving them into another CSV file.
### 2. Running the Script
   - Importing libraries necessary for browser automation, file handling, and managing delays.
   -  Initialize a Chrome browser instance that will be controlled by Selenium. This is the first step in automating interactions with Twitter.
   -  This Login function automates the process of logging into Twitter by navigating to the Twitter login page.
   -  The Function to Scrape Tweet Comments
      - The tweet URL is split to extract the user profile and tweet ID, which are used to name directories and files for storing scraped data.
      - Creates a directory named after the user profile if it doesn’t already exist, which will hold the CSV files.
      - Navigates to the tweet’s page and waits 17 seconds to ensure the page fully loads, including all comments.
      - Extracts the date and time of the main tweet post and formats them appropriately.
      - Creates a unique filename using the tweet ID and date to store the scraped data.
      - Opens the CSV file for writing and writes the header row to define the structure of the CSV file.
      - Tracks the last scroll position and initializes a set to track seen comments, preventing duplicates.
      - Starts the loop to scrape comments, with each comment represented as a web element.
      - Extracts the comment’s unique datetime identifier and skips already processed comments.
      - Extracts the user ID, comment text, and datetime of the comment.
      - Checks if the comment contains text and stores it; otherwise, it notes that no text was found.
      - Scrolls down the page to load more comments, waits for them to load, and stops scrolling when no new content is loaded.
      -  Handles any errors during the scraping process and returns a success status
   -  Main Script Execution
      - Replaces placeholders with your Twitter credentials and logs into the account
      - Opens the input CSV file containing tweet URLs and prepares to process each tweet.
      - Attempts to scrape comments for each tweet URL. Successfully processed tweets are moved to a different file, while unsuccessful ones are stored for reprocessing.
      - Overwrites the original CSV file with only the rows that were not successfully processed, allowing for retry.
      - Closes the Chrome browser and ends the Selenium session.

## Usage Notes
This script is a powerful tool for scraping Twitter comments but must be used responsibly and within Twitter’s terms of service. Ensure that the usage does not violate any rules and consider implementing rate-limiting mechanisms if scraping a large number of tweets.
## Future Improvements
- **Error Handling:** Enhance error handling to better manage unexpected issues during scraping.
- **Rate Limiting:** Implement rate-limiting to avoid Twitter blocking the account due to excessive requests.
- **Headless Mode:** Consider running the Chrome browser in headless mode for better performance in server environments.

## CSV Combiner
- This code will create unique files for every tweet. You can combine all csv files too a single csv file using csv combiner file.

## Conclusion
This project demonstrates a novel approach to Twitter data scraping by combining ntscraper for fetching tweet details and Selenium for automating browser interactions to scrape comments. The two scripts work together to provide a comprehensive solution for gathering and analyzing Twitter data. This implementation is the first of its kind, created entirely by me, and provides a powerful tool for extracting valuable insights from Twitter.


If you are problem with adding chrome drivers download from this link 
    https://getwebdriver.com/chromedriver#stable
Paste the path of this driver in your environment variable of your pc.
