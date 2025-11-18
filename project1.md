[Back to Portfolio](./)

Project 1 Automated Web Scraper 
===============

-   **Class:** CSCI 301
-   **Grade:** 100 (A)
-   **Language(s):** Python
-   **Source Code Repository:** [Source Code ](https://github.com/Bdev2325/SeniorPortfoiloSourceCode1/blob/main/Webscraper.py)
    (Please [email me](mailto:bjcooper2e@csustudent.net?subject=GitHub%20Access) to request access.)

## Project description

This project is an **automated web scraper** built using Python. Its primary purpose is to collect job listings from a sample job site and display  information about positions related to **Python**.

The scraper uses two core Python Libraries:
- **'requests'** - to fetch web pages.
- **'BeautifulSoup'** (from 'bs4') - to parse HTML and search for structured data.

Combinging these tools allows the program to automate the process of gathering and filtering job postings from a webpage.
It demostrates how webscraping techniques can be applied to extract meaningful information from HTML sources for analysis or automation.

## How to run the program

There are two prerequisites prior executing the program

- Python 3.x installed on your system
- The following libraries installed:

```bash
pip install requests beautifulsoup4
```
Steps to Run:

1. Download or clone the repository containing test.py.
2. Open a terminal  in the directory containing the script.
3. (execute) Run the program with:

```bash
python test.py
```
4. The script connects to the sample site:
```
https://realpython.github.io/fake-jobs/
```
and outputs application links for the **Python-related** job listing.

## UI Design

User Tasks:
- The user simply runs the program from the terminal, no inputs are required.

**Program Functionally** (What the Program Does):
When executed, the program:
- Connects to the target website
- Downloads its HTML content.
- Parses the job listings section.
- Searches for job titles containing the keyword "Python".
- Extracts and displays the application links for these jobs.

The output gives users a quick way to view or access available Python-related job postings without manually browsing the site.

How It Works:

1. Import Libraries
   - Uses 'requests' for HTTP and BeautifulSoup for HTML parsing.
     
2. Fetch HTML Content
   
   ```python
   URl = "https://realpython.github.io/fake-jobs/"
   page = requests.get(URL)
   ```
3. Parse the Page
   
   ```python
   soup = BeautifulSoup(page.content, "html.parser")
   ```
   Builds a searchable parse tree of the webpage.
   
4. Locate Job Listings Container

   ```python
   results = soup.find(id="ResultsContainer")
   ```
5. Filter for Python Jobs

   ```python
   python_jobs = results.find_all(
      "h2", string=lambda text: "python" in text.lower()
   )
   ```
6. Extract and Display Links

   ```python
   for job_element in python_jobs:
       links = job_element.find_all("a")
       for link in links:
           print(f"Apply here: {link['href']}\n")
   ```

## UI Design

- Requests + BeautifulSoup pairing: Lightweight and simple for HTTP + HTML parsing.
- Scoped searching: Targets only the main results container for accuracy.
- Keyword filtering: Uses a 'lambda' for flexible case-insensitive matching.

After installing bs4 and python3 excute the script (see Fig 1), consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat (see Fig 2). Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum (see Fig 3).

![screenshot](images/Webscraper3.jpg)  
Fig 1. The launch screen

![screenshot](images/webscraper1.jpg)  
Fig 2. Example output after input is processed.

![screenshot](images/webscraper2.jpg)
Fig 3. Example output after input is processed.



[Back to Portfolio](./)
