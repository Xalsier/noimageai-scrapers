# noimageai-scrapers
This is just a compilation of different methods to block webscrapers that take art from websites to use in their models. 

If more options become available, I might make this a github page just because scrolling through a README might be a chore.

## 1. Html head <meta>

```<meta name="robots" content="noimageai">```<br>
```<meta name="robots" content="noai">```

No known ai scrapers at this time follow this directive. The [DeviantArt Team](https://www.deviantart.com/team/journal/UPDATE-All-Deviations-Are-Opted-Out-of-AI-Datasets-934500371) introduced it in November 11, 2022 after community backlash for using art on the website for ai training. 

```<meta name="robots" content="noai, noimageai">```

This is a modification of the above directive, suggested by [Neil Clarke](https://neil-clarke.com/block-the-bots-that-feed-ai-models-by-scraping-your-website/) on August 23, 2023.

## 2. Disallow All Robots, robots.txt

This will block all robots, which might conflict with necessary website crawlers used for indexing sitemaps or analytics.

```
User-agent: *
Disallow: /
```

## 3. Disallow Some Crawlers, robots.txt

A more extensive one will be available on this repository (At some point). For now, this will include 3 crawlers that are known for webdata into it's datasets. CCBot comes from a Non-Profit Organization called Common Crawl according to [searchenginejournal](https://www.searchenginejournal.com/how-to-block-chatgpt-from-using-your-website-content/478384/) and it is possible some images from your website are already in it's historical datasets. GPTBot is used by OpenAI to crawl the internet to improve it's systems. In the same article by Neil Clarke, Imagesiftbot was mentioned as in correlation with The Hive, a company that produces image generation models which might pose some cause for concern.

```
User-agent: CCBot
Disallow: /

User-agent: GPTBot
Disallow: /

User-agent: ImagesiftBot
Disallow: /
```

## 4. Blocking IP Addresses using .htaccess

This will be useful on apache web servers. Using IP Addresses is a more granular way to block web scrapers, although it's not entirely effective against VPNS. This method is best I'd imagine if the IP addresses are static for the bot being used to scrape.

```
Order Allow,Deny
Allow from all
# Block GPTBot IP ranges
Deny from 20.15.240.64/28
Deny from 20.15.240.80/28
Deny from 20.15.240.96/28
Deny from 20.15.240.176/28
Deny from 20.15.241.0/28
Deny from 20.15.242.128/28
Deny from 20.15.242.144/28
Deny from 20.15.242.192/28
Deny from 40.83.2.64/28
```

## 5. Blocking Known VPN IP Addresses

This is a nuclear option, and it will make it more difficult for users using VPNs to access the website- but it also will prevent webscraper bots using VPNs from accessing the website. 

```
No example list available for IP addresses
```



