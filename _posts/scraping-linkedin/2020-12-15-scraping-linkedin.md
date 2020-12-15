---
layout: post
title: Scraping 6000 Linkin-job postings using linkedin-jobs-scraper 
date: 2020-12-15 05:06 +0700
---
Lately, I've been job hunting but I've having a tough time for a few reasons. For one, while there is a massive demand for cloud skills, the market is scare for novice level entry level jobs. It's so bad that I only managed to apply for only 2 jobs in my location. Secondly, I hate the emotional roller-coaster involved in scanning job postings. Picture this: You find the perfect job ad only to realize that that the final paragraph states they want want somone X amount of years of experience. Discouraging, right?  And mind you, this process ends up happening way more often than the happy parts. And finally, I'm just a lazy guy. I don't want to spend my time job hunting, I'd rather spend that time working on other projects like this one. 


Thankfully, the kind people on github have already invented the wheel for me. I don't have to write the scraper from scratch, I can leverage somone else's work. Now using the scraper, I could scrape thousands of job listings with specific filters built-in into the scraper. 

```py
    Query(
        query='Cloud Engineer',
        options=QueryOptions(
            locations=['Canada',"United-States"],
            optimize=False,
            limit=limit,
            filters=QueryFilters(
                relevance=RelevanceFilters.RECENT,
                time=TimeFilters.MONTH,
                experience=[ExperienceLevelFilters.INTERNSHIP, ExperienceLevelFilters.ASSOCIATE, ExperienceLevelFilters.ENTRY_LEVEL]
            )
        )
    ),
```
Unfortunatly, the built-in filters didn't offer as much granularity as I wanted. I wanted a way to parse for specific keywords like languages,tools,skills, wether the job was remote,etc as well exclude any job advert that contained more than 3 years of experience. And as far as I'm aware, Linked-in advanced search doesn't even offer such functionality. In order to accomplish my goal, I had to learn a very powerful skill: Enter Regex. 

Funny enough, I always tried to avoid regex at all costs. The weird and arcane symbols you see in regex expressions certainly didn't help the learning curve, but I was determined to learn it to solve my problem. It was hard at first, but I slowly realized that there was a language to it. Once you understood the language, regex became easier to digest. Also if you're curious, I used this godsend of a site to learn it. 

 The following examples will contain the regex that I used to parse the job postings. If you don't know Regex, don't fret. I'll do my best to walk you through the  regex expression. 
 
 Let's start with a fairly basic one: 
 
 `r'\b(node(js)?|Typescript|javascript|python|bash)\b`

the `|` is called the [alternator](https://www.regular-expressions.info/alternation.html#:~:text=Alternation%20is%20similar.,of%20several%20possible%20regular%20expressions.&text=That%20is%2C%20it%20tells%20the,right%20of%20the%20vertical%20bar), but you can think of it as an `or` operator like in many programming languages. So the regex will try to match the job posting ad against all the characters in `Typescript or javascript or python or bash`. 
 
 The `node(js)?` is a bit special. The stuff in the parenthesis which is `(js)` is optional. This means that regex can match either `node or nodejs`. Putting it all together we get `node or nodejs or Typescript or javascript or python or bash` 
 
 The `\b` on either end of the regex expression denotes the word boundary. Remember how I said regex will match against all the characters in `Typescript or javascript or python or bash`.? 
 
 This means if you have say, "helloTypescriptworld", the regex will still match as the characters in the test string matched against all the characters in `Typescript`. Some people may consider this unwanted behaviour, and would rather want to match on a word against word basis.  With word bounadaries, the regex starts matching starting at the position of the word boundary. 
 
 
 
 
 
 












