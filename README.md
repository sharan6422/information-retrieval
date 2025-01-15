# information-retrieval

VERTICAL SEARCH ENGINE

1. Introduction
Information Retrieval, in simple words means, finding the information which is relevant to the partial information provided by user within a large collection of data stored in databases. 
The technological revolution has been accelerated by the internet and helped us in connecting people around the world. With 5.18 billion users worldwide, it is evident that world wide web has been an integral part of our lives. It is impossible to imagine the internet without search engine. Search engines have grown to a point where they are shaping how the businesses are being operated. In basic definition, a search engine is a software used to extract information out of a database in regards to the user's queries. In the coursework, I have used relevant libraries, functions and imports to create a vertical search engine. This search engine has the ability to retrieve publications from coventry university center for global learning section.
I have made sure that at least one of the authors of the publication is a member of CGL. Functions and imports have been installed in the code to make sure that the search engine is polite. The code makes sure that the search engine is not hitting the servers too fast. The program runs in a way that the search engine crawls through the relevant websites in an interval of 7 days. The rules of robots.txt is followed.The search engine is designed to crawl the website to look for new information every week. We have used schedule library to schedule this functionality.

1.1 Imported Libraries
All the relevant libraries were imported so as to make sure that the code works properly. 
requests: This library retrieves data from URLs by sending HTTP requests to web servers. I have used requests library to make HTTP GET requests to fetch the content of web pages for web scraping.bs4 (BeautifulSoup): BeautifulSoup or bs4, parses and navigates HTML and XML documents. It also helps in extracting relevant elements and data from web pages and URLs. I have used the bs4 library to parse the HTML content of web pages obtained using requests and extract publication details from the web pages.pandas (imported as pd): The pandas library is a powerful data manipulation and analysis library in Python. It provides data structures like DataFrame and Series that are highly efficient for working with structured data. I have used pandas to read, process, and store data in tabular format (e.g., CSV files) and perform operations on the data. time: all the time-related operation are handled through the time library. it provides functions and methods to help this happen in python. I have used this library to introduce a delay between web requests to be polite and avoid overloading the server during web scraping. datetime: This library is helpful in handling date and time in the codes. We can extract current date and time for our operations. datetime library also helps in performing time related calculations on the code. string: String library can be used to extract constants respresenting the ASCII characters. We can also use this library in preprocessing where it removes the punctuation marks. json: This library helps us in working with JSON (JavaScript Object Notation) data. Data handling and other storage related functions was fecilitated by this library. nltk (Natural Language Toolkit): The nltk library is a comprehensive library for natural language processing (NLP) tasks in Python. In this code I was able to do tokenization, lemmatization and other preprocessing tools to both the data and query. Other preprocessing tasks like removing stopwords, part-of-speech tagging, stemming etc was also done using this.

These libraries greatly enhance the capabilities of Python for web scraping, data manipulation, and natural language processing tasks, making it easier to work with complex data and text-based projects.

The list of libraries imported are listed below
requests library imported
BeautifulSoup imported from bs4
pandas imported as pd
time library imported 
datetime library imported 
string library imported
json library imported
nltk library imported
pos-tag  

stopwords imported from nltk.corpus
wordnet imported from nltk.corpus
WordNetLemmatizer imported from nltk.stem

2.0 Crawler
Crawler is arguable the most important component of the search engine. It can be considered as a breadth-first search (BFS) that travels the internet.
The process of crawling starts from a URL set or seed URL. Crawler fetches a webpage first, then it parses it to extract all linked URLs. This process is repeated for all web URLs not seen before. web crawler strategies includes breadth first search algorithms, depth first search algorithms and page rank algorithms. The publication title, its URL, author's name, authors's profile URL, publication year and other details are extracted from the webpage. The publications are stored in a list and the staff into is stored in a dictionary. 

while loop is used to loop through the pages with the page number as the loop condition. The details are extracted and stored. If the details are not found, a message is displayed. When extracting information from a a page is completed, the count of current-page is increased. This goes on till the current-page is equal to the total number of pages. Then a 'Pages end here!!' message is displayed. The total number of authors is found out to be 76, maximum number of distinct publications per staff is 47, totla number of publications are  286 and the maximum number of distinct publication per staff is 47.

2.1 Scrapping the Data
In the code I used, the coventry university web page is first scraped. We import necesssary libraries to achieve this first. These include 'csv', 'time', 'BeautifulSoup', 'requests' and 'urljoin'.
To make sure that the crawler is not hitting the servers too often, we use fetch-crawl-delay(url) function. This makes sure that there is a delay between successive requests.
The URL used for web scraping is https://pureportal.coventry.ac.uk/en/publications/. The data about the publucation, URL and authors are scraped and stored in a database.
fetch-publication-details(url,crawl-delay) function scrapes the publication details from the given URL which contains the details of the publications.
save-to-csv(publications,csv-file) function saves the extracted publication details to a csv file.
The main() function initiates the web scraping and the csv file creation processes. It calls the fetch-crawl-delay function to make sure that the search engine is polite. the main function also contains the loop which crawls through the list of publications on each page. Finally the details are stored in a csv file named 'publications-and-hyperlinks.csv'

Then the csv is loaded into a dataframe and printed. using pd.read-csv() method, we load csv file into a dataframe. I also renames the column with the label 'Unnamed: 0' to 'SN' (Serial Number) using the rename() method. Then the main() function renames the name of CSV file to 'csv-file'. Then the dataframe is retured using the load-sample-database() function . The returned data frame is is assigned to sample-df. The DataFrame is printed using print(sample-df).

2.2 Operations of CSV
def load-and-rename-csv(csv-file) function reads the csv file into dataframe using pd.read-csv(csv-file) method. .rename(columns={'Unnamed: 0': 'SN'}) method renames the 'Unnmaes:0' column to 'SN' in the datafrom. def update-dataframe(df) function updates the datafrome by adding the SN(serial number) attribute and increases the values with regards to the number of entries added. def save-dataframe-to-csv(df, csv-file) function takes a dataframe as input and saves it as a csv file.

We load the data from CSV file named 'publication-titles-and-hyperlinks.csv' make necessary changes like addition of serial number and update the dataframe back to a csv file. This is then displayed as updated dataframe named 'updated-sample-df'


2.3 Duplicate values
The CSV file is read into a pandas dataframe. The 'Title' column of the dataframe is extracted and assinged to variable 'ids'. ids.duplicated() generated a boolean series where is decides whether the values in 'titles' is duplicated or not. The resulting DataFrame containing the duplicate rows is returned by the function. The main function uses head(7) method on the DataFrame to get the first 7 rows and assigns it to sample-db-head.The sample-db-head and duplicate-rows are printed

2.4 Sceduling the crawler
The variables days and interval are initialised in the beginning. A function call is used to scrape data from the website. The date and time of the last crawl will be printed using f"Crawled at {datetime.datetime.now().strftime(''). The format used is YYYY-MM-DD HH:MM:SS. The date for next crawl is also printed. The day variable is incremented after each day and next crawl is done is the pre determined day.

3.0 Indexer

From the processed-initial-db dataframe, the first row is extracted and stored. This is done to work with this data without modifying the complete code. An empty dictionary is created and named as indexing-trial. Individual words are then seperated considering the SN or serial number. A line is then printed to separates the consecutive outputs for better readability. 
Then the function index-documents-for-row() with inputs and index as arguments are used. The 'Title' column is split and stored into variable called words. It is checked whether the current word is already present as a key in dictionary index. If it is not, it is added. This is done to avoid duplication. A key-value pair in index dictionary is created. This loop is run till all the words have been 
processed. 




4.0 Query Processor
Libraries like 'string', 'nltk', 'stopwords', 'wordlemmatizer', 'pos-tag' and 'wordnet'. has been imported. The stopwords like 'this', 'is', 'and' etc are removed during query processing. Lemmatization is an important step and is used to get relevant results from the web. preprocess-query(query) function makes sure that the query is suitable for searching. The query is converted to lowercase and case-insensitive matching is done. get-wordnet-pos(tag) function takes a part-of-speech tag as input and maps it to subsequent tag of wordnet POS. In the wordnet database, the information of word meaning, synonyms etc are avilable. preprocess-query(query) function performs lematizzation by takenizing the individual words using 'nltk-word-tokenize'. The lemmatized text are returned in the form of a conccatinated string. Then a  loop is executed through the dataframe df. A variable 'inpt' is initialised and with each iteration, a row from 'df' is stored into inpt. The loop continues toll all the rows of data in 'df' is processed. The apply-index function processes the 'title' and 'SN". 
From the current row and updates the index accordingly. The data in df is then preprocessed using the function preprocess-df(). Full index function is then used to proces processed-db and store the final indexes of all words. Finally, the index data is saved and loaded to JSON file. A new file 'indexes.json' is saved. and used json.dump() method to write contents from indexes dictionary to this file. 


5.0 Search Engine
A function called 'vertical-search-engine' is defined and this performs a search operation on the dataframe named 'data-df'. As we already has an index that maps words to its serial number, the query is sorted in a ranked order. We use an empty list called retrieved-indexes to store the SN vales for each word in the query. A loop goes through the query-terms list which has the split version of the input query. The retrieved-indexes.append(index[word]) will append the SN of the corresponding index.
get-intersection() and get-union() retrieves the intersection and union of list in retrieved-indexes. The final list of SN of search results are stored in result-indexes variable. The final-output contains the data filtered from the data-df to include only  the rows whose SN are in results-index. The results, SN values and final-output  are stored in results-df dataframe. Based on rannked retrieval order the matching results are found and returned.

Vertical-search-engine function performs  search on dataframe using query and index and the result is returned in a ranked order based on intersection and union of SN values.


