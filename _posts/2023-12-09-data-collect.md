---
layout: post
title:  "Crash Landing on Data"
author: "Camilla McKinnon"
description: "Webscraping with Selenium and Beautiful Soup"
image: "/assets/images/data_collect_photo.jpg"
--- 

## Introduction

I was pulled into the world of Korean dramas, or “K-dramas,” my freshman year of college. Since then, K-dramas have quickly become my number one choice whenever I want to relax and watch a show. The title of this post references a popular drama and one of my personal favorites, called "Crash Landing On You".

I discoverd My Drama List, a community-driven platform with information regarding all things dramas. You can find all the information you ever wanted on your favorite Asian dramas. You can get the latest scoop on upcoming shows and movies, see what your favorite actors are doing, and peruse various lists of dramas. I was interested in the page that ranked the most popular dramas. With limited time to sit down and watch a show, I want the data on which dramas are the best!

Some of the questions I want to consider as I dive into my exploratory data analysis are
* Are some genres consistently rated higher than others?
* What is the relationship between show length (number of episodes) and viewer rating?
* How has show length changed over the years?
* Who are the most popular actors?
* Did veiwership increase after COVID-19?
* Which streaming service provides viewers with shows that have the highest ratings?

## How the Data Was Collected

I scraped my data from <a href="https://mydramalist.com/" target="_blank">MyDramaList.com</a> Specifically, I was looking at the list of shows by popularity, found <a href="https://mydramalist.com/shows/top" target="_blank">here</a>.

#### **Ethical Considerations** 
This data is published online and available to the public, so there were no ethical concerns with scraping the data.

## Scraping the Data

#### Using Beautiful Soup:

For the first part of my dataset, I utilized the python package BeautifulSoup. The information for title, year, country, episode count, rank, and score are present on the front page. The hardest part of this section was finding the tags in the inspect page, but other than that it was pretty smooth-sailing. 

This is an example code snippet for scraping data from the front page:

```
# SHOW TITLES
titles = []
show_titles = soup.find_all('h6', class_='text-primary')
for title in show_titles:
    title = title.text.strip()
    titles.append(title)
```

#### Using Selenium:

The other information I wanted (streaming service options, genres, and number of watchers) required clicking on the title of each drama. Selenium is a great package for clicking and navigating websites when scraping. 

The hardest part of this code section was clicking the right places at the right time! Each title had to be clicked, but before you could do that you had to make sure the page had loaded, and then scroll the page so the computer could see the title. I also implemented try/catch code to help with some of the pages taking too long to load. This helepd the code continue after errors instead of crashing each time. 

Here is a code snippet for scrolling and clicking on a title and then scraping the genre:

```
# Clicking on the title...
try:
    # scroll title into view
    driver.execute_script("arguments[0].scrollIntoView();", element)
    driver.execute_script("window.scrollBy(0, arguments[0]);", -100)
    time.sleep(1)
    element.click()
except TimeoutException as error:
    print("Timeout error- clicking title ")   

# get the genre
#print("Searching for genre...")
try:
    genres_section = driver.find_element(By.CLASS_NAME, 'show-genres')
    #print(genres_section.text)        
    genres.append(genres_section.text)
except:
    print("Genre not found")
    genres.append('na')
```

## Cleaning the Data
After I had merged the data from each part above, I moved on to cleaning it. I had to make sure my numbers were stored as integers or floats, not strings. I also did some string manipulation to extract the information that I wanted. 

Here's an example of extracting the country, year, and episodes. When I first scraped this element, it came out as a string looking like "Korean Drama 2023, 18 episodes". I separated by spaces to extract the country, then by commas to get the year and episodes.

```
# extract the year
year = info.split(',')[0][-4:]
year = int(year)
years.append(year)
# extract the episode
episode = info.split(',')[1]
numbers = re.findall(r'\d+', episode)
ep_length= int(numbers[0])
episodes.append(ep_length)
# extract the country
country = info.split(' ')[0] 
countries.append(country)
```
The last thing I did was change how network and genre were stored. They were originally scraped as strings (for example "Genres: Romance, Fantasy, Family"). I searched all the genres strings to get a list of the unique genres. Then I created a column in my dataframe for each genre, and included a 1 if the genre was present, 0 if not. After that I chose dropped networks and genres that didn't have at least 15 occurences. You can see this code at the link below.

---

Once the data was cleaned, I stored it as a csv file to make it easier for future data analysis. 

Check out my code for collecting and cleaning the data <a href="https://github.com/camilla47/termProject/tree/main/code" target="_blank">here</a>.

## Conclusion
I learned a lot about the Beautiful Soup and Selenium packages while preparing this dataset. Things that are simple for a human to do, like clicking a button, are more complicated when trying to do it in your code! I am excited to start analyzing these dramas and discover patterns for what makes a drama the best. 
