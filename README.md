# Cloudflare Turnstile Page & Captcha Bypass for Scraping

**We love scraping, don't we?** But sometimes, we face Cloudflare protection. This script is designed to bypass the Cloudflare protection on websites, allowing you to interact with them programmatically. 

## Sponsors

### Scrapeless

[![](https://github.com/user-attachments/assets/783ce396-fa8c-4e10-846e-86d0ba0d0144)](https://www.scrapeless.com/en/product/scraping-browser?utm_medium=github&utm_campaign=sarperavci-cap)

If you’re looking for an automation browser tool designed to bypass website bot detection systems, I highly recommend the [**Scrapeless Scraping Browser**](https://www.scrapeless.com/en/product/scraping-browser?utm_medium=github&utm_campaign=sarperavci-cap). This cloud-based browser platform features advanced stealth technology and powerful anti-blocking capabilities, making it easy to handle dynamic websites, anti-bot mechanisms, and CAPTCHA challenges. With a built-in **free CAPTCHA solver**, it is perfectly suited for web scraping, automated testing, and data collection—especially in environments with complex anti-bot defenses.
  
**Key Features:**

* **Built-in Free CAPTCHA solver:** Instantly solves reCAPTCHA, Cloudflare Turnstile/Challenge, AWS WAF, DataDome, and more.  
* **High-concurrency scraping:** Run 50 to 1000+ browser instances per task within seconds, with no server resource limits.  
* **Human-like browsing environment:** Dynamic fingerprint spoofing and real user behavior simulation, powered by the Scrapeless Chromium engine for advanced stealth.  
* **Headless mode support:** Compatible with both headful and headless browsers, adapting to diverse anti-scraping strategies.  
* **70M+ residential IP proxies:** Global coverage with geolocation targeting and automatic IP rotation.  
* **Low operating costs:** Proxy usage costs only $1.26 to $1.80 per GB.  
* **Plug-and-play integration:** Fully compatible with Puppeteer, Playwright, Python, and Node.js for seamless setup.

[**Scrapeless**](https://www.scrapeless.com/en?utm_medium=github&utm_campaign=sarperavci-cap) is an all-in-one, enterprise-grade, and highly scalable data scraping solution built for developers and businesses. Beyond the Scraping Browser, it also offers a [**Scraping API**](https://www.scrapeless.com/en/product/scraping-api?utm_medium=github&utm_campaign=sarperavci-cap), [**Deep SerpAPI**](https://www.scrapeless.com/en/product/deep-serp-api?utm_medium=github&utm_campaign=sarperavci-cap), and robust [proxy services](https://www.scrapeless.com/en/product/proxies?utm_medium=github&utm_campaign=sarperavci-cap).
  
👉Learn more: [**Scrapeless Scraping Browser Playground**](https://app.scrapeless.com/passport/login?utm_medium=github&utm_campaign=sarperavci-cap) **| [Scrapeless Scraping Browser Documentation](https://docs.scrapeless.com/en/scraping-browser/quickstart/introduction/?utm_medium=github&utm_campaign=sarperavci-cap)**  



# How does this script work?

If you use Selenium, you may have noticed that it is not possible to bypass Cloudflare protection with it. Even you click the "I'm not a robot" button, you will still be stuck in the "Checking your browser before accessing" page.
This is because Cloudflare protection is able to detect the automation tools and block them, which puts the webdriver infinitely in the "Checking your browser before accessing" page.

As you realize, the script uses the DrissionPage, which is a controller for the browser itself. This way, the browser is not detected as a webdriver and the Cloudflare protection is bypassed.


## Installation

You can install the required packages by running the following command:

```bash
pip install -r requirements.txt
```

## Demo
![](https://cdn.sarperavci.com/xWhiMOmD/vzJylR.gif)

## Usage

Create a new instance of the `CloudflareBypass` class and call the `bypass` method when you need to bypass the Cloudflare protection.

```python
from CloudflareBypasser import CloudflareBypasser
from DrissionPage import ChromiumPage

driver = ChromiumPage()
driver.get('https://nopecha.com/demo/cloudflare')

cf_bypasser = CloudflareBypasser(driver)
cf_bypasser.bypass()
```

You can run the test script to see how it works:

```bash
python test.py
```

# Introducing Server Mode

Recently, [@frederik-uni](https://github.com/frederik-uni) has introduced a new feature called "Server Mode". This feature allows you to bypass the Cloudflare protection remotely, either you can get the cookies or the HTML content of the website.

## Installation

You can install the required packages by running the following command:

```bash
pip install -r server_requirements.txt
```

## Usage

Start the server by running the following command:

```bash
python server.py
```

Two endpoints are available:

- `/cookies?url=<URL>&retries=<>&proxy=<>`: This endpoint returns the cookies of the website (including the Cloudflare cookies).
- `/html?url=<URL>&retries=<>&proxy=<>`: This endpoint returns the HTML content of the website.

Send a GET request to the desired endpoint with the URL of the website you want to bypass the Cloudflare protection.

```bash
sarp@IdeaPad:~/$ curl http://localhost:8000/cookies?url=https://nopecha.com/demo/cloudflare
{"cookies":{"cf_clearance":"SJHuYhHrTZpXDUe8iMuzEUpJxocmOW8ougQVS0.aK5g-1723665177-1.0.1.1-5_NOoP19LQZw4TQ4BLwJmtrXBoX8JbKF5ZqsAOxRNOnW2rmDUwv4hQ7BztnsOfB9DQ06xR5hR_hsg3n8xteUCw"},"user_agent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36"}
```

## Docker


You can also run the server in a Docker container. Thanks to [@gandrunx](https://github.com/gandrunx) for Dockerizing the server.

First, build the Docker image:

```bash
docker build -t cloudflare-bypass .
```

Then, run the Docker container:

```bash
docker run -p 8000:8000 cloudflare-bypass
```

Alternatively, you can skip `docker build` step, and run the container using pre-build image:
```bash
docker run -p 8000:8000 ghcr.io/sarperavci/cloudflarebypassforscraping:latest
```

## Example Projects

Here are some example projects that utilize the CloudflareBypasser Server:

- [Calibre Web Automated Book Downloader](https://github.com/calibrain/calibre-web-automated-book-downloader) - A tool to download books from calibre web.
- [Kick Unofficial API](https://github.com/sarperavci/kick-unofficial-api) - A tool to interact with the Kick.com, download videos, send messages, etc.

## Star History

<a href="https://star-history.com/#sarperavci/CloudflareBypassForScraping&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=sarperavci/CloudflareBypassForScraping&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=sarperavci/CloudflareBypassForScraping&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=sarperavci/CloudflareBypassForScraping&type=Date" />
 </picture>
</a>
