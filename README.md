# Amazon-web-scraping-project

This project is a simple web scraper built in Python to track the price of a specific product on Amazon. The scraper collects data at regular intervals and stores it in a CSV file. Additionally, it can send an email alert when the product's price drops below a certain threshold.

## Features

- Scrapes product title and price from Amazon
- Stores the scraped data in a CSV file
- Appends new data to the existing CSV file
- Runs at regular intervals (every 24 hours)
- Sends an email alert when the product's price drops below a specified amount

## Requirements

- Python 3
- BeautifulSoup
- Requests
- smtplib
- pandas
- csv

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/amazon-price-tracker.git
    cd amazon-price-tracker
    ```

2. Install the required Python packages:

    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. **Set up the web scraper:**

    The script is designed to scrape the price and title of the product from the given Amazon URL. You may need to change the URL in the `check_price` function to track a different product.

2. **Running the script:**

    The script is set to run indefinitely, scraping data every 24 hours. To start the scraper, simply run:

    ```bash
    python scraper.py
    ```

3. **Email Alert:**

    To enable email alerts, update the `send_mail` function with your email credentials. Note that you may need to enable "less secure app access" in your email account settings.

    ```python
    def send_mail():
        server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
        server.ehlo()
        server.login('your-email@gmail.com', 'your-password')

        subject = "The product you want is below the target price!"
        body = "The price of the product you are tracking has dropped. Check the link: [Product Link]"
        msg = f"Subject: {subject}\n\n{body}"

        server.sendmail(
            'your-email@gmail.com',
            'recipient-email@gmail.com',
            msg
        )
        server.close()
    ```

### Libraries

- `bs4` (BeautifulSoup): Parses HTML and XML documents
- `requests`: Sends HTTP requests
- `time`: Provides various time-related functions
- `datetime`: Supplies classes for manipulating dates and times
- `smtplib`: Defines an SMTP client session object
- `csv`: Implements classes to read and write tabular data in CSV format
- `pandas`: Provides data structures and data analysis tools

### Main Functions

- `check_price()`: Scrapes the Amazon product page for the title and price, and writes the data to a CSV file.
- `send_mail()`: Sends an email alert when the product's price drops below a specified amount.

