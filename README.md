## Links
Devpost: https://devpost.com/software/pronto-zt2niq

Video Demo: https://www.youtube.com/watch?v=LU5fVp96I6s

## Inspiration

The open spread of information through the news and media is essential to maintaining an informed society. We constantly depend on the media to fill us in on every large and impactful event taking place worldwide. As the world was forced into lockdown by the pandemic, we increasingly relied on electronic media as data and news spread faster than ever before. This vast amount of information has made it difficult to decipher which events are the most important. Not only did this leave millions feeling overwhelmed, but allowed for the spread of misinformation without scrutiny or regulation, resulting in major societal ramifications. 

As a team, we all suffered through this personally and at times, even knowingly abandoned the effort to remain educated due to the sheer volume of news we are exposed to every day. We wanted a way to cut through the clutter and simply get the most important news, filtered to our interests so that we could streamline the news process and feel confident in trusting what we read. 

## What it does

Pronto is a chrome extension designed to allow users to easily access the most popular, recent news, customized by their interests in our cluttered Information Age. 

We provide the Top 5 current news stories which regularly update every 3 hours. The visible stories can be filtered by 6 categories: business, entertainment, health, science, sports, and technology which the user can select or deselect using settings based on their preferences. These Top 5 articles are displayed on our chrome extension’s homepage and for each article, we provide the title, publishing news network, and a link to the full article. In addition, when an article’s title is clicked, the user can access a machine learning generated summary of the article, an approximation of how long it will take to read, and a sentiment score based on how positive or negative the author is towards the subject. Once an article is selected, the user can easily navigate around to the next article in the list or return to the homepage.

With the global pandemic and information rapidly available everywhere, Pronto aims to simplify its users’ lives by centralizing the news in one convenient location where many already spend part of their day: their web browser. With Pronto, users are one click away from accessing the most important news; even faster than typing in a website URL!

## How we built it

Using the Microsoft Visual Studio Code, we developed HTML, CSS, and Javascript code to serve as our front end user interface for the Pronto extension. JavaScript is the core of this interface as it controls the functionality of the buttons, filter selection, and color implementation. A settings page was also implemented using the chrome storage API to allow the user to filter their news preferences. Additionally, the JavaScript utilizes HTTP requests to our Google Cloud Functions backend to retrieve information based on the user’s selected categories of news. 

Then, our backend makes use of multiple APIs and our custom filtration algorithms to provide our users with content tailored for them. First, using a REST API called News API, we retrieve the corresponding top news articles for any given category in a JSON format. We then run each article through our filtering process which combines machine learning with Levenstein distance through the Fuzzy API to compare articles for similarity. We then eliminate articles with features deemed too similar to ensure the user receives unique articles on different events. Now we can use the remaining JSON of articles to access their titles and URLs, which in turn enables us to extract an article’s content with the boilerpipe web scraper library. Using this content, we were able to pull the most important sentences to generate a text summary for each article using DeepAI’s machine learning and algorithmically generate an approximate time estimate for how long the article takes to read. We also leveraged Google Cloud’s natural language processing API to display a sentiment score on each article. 

## Challenges we ran into

Besides the fact that none of us had any real experience with Web Development, the major issue we ran into on the front end was the CORS Policy. This policy restricts the data that is allowed to be sent to and from various sources across the internet. Initially, we ran into an error where the CORS Policy prevented our requests to be sent and received which had to be resolved by properly integrating the server backend with the frontend and adding additional permissions in the manifest json file. Another challenge in the frontend was the fact that the chrome storage API acted asynchronously which caused many bugs of code running out of order. Correctly implementing the asynchronous code was definitely the most time confusing challenge in the front end.

On the backend one of the largest problems we faced was API key management. Because we only had a limited number of calls to each API, we needed to configure our code to retrieve the most information out of each request and avoid repeat calls, which we were able to accomplish by storing chrome data for larger calls. Along with this, many of the news websites which we visited had defenses against web scrapers which made it impossible to analyze the content from certain webpages. This forced us to use a variety of different methods to catch HTTPS errors and get usable content from difficult websites. Even when web pages were accessed successfully there were oftentimes problems with the content within the webpages which prevented summaries and sentiment from being accessed. Because of this, we had to develop checks to ensure that the returned content was valid before passing it to the frontend. This brought unique challenges as invalid content took many forms which needed to be addressed.

## Accomplishments that we're proud of

Starting this project, none of us had any formal web development experience. Neither had any of us ever used a cloud platform. We had never used APIs before and didn’t understand how internet protocol or http communication worked. Nonetheless, in less than a week, we pulled it together as a team to make a fantastic chrome extension, gaining valuable hands-on design experience. As we repeatedly googled-searched our way through each step, we took inspiration from our favorite UI designs, and creatively combined sets of features to produce a clean interface and an intuitive user experience. Furthermore, setting up the google cloud server with its sheer volume of options and products was still a daunting task. Through relentless searching of Google’s well-documented guides, we were soon able to determine optimal tools to add our backend endpoints and provide a smooth experience and connection between the chrome extension and cloud. Ultimately, we were able to successfully use the vast resources available on the internet to efficiently determine and create our functionality.

## What we learned

We learned how to integrate backend functions seamlessly into a working, efficient frontend that also provided a user interface. Our frontend team learned to use the syntax of HTML/CSS and also gained the skills necessary to create an uncluttered and intuitive user interface. The backend team had to work with python, a language we were fortunate enough to be familiar with, to create functions. Using JSON objects effectively was something we had to learn since we were inexperienced with API calls. Both teams had to learn how to work with google’s cloud server and set up an HTTP call that would allow us to relay all necessary information between the frontend and backend.

## What's next for Pronto

We have multiple other features for both the frontend and backend in the pipeline. On the frontend, we want users to be able to customize aspects of their user interface experience including thematic colors, fonts, or backgrounds. In addition, we currently are unable to access the content of certain news articles due to restrictions by the publisher. We would love to add support for these select web pages which would ensure the user can always have a summary and estimated read time. Meanwhile, on the backend cloud server, we also want to add a fact checking functionality that can provide a reliability score for each article. Another useful feature we are considering would be allowing the user to request the webpage analysis on the article that the user is currently on.


## Pronto Extension Download Guide
https://docs.google.com/document/d/1g3IXMd4WqHZNs_7wJFouVyKb7Ou7Hn2LBj5vP3q0F60/edit?usp=sharing
