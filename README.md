# EurekAlert! Data Analysis Project 

## Overview of Analysis
 
The EurekAlert! Website states: “These news releases may describe research findings recently published in peer-reviewed journals, timely information related to the business, innovation, and societal aspects of science, and details of grants, awards and honors, books, and scientific meetings.” The top subjects include Agriculture, Archaeology, Atmospheric Science, Biology, Business/Economics, Chemistry, Earth Science, Education, Mathematics/Statistics, Medicine/Health, Policy/Ethics, Social/Behavioral Science, Space/Planetary Science, and Technology. What is the quantity of releases describing each of these topics? 

##### data can be requested from Wayne State University

Questions to answer:
- What are the top 5 topics on EurekAlert! by keyword?
- What is the growth of EurekAlert! journals on the site?
- What are the top 10 journals that publish on EurekAlert!?
- How many articles have and do not have a DOI for the years of 2009-2018?
- How many articles have and do not have a DOI for the year of 2018 only?
- Who are the top 10 publishsers on EurekAlert!?
- Who are the top 10 university publishsers on EurekAlert!?
- Who are the top media personnel by article count?
- What are the top articles by leading cause of death?
- What is the sentiment score by journal entry?

## Results

### *See all queries in SQL Queries*

### Releases by Keyword

The results are as follows: 
Agriculture: 5,448 articles 
Archaeology: 1,391 articles 
Atmospheric Science: 7,824 articles 
Biology: 26,754 articles 
Business/Economics: 4,358 articles 
Chemistry: 10,647 articles 
Earth Science: 3,253 articles 
Education: 2,262 articles 
Mathematics/Statistics: 364 articles 
Medicine/Health: 14,993 articles 
Policy/Ethics: 286 articles 
Social/Behavioral Science: 642 articles 
Space/Planetary Science: 213 articles 
Technology: 891 articles 

The top five topics are Biology, Medicine/Health, Chemistry, Atmospheric Science, and Agriculture.

![image](https://user-images.githubusercontent.com/67409852/152918467-aec09dbe-edbe-499a-8e65-cea52f34864e.png)

### Growth of Articles on EurekAlert!

Data from these queries can then be combined via the “union” function within Python and mapped into a visualization to show the year-to-year growth (or decline) of the number of articles being added to EurekAlert! Articles were added to EurekAlert! from June 2009 to September 2018. However, to ensure there is no data loss, the top graph shows articles added during the entire year during 2009 thru 2018, while the bottom graph shows articles added just during July- September during the years of 2009 thru 2018 for comparison.

![image](https://user-images.githubusercontent.com/67409852/152918533-b667d11d-7d2b-4112-ae97-ef2cd4bd59e4.png)

### Top 10 Journals

The top 10 journals are: Proceedings of the Natural Academy of Sciences (3.216%), Science (2.551%), Nature (2.342%), Nature Communications (2.041%), and PLOS One (2.036%), Scientific Reports (1.08%), JAMA (1.05%), Cell (.72%), New England Journal of Medicine (.71%), and Current Biology (.64%).

![image](https://user-images.githubusercontent.com/67409852/152918571-7e53a2bf-7048-4449-a3bf-f41bdca50325.png)

### Articles by DOI (2009-2018)

This query will show which articles have no DOI. This query yielded a result of 186,907 results. Thus, 186,907 of articles have no DOI out of 227,603 articles. Therefore, 40,696 articles have a DOI. Converting this information into statistics, ~18%, or around 1/6 entries have a DOI, and ~82%, or 5/6 of entries do not have a DOI.

![image](https://user-images.githubusercontent.com/67409852/152918602-b1d54655-31af-4e0c-b237-cff0f999099e.png)

### Articles by DOI (2018 only)

This yields the result of 12,042 that do have a DOI in 2018. The data shows that in the beginning, EurekAlert! articles had no DOIs, but as more articles were added, more articles with DOIs were included on the site. In 2018, 51% of articles had no DOI, while 49% did.

![image](https://user-images.githubusercontent.com/67409852/152918680-f821c889-e3f7-4902-b2b1-0a8bb00455e9.png)

### Top 10 Publishers

The top ten publishers on EurekAlert! are: NASA/ Goodard Space Flight Center (2.08%), The JAMA Network Journals (1.41%), Wiley (1.31%), PLOS (1.28%), American Chemical Society (1.19%), BMJ (.86%), Cell Press (.79%), NULL (.75%), University of California- San Diego (.70%), Penn State (.67%). 
 
Since NULL means .75% of articles have no publisher listed, and is not a publisher name, we can note this information, but increase our query to the top eleven publishers in order to find out the top ten publishers. After increasing LIMIT 10 to LIMIT 11, we find that MIT is the tenth most featured publisher at .64%.

![image](https://user-images.githubusercontent.com/67409852/152918711-0058a3f7-4acc-4cca-aefe-712515843eb1.png)

### Top 10 University Publishers

By using ‘%university%’, we are finding the top ten publishers that have university in their name, not just schools with names that begin with “university”. This ensures we are uncovering the correct publishers. From this query, we find that the top ten publishers are: University of California- San Diego (1.66%), University of Pennsylvania School of Medicine (1.31%), Rice University (1.23%), Michigan State University (1.07%), Northwestern University (1.03%), University of Missouri- Columbia (1.02%), University of Illinois at Urbana- Champaign (.97%), University of Washington (.96%), Brown University (.93%), and Duke University (.89%).

![image](https://user-images.githubusercontent.com/67409852/152918747-fbc2bc04-22f9-4c46-be5d-cd0d1f28032f.png)

### Media Personnel by Article Count

As we can see from the snippet of the results of the query, the data is very messy, with many fields in one column (media_contact), and two entries for Rob Gutro. Both rows, row 1 and row 9 must be combined in both columns. This leaves us with 19 entries now, so we can expand the limit on our query to “21”. The column “media_contact” should be divided into columns “Name”, “Email”, “Phone”, “Twitter”, and “Website.” This can be done via Python or OpenRefine. After our data is cleaned, we can see that Rob Gutro is the top media contact personnel per articles associated with them. Contact information for all personnel is now separated into different columns.

![image](https://user-images.githubusercontent.com/67409852/152918784-042944bc-9ae7-42c4-95d9-231d38b28c87.png)

### Full Text Entries (jargon analysis)

This will combine the two queries together. Next, using either OpenRefine or Python, we can change each entry to “Influenza/Pneumonia” so they show up correctly in our visualization. After our visualization is complete, we can see that the most full_text snippets pulled from EurekAlert! articles are on the topics of Cancer, Heart Disease, Diabetes, and Stroke.

![image](https://user-images.githubusercontent.com/67409852/152918820-594d7d6f-c255-411d-b2fa-15184f3dbeda.png)

### Sentiment Score for Journal Entries (sentiment analysis)

#### *See Python code*

From here, we will receive a score is the sentiment is positive or negative, followed by a numeric score. We can then build a simple spreadsheet of these values and create a scatterplot via Microsoft Excel or R. 

Fig. 10 shows the distribution of the sentiment scores for the 100 random entries that were used. We can see that the distribution skews very far to the negative side, with the most common score being “negative .5%”. This is not difficult to comprehend due to the fact that many of the most popular journals on EurekAlert! are scientific and medical. When speaking about illnesses, climate change, and human biology, the topic will most likely deal with issues facing both human beings and animals, which will contain serious, and sometimes “dark" terminology.

![image](https://user-images.githubusercontent.com/67409852/152918864-9ef6bb62-146e-410e-8f8f-d68d2bd69307.png)

## Summary

EurekAlert! is an editorially independent, non-profit news release distribution service launched in 1996. This project was conducted to uncover what kind of content is on the site, who contributes to it, the growth of the amount of content on the site, and the sentiment of that content. The amount of content on the site grew significantly from 2009-18 and continues to grow, along with greater usage of DOIs, which increases record-keeping capabilities, and covering a greater range of topics that are important to scientific discourse.  
