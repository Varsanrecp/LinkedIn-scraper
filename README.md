# 🔗 LinkedIn Profile Scraper

A Python project that uses **Selenium** and **Beautiful Soup (BS4)** to automatically log into LinkedIn, navigate to a specific profile, and scrape detailed information, including the user's name, headline, 'About' section, Certifications, Projects, Courses, and Honors & Awards.

---

## 🛠️ How It Works

This script automates the following steps:

1.  **Setup:** Imports necessary libraries (`selenium`, `bs4`) and loads credentials from a `.env` file.
2.  **Login:** Initializes a Chrome browser, navigates to the LinkedIn login page, and uses your credentials to log in.
3.  **Basic Profile Data:** Navigates to the target profile URL and scrapes the **Name**, **Headline**, and **About** section.
4.  **Detailed Sections:** It uses Selenium's `click()` function to navigate to the "See all" pages for **Certifications**, **Projects**, **Courses**, and **Honors & Awards**.
5.  **Data Extraction:** For each section, it scrapes the new page source using **Beautiful Soup**, extracts the relevant details (like names, dates, and institutions) using helper functions, and stores the structured data in a main `profile_data` dictionary.
6.  **Navigation:** Uses `driver.back()` and strategic `sleep()` calls to ensure proper page loading and navigation between sections.

---

## 🚀 Getting Started

Follow these steps to set up and run the script on your local machine.

### Prerequisites

You need to have **Python** installed. You'll also need the following tools:

1.  **Google Chrome:** The browser the script will automate.
2.  **ChromeDriver:** A compatible WebDriver for your version of Chrome. (Modern Selenium often handles this automatically, but you may need to download it manually if you face issues).

### Installation

1.  **Clone the repository (if applicable):**
    ```bash
    # git clone <repository-url>
    ```

2.  **Install the required Python libraries:**
    ```bash
    pip install selenium beautifulsoup4 lxml python-dotenv
    ```

### Configuration

You must set up your login credentials so the script can access your LinkedIn account.

1.  **Create a `.env` file** in the same directory as your Python script.
2.  Add your LinkedIn email and password to this file using the keys `EMAIL` and `PASSWORD`.

    **.env file content:**
    ```
    EMAIL="your_linkedin_email@example.com"
    PASSWORD="your_linkedin_password"
    ```

### Running the Script

1.  Make sure your `.env` file is configured correctly.
2.  Ensure the target LinkedIn URL (e.g., `https://www.linkedin.com/in/laxmimerit`) is correctly set in the script.
3.  Execute the Python file:
    ```bash
    python your_script_name.py
    ```

The script will open a Chrome browser window, log in, navigate the profile sections, and finally print the scraped data as a Python dictionary.

---

## ⚠️ Important Note on Scraping

Web scraping, especially on dynamic sites like LinkedIn, can be fragile.

* **HTML Class Changes:** LinkedIn frequently updates its website structure, which means the CSS classes used for scraping (like `'UXwXGvkZjLHXTkTzfStIRtZBcIdwKURDfTbmzc inline t-24 v-align-middle break-words'`) will likely change over time. If the script breaks, you will need to inspect the LinkedIn page source to find the new class names.
* **Rate Limiting:** Aggressive scraping can result in your account being temporarily restricted or banned. Use this script responsibly and for personal, legal purposes only.
* **Using `sleep()`:** The script relies on `time.sleep()` to wait for pages to load. If your internet connection is slow, you may need to increase the sleep values to prevent `AttributeError: 'NoneType' object has no attribute 'find_all'`.