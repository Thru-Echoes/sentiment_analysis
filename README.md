# Sentiment Analysis 

EML / Google Alert scraping and language analysis. 

## Issues with first pass of scraping 

### Media sources with anti-scraping:

- **La prensa grafica** (La Prensa Gráfica)

## Alternative scraping methods 

Use of **headless browser** --> *i.e. Selenium*; acts as a web browser using the same drivers as a chosen browser but without the actual browser...(you do not see it but it acts like a browser in code).

## Tasks

1. Modify existing functions to return error message when errors happen (to track when anti-scraping error vs other errors)
2. Implement a Selenium (headless browser) approach to scrape text from web pages with anti-scraping 
3. Develop a filter to drop unrelated articles (not in scope articles)
4. Calculate top occurring words (tf-idf) and other relationships between words / articles etc 

## Workflow order 

Below is a diagram of the call order with some helpful notes: 

1. parse_eml_file(path) <br>
    ---- calls get_bodies(msg), returns plain_text, html_text <br>
    ---- calls extract_inboxmarkup_json(html_text), gets Google's embedded JSON <br>
    ---- for each link: <br>
        ---- call unwrap_google_url(url), returns URL <br>
    return email metadata and items with resolved_url <br>

<br>
<br>
2. For each item, collect unique resolved_url values 
<br>
<br>
3. For each resolved_url, call extract_website_details(url), returns [title, date_iso, body_text]