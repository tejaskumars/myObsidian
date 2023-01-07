
Selenium is used to automate the web, or scrape the content from websites. It can be used with Python, Java and other languages. Selenium can become very handy when you dive deep into it, like bypassing captchas, scraping sophisticated websites and many more.

Github repo of Micheal - https://github.com/michaelkitas/Python-Selenium-Tutorial 

```
from selenium import webdriver 
from selenium.webdriver.common.by import By 

driver = webdriver.Chrome()  #make sure the chromedriver.exe is in same folder 
driver.get("URL")

elem _list = driver.find_elements(By.CLASS_NAME , "<class_name>")

```

- use `chromedriver_autoinstaller` to install correct version of chrome driver automatically.
- How to wait untill the webiste loads and the element is found? 
	``` 
	from selenium.webdriver.support.wait import WebDriverWait

	element = WebDriverWait(driver , 10).untill(EC.presence_of_element  _located(By.CLASS_NAME , "<class_name>")
	```
- How ro bypass captchas? using [2captcha](https://2captcha.com/)
	- recaptcha
		- `pip install 2captcha-python` 
		-  from twocaptch import Twocaptcha
		- go to the website and find the data site key by inspecting and going to the console, pass that as input along with the website url to the code outputted by the captcha website. 
		- To automate the process, you need to modify the source code of the website, this can be achieved by `driver.execute_script()` method, where a javascript code can be executed. 
	- normal captcha 
		- Find the image, take a screenshot of it and save it using `img.screenshot("path_to_save")` 
		- pass the screenshot along with url as input to the code outputted by 2captcha website, after autheticating with API keys. 
		- Pass the output received by the service into the text area using `send_keys(data)` method. 
		- FInd the submit button and click it. 
	- hcaptcha 
		- same as recaptcha.

- How to block from websites knowing we are using selenium? 
	-  install a package `pip install undetected-chromedriver` 
	- use a proxy Ip address by adding it in `ChromeOptions` 
	- use your gmail acc to go undetected : `options.add_argument('--user-data-dir=')`  , add folder to your chrome profile `chrome > version > profilePath` here. (replace profile number with "Default")
	- Make sure your driver is visible and not `--headless`  
- how to use, save and resure cookies? 
	- use `driver.get_cookies()` method to get the cookies and save it to a `.pkl` file. 
	- Cookies are nothing but an object of key value pairs containing some credible info of the user, mainly helps in maintaing the history of user activity, passwords etc. 
	- load the the save cookies file, make sure the domain is correct and uniform across all objects, add cookies to the driver using `driver.add_cookie(cookie)` for all cookies. some of them might error out. 
- Capture, Block and Mock requests and responses using **Selenium wire** (https://pypi.org/project/selenium-wire/)
- How to scroll infinetely? 
	- you can scroll infinitely by having the height readjustment in the code, follow the github link in the start to know more. 
- 