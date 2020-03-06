
Version:1.0 StartHTML:000000174 EndHTML:000123635 StartFragment:000000431 EndFragment:000123603 StartSelection:000000431 EndSelection:000123603 SourceURL:about:blank

## Table of Contents

### 1. Introduction

### 1.1 Overview ...............................................................................................................?

### 1.2 Glossary ..................................................................................................................?

### 2. System Architecture

### 2.1 Overall System Architecture ........................................................................................?

### 2.2 3rd Party / Reused Architecture ..................................................................................?

### 3. High-Level Design

### 3.1 Object / Class Diagrams ..............................................................................................?

### 3.2 Context Diagram ........................................................................................................?

### 3.3 Sequence Diagram ..............................................................................................?

### 3.4 Data Flow Diagram ........................................................................................................?

### 3.5 Logical Data Structure .................................................................................................?

### 4. Problems and Resolutions

### 4.1 Sentiment Analysis Issues and Solutions ....................................................................?

### 4.2 Application Issues and Solutions ...............................................................................?

### 4.3 Firebase Issues and Solutions .....................................................................................?

### 5. Installation Guide

### 5.1 Required Software, Hardware, Versions, Components ..........................................?

### 5.2 Step by Step Instructions .........................................................................................?

### 6 Testing

### 6.1 Unit Testing ............................................................................................................?

### 6.2 User Testing ............................................................................................................?

### 6.3 Evaluation of Testing...................................................................................................?

# 1. Introduction

### 1.1 Overview

The name of the product developed is the “Brand Analyzer App”. The goal of this application is to allow any user to input a popular brand name or business to acquire information about them. After a brand name is submitted, the app fetches a large set of posts and comments from Reddit and performs sentiment analysis on the corpus of text. A collection of data from this analysis is gathered and returned to the user. The user can see what is being said about the brand, whether the opinions and reputation of the brand is negative or positive and the most common as well as the most positive / negative things being said about the brand. As well as that, the user will have access to the percentages between how many of the opinions are positive or negative, how much more one sentiment is prevalent compared to the other and the accuracy of the data they have received. (the user can change the time frame from which the data is acquired to see the history etc timeframe meme if applicable here). The user can also see what the popular news articles say about the brand and how it affects the brand’s reputation. As stated previously, all of the above helps the user to quickly and easily see the online reputation of a brand or business at the press of a button.

### 1.2 Glossary

  

- **Sentiment Analysis** - A system of natural language processing to identify, obtain, assess, and study information from a text.

- **Virtual Environment** - A virtual machine instance, essentially an emulation of a computer system, that is running on a computer.

- **Application Program Interface** - A set of functions and methods that allows the creation of programs or applications.

- **User Interface** - The visual way in which a user and a machine system interact.

  

# 2. System Architecture

### 2.1 Overall System Architecture

The application and complete frontend of the project was fully developed using Flutter. The user interface, the functionality and the testing of the application was all handled using this toolkit. Flutter uses the Dart programming language which is similar in style and structure to Java or Javascript. Within the toolkit are Widgets which help with user interface design and composition. This allows for easy creation, modification and evaluation of each element of interaction within a user interface. Flutter runs in the Dart virtual machine which has its own run-time compiling and execution as well.

  

The structure of the user interface was designed to be as clear and simple as possible. When the user enters the app for the first time, they enter the home page of the app. They will see a search bar asking them to input the name of a brand, as well as a navigation bar that has the terms 'News' and 'Search up at the top of the app. If they tap into the news section of the app, they will see news articles of the day about various brands and businesses. When the user inputs a brand into the search bar, they will be taken to the results page of that analysis. If the user would like to return to the search bar or news tab, the navigation bar will have all 3 sections available so the user can either tap or slide their finger across the screen to access them. After they have inputted the brand, they will have the different categories that the results and data have been split up into. There is a category that displays a chart showing the ratio of how positive or negative the online sentiment on the brand is. The other 3 categories display other results that were acquired, with their own category names, that the user can tap into for more information. That is the complete architecture of the frontend application that the user interacts with.

  

The architecture of the backend involves many functions and modules interacting with each other. When the user inputs the brand name, a function within Flutter sends a get request to Firebase Cloud Functions, which serves as the backend for the project. Firebase Cloud Functions automatically runs the backend code for our project using Googles' servers when one of the functions is triggered. It allows for the frontend to run smoothly and quickly, while communicating with the backend. In this case, the get request sent by the input of a brand name causes the HTTP trigger event for a Firebase Cloud Function . This Firebase Cloud Function fetches the Reddit posts and comments that are about that brand. The way the function acquires this large set of text is by utlising a wrapper known as Snoowrapper on the Reddit API. The wrapper has methods that fetch the data, comments and posts without directly dealing with the endpoints of the Reddit API. When this corpus of text is acquired, the sentiment analysis is performed on this corpus of text. The Javascript module used to perform this analysis is known as Sentiment. The sentiment analysis system goes through every element of the array, each element being a string of other a post or comment, and acquires the sentiment of the whole corpus. After the corpus is analyzed and all the data is retrieved by the sentiment analysis system, the results are returned by the function and sent back to the user. This is how the backend of the app is structured.

### 2.2 3rd Party / Reused Architecture

For the sake of consistency, we reused the architecture of the validate function that can be found within the Sentiment module. The validate function test the accuracy of the sentiment analysis that was performed by the system. Reusing it helped us ensure that our results that we were returning to the user was as accurate as possible.

# 3. High-Level Design

### 3.1 Object / Class Diagrams

![](https://lh5.googleusercontent.com/giilEglnVFUGExtDUKaEkWuCw2dvalPS2AP1qx8tdZ7NMKzoM-n7k-9eWghpQ3WpwzJyXcyGeXS1bh0O-yrUptliI6iUZYT295iCF7tvEFrx1JLFCHA5R1pNYUzvr6w7cCJevxw3)

### 3.2 Context Diagram

![](https://lh5.googleusercontent.com/58UfZ9t7bWst6thb5gnrQ_cdN9x2djRKGxKVKT-n3tL0B0k1PbMRT1xSLsS_Mo0Izc_hf-bKZ6O3u9reYrVWklE94BSrTKJ5WVvro0qRWS2MsXZrYD_dLuOMrRJP3Xm3UWexz_UY)

  

### 3.3 Sequence Diagram

![](https://lh4.googleusercontent.com/DusqeVSvnzuiFavbsAvUsPEjNTcrZFy5yFTkpzMjKQHq3XKh6b93jzKRdlLK9Vj2d5C8_p_QAzDHztBFVhFOezi-roIty9kx0ZmVyhtrMJR0vo6g_jI3S8FcgPAKUDIL8TuCJI03)

### 3.4 Data Flow Diagram

![](https://lh5.googleusercontent.com/tNCYAH-HQ-Qsp7k7a_g3EICfGvFPCYNFQs0W-RZgvfcK5-mbbmsOXwSvvPCxVOQmM1rCnyjUTwgOLA7igUhIwKF5vXpEB5jKunqpX9NZloSDhwVrBrNn2IqfG3Ho7DXOVY0NN9xq)

### 3.5 Logical Data Structure

Our Logical Data Structure from the Functional Specification assisted us in visualising how the data would flow throughout the whole system as we were developing it. Fortunately, even though we made changes to the system during development, we did not have to change how the data flowed through the system. The Logical Data Structure below demonstrates how data flows through the design of the system as demonstrated. The User still inputs the Brand name, the Application analyses the brand and the Results are outputted, being viewed by the User.

![](https://lh6.googleusercontent.com/DL9hPllT2JT5u4bkg9mX3-pn5w2huNBPF8sz5QkTNDU1i9LjFhMMP_RIuczAFvOe6fw-KBmcNDZvBp84sqY2_MXGFJzIdwsdAN0sw2C0cOxJjKW1i-64h1xdZP3HkfZK2Arm_JX7)

# 4. Problems and Resolution

### 4.1 Sentiment Analysis Issues and Solutions

With the AFINN-based sentiment analysis system, there were many complex challenges that had to be faced simultaneously. Below are the many issues that needed to be resolved:

- negation, sarcasm

- profanity

- opinion strength accuracy

- abbreviations, poor spelling

  

The first problem that needed to be dealt with was negation and sarcasm. When a sentence is just read from text, it can be difficult to detect sarcasm or dry humour within a sentence. A sentence like, "I really like the way the app stores my data." can have very negative connotations when the tone of the speaker is sarcastic. Tone is something that a machine can find very difficult to understand effectively. In order to have a method of dealing with this, we had to be able to detect the overall sentiment of the posts and comments. This would allow us to see whether the general emotion of the text where the sarcastic sentence originates from is either positive or negative. If the overall sentiment of the piece is negative, then the sentiment module reads that comment as sarcastic. If the overall sentiment of the text is positive, the comment is not seen as sarcastic. As for negation, we had a file that contained all the words that cause negations to a sentiment. Then, when the system is analyzing the sentiment of the word, if a negation is in front of it the sentiment score (regardless if it is positive or negative) has its sign inverted. So if it was a minus two, it became a plus two and vice versa.

  

Profanity was a major issue for us to deal with since it was a topic we felt very strongly about. On one hand, the profanity of a piece can contribute both positively or negatively to the sentiment of a text. So it was important from a statistical standpoint to collect and analyze the profane words that a text may have. This would allow our system to be as accurate as possible. However, we did not want to constantly expose ourselves and our possible users to the large amount of profane and potentially hurtful language that can be found in a project similar to this. The key to solving this problem was utilising the global environment configurations that are available to every Firebase project. We stored all of the profanity as one long string of profane words connected by periods so that we could split the one long string into a list of words using "split(".")". This allows us to just import the list of profane words as a variable into the program without anyone the developers or users seeing them. However, we were unable to filter out all of the possible incorrectly spelled combinations of every profane word. As well as that, within the timeframe of the project we weren't able to develop a way to remove a phrase or sentence with inappropriate innuendos. The solution we have provided is the best one we could create reasonably within the timeframe. During the analysis of the text, the profane words are taken into account for the calculation but are not stored in the statistics that the user will see. We wanted to have a professional and academic approach to solving this issue and the profanity filter we implemented allowed us to achieve that.

  

Opinion strength accuracy is very vital to the analysis of a piece's sentiment. Of course, being able to analyze the sentiment of a text is significant but having the ability to test its weight and accuracy are just as important. Some sentences are more positive than other positive sentences, and the same goes for negative sentences. The system should be able to notice this distinction. Fortunately, the sentiment module we have utilises the AFINN 165 academic lexicon, a data set of over 3000 words with each word having a number from -5 to 5 indicating how positive or negative that word is. This allows our system to see which opinions are more positive or negative than other similar opinions. We also must prove that information we gather is accurate. The sentiment modules provide a function called "validate" which takes in a data set and then iterates through and analyzes each element's sentiment. After this, the accuracy of each elements' sentiment is calculated by testing the class and comparative score of the element and whether it passes or fails, a respective counter is incremented. Then the overall accuracy of the piece is calculated and returned by the function. Since the validate function operates quickly, it allows for quick and precise measurements of the accuracy of a data set the app acquires.

  

Abbreviations and poor spelling can be nightmares to deal with. The almost infinite amount of spelling mistakes alone can make navigating the sentiment of a piece very difficult. We decided not to take spelling mistakes into account and we simply leave any incorrectly spelled words as neutral and give them a sentiment of zero. However, the AFINN 165 lexicon does have plenty of abbreviations already stored within its library. Making use of that, we were able to get the sentiment of words like "lol" and "ftw". This allowed our results to be much more accurate than otherwise possible.

### 4.2 Application Issues and Solutions

Initially, the application did not seem to verify via Firebase upon installation. It was run on Google Chrome and therefore Firebase did not recognise this. The solution was to first set up a Virtual Device Simulator using AVD Tools in Android Studio. However the system required to configure Virtualisation set to true in BIOS settings as it had been disabled. Once this was complete, a simple instance of the application was run and Firebase could finally verify the application.

  

Due to the nature of the analysis Firebase function and intensity of data it has to process, it may take a while to render on the application. Due to the asynchronous functionalities that exist in Flutter, it is possible to wait until the HTTP request is complete and sends a response. However the more data that has to be analysed then the application can’t handle and on multiple occasions doesn’t deliver a response. When this happens an error message is sent back to the user.

  

When the application makes a call to the http function that originates from firebase, it waits for a response. Once it receives a message then a page routing function is invoked. Initially the application did not “wait” for a response. It invoked the routing as it was still receiving a message. Therefore the application crashed as it tried to open a new page with the route details but they were not complete. This was fixed by using “await” until the HTTP function had finished calling. This means that the compiler doesn’t continue reading the next line of code until the function stops executing. They are generally used for data fetched from the internet.

### 4.3 Firebase Issues and Solutions

When utilising Firebase and its many available services, there were many steep challenges that needed to be overcome. Below are the many issues that needed to be resolved:

- function calls and functions triggers, testing

- payment plan changes

  

A key part of using Firebase Cloud Functions involves using specific triggers or calls that execute the code when a certain condition is made. There are many events that a developer can set for their function. Some examples include when you make a HTTP get request (which causes what is known as a HTTP trigger) or when a file is saved onto their Firebase Storage service (a Cloud Storage trigger). However, performing the testing for whether this event is triggered is difficult. There is a vital lack of a virtual testing environment where the function can be run as if the trigger condition has been met. Testing is absolutely critical to any system being developed. The function must be time consumingly deployed and no information is given as to whether the function operates at that point either. To test the function, the trigger must be manually performed and depending on the trigger that can be costly in time as well. To see the results, you must enter a different tab and check the logs. This process of painstakingly deploying, triggering the event and checking the logs was a major time consuming issue that we needed to overcome. We utilized a Javascript Testing Framework called Mocha that allowed us to quickly run tests of the Firebase-less versions of the code we were developing instead. This saved us a lot of time as we were constantly testing our code in AGILE way. We would test the app, get feedback from users on our app, make more changes, test those iterative changes and get more user feedback in that constant loop. Streamlining and making it easier to perform the testing assisted us immensely for the AGILE approach we took for this app.

  

When it comes to Firebase, there are different prices and limits depending on what payment plan is chosen. The Spark plan is the free option but it is very limiting in terms of what you can do. For example, you cannot utilise multiple databases for one project, you cannot utilise multiple buckets for storage for one project and the caps set for memory usage and function calls are far too small, even just for a project similar to this one. We found ourselves at the limit of the Spark plan about halfway through the project. This stopped us from continuing working on the project completely. To solve this problem, we were forced to upgrade to the Blaze plan. In order to actually use Firebase for the whole duration of our project, we needed to upgrade to the Blaze plan. This plan operates on a pay as you go system, with less restrictions and bigger caps for service users. The issue was if a user went past these caps, they would have to pay a fee so we had to make sure those limits were never reached in order for the Blaze plan to stay free. Fortunately there is a dashboard where you can view how close you are to the limit so we were able to monitor our usage and progress closely.

  

# 5. Installation Guide

### 5.1 Required Software, Hardware, Versions, Components

- Android Version 4.1 Jelly Bean (API 16) or later

- Android Virtual Machines Version 4.4 (API 19) or later

No additional hardware or software required.

### 5.2 Step by Step Instructions

In order to install the Brand Analyzer App, you can install it by clicking the link in the installApp.md within the technical_specfication repository found on the project's GitLab. As well as that, you can find the link to install the app on either of the project member's blogs. After clicking the link, your Android phone will download the application onto your device. Make sure your Android is fully up to date as issues may occur when using a device that is not fully updated with its latest version available. You will need an internet connection to access the links, to download the application and to use it as well. The application requires an internet connection as it needs to retrieve online posts and comments from the Reddit website.

# 6 Testing

### 6.1 Unit Testing

Unit Testing requires all possible components of a system to be tested to make sure they work as intended. 20 unit tests for the Sentiment Analysis system were developed. As features were added to the system, each component had to be tested before it could be added. This was to save as much time as we could and to reduce errors and bug fixing. Each unit test result is displayed in the image below:

![](https://lh3.googleusercontent.com/dK8w_E8h0GRuBqkwkc9rCU6khB3i6Vck7HrjJ87XwYqi41xKSJD856QrFPnK9nPzJG4OdLzbCg8JCJr4g-r6ItpWEJXidXTfLjWjroio7P1Hx-npnrGCkMYAKDrNqNQuZCEMxlmM)

- The first test examined whether the sentiment module score correctly analysed that the overall sentiment of the comments were positive.

- The second test inspected whether the system could accurately acquire all the positive words in the comments.

- The third test investigated whether the sentiment analysis function could acquire the correct number of positive words in the comments. Boundary testing is vital to see what the upper and bottom limits of a calculation could be.

- The fourth test and the fifth test respectively assessed whether the system could precisely record the most recurring word that appeared in all of the comments and how many times it appeared in the comments.

- The sixth test analysed whether the system could acquire the second most common term that appeared in the document. This provided the foundation for how to acquire all of the occurences of each word that occured in the comments.

- The seventh test tested whether all of the most positive words in the document could be gathered into a list.

- The next eight tests all had to examine whether the validate function correctly acquired the accuracy of the results that the Sentiment Analysis system had got. For most of the tests, they all had a unique data set to test the Sentiment Analysis system. Most data sets did not have a proper class assigned to every sentence within the set. The class would tell the system whether a comment was positive with a 1 or negative with a 0. When each file was assigned the proper class to the comment, all of the accuracy results were 100%. There was no doubt that when the system knows which comment is positive or negative beforehand, the accuracy of the results is guaranteed. We performed the unit tests both with and without the classes. This allowed us to see which data sets were more accurate than others. Also, we found a trend that data sets which had text similar to informal social media language were usually more accurate than say for example: movie reviews or IMDB reviews.

- The ninth and tenth test respectively asserted whether all of the negative sentences were found within a comment and whether the correct amount of them were acquired.

- The eleventh test involved putting all of the variables the system we had been using beforehand into one JSON object named results. This transition and change in the system was to help with the integration of the app and to also improve the readability and comprehensiveness of the code.

- The twelfth test inspected whether the sentiment analysis system could correctly pick out the most negative sentence within the text, regardless of the overall sentiment.

- The thirteenth test investigated whether the regular express correctly removed all of the punctuation from both the left and right hand side of a comment. We had to make sure we were not removing any punctuation from the middle of the comment since comments can have multiple sentences and removing the punctuation from within a comment could change the meaning or remove the meaning from the comment.

### User Testing

The following are the observation notes made by the project members as well as the answers to the questionnaire that the 4 anonymous participants gave. The observers did not speak or interact with the participant as they used the application. Answers from the participants who filled out the questionnaire in the link below:

  

https://docs.google.com/forms/d/1KpdIz6NuPFpqEAUnMnXhfozyN-vtHJUW9oUaR0ZlKpQ/edit#responses

**Participant #1:**

As soon as the participant received the phone with the app, they went straight to the news section by tapping the news tab on the navigation bar to see what articles were available to read. They stopped and pointed at one news article about Amazon, and then immediately went to the search tab via the navigation bar and tapped the search bar. After typing into the search bar, they waited impatiently as the results on the brand sentiment analysis was being conducted. After a sigh of relief, they scrolled up and down inspecting every bit of the results page. When they reached the bottom of the page, they scrolled all the way back to the top of the page. They went back to the home page and paused for a bit. They suddenly tapped the search tab of the navigation bar despite already being on the search page already. After a ‘tsk’, they handed back the phone to the observer. After that, they privately filled out the questionnaire.

  

**Key observations**

- The news tab might affect the search results that the participants put in.

- The app might take too long to perform the sentiment analysis for some users.

- This participant most likely wished to go back to the results they acquired after leaving the results page.

- This participant completely did not interact with the timeframe settings. Whether it was on purpose or not is unclear.

  

**Questionnaire Answers**

___

Q1: What brand did you input?

A1: Amazon

___

Q2: Was navigating to and from the different pages and menus easy or hard?

A2: It was easy, but you should be able to see the results at any time you want.

___

Q3: (if participant said harder to Q1): What made it harder for you?

A3: N/A.

___

Q4: Did you like the results that were displayed?

A4: Yes

___

Q5 (to the previous question, regardless of answer): Why did you like / not like them?

A5: I didn’t know that a lot of positive things were being said about Amazon. It surprised me.

___

Q6: Did you like how the results were displayed?

A6: I did. Very clear layout design and good colour choice.

___

Q7: Was the app performance fast or slow for you?

A7: Menus were fine. Getting the search results took too long.

___

Q8: If you could add an additional feature, what would you add?

A8: Being able to go back to the results.

___

**Evaluation #1**

Taking into account this participant’s actions during the user test, as well as their questionnaire answers, it is clear to see that fast performance and an intuitive workflow for them is important. When we implemented the application, we did not take into account people wanting to see the results again after leaving the results. We made the assumption during the development that after thoroughly going through the results the first time around, a user would not want to go back to that page. However, a user may not go thoroughly through it, or may even accidently leave that page and lose their results. Unexpected situations are important to take into account during the development of any website or app. On the other hand, upon further reflection, the overall performance of the app may slow down if it must cache the results too. To strike a balance between fast performance and a good user workflow is vital.

___

**Participant #2**

After sitting down, the participant picked up the phone and saw the search bar. Without looking at the news tab, they entered “Adidas” into the search bar and began analysing the online sentiment of the brand immediately. After a surprisingly short amount of time, the user saw the results and nodded their head. They seemed to look at the pie chart and the amount of posts analysed before scrolling down to the bottom immediately. After viewing the rest of the results, they returned back to the search page and typed “Nike” into the search bar. After waiting for a bit longer, the participant finally saw the results and immediately gave a surprised look. They scratched their head and scrolled down to see the rest of the results as well. Finally, they left the results page, put down the phone and privately filled the questionnaire out.

  

**Key observations**

- The app performs its goal quicker when the user does not inspect the news section of the app.

- The app can be used to analyse multiple brands at once, but slows down with each search made.

- Comparing brands with each other can bring a lot of interest and intrigue to a user of the app.

- The workflow of comparing brands with each other is poor. Involves too many steps if users do not want to go back to the home page.

- The app does not store multiple search results and multiple sentiment analyses.

  

**Questionnaire Answers**

___

Q1: What brand did you input?

A1: Nike and Adidas

___

Q2: Was navigating to and from the different pages and menus easy or hard?

A2: Very easy

___

Q3: (if participant said harder to Q1): What made it harder for you?

A3: N/A.

___

Q4: Did you like the results that were displayed?

A4: No

___

Q5 (to the previous question, regardless of answer): Why did you like / not like them?

A5: Cannot believe people think Nike is just as good as Adidas. Adidas is better.

___

Q6: Did you like how the results were displayed?

A6: It was okay but pretty simple. Gets the job done, would have liked to see a dark mode.

___

Q7: Was the app performance fast or slow for you?

A7: Second search was slower than the first, but overall grand.

___

Q8: If you could add an additional feature, what would you add?

A8: A dark mode.

___

  

**Evaluation #2**

We were aware of the slow run time the application may have while running multiple sentiment analyses. We did not anticipate that people would want to compare one brand with a lot of other brands. If someone was to try and compare every single clothing brand with each other, it would take a long time. As well as that, storing the result for every single one would take up a lot of application and phone resources. The user would need to remember every result if they wanted to compare for example: 5 brands amongst each other. That would be unfeasible solely utlising the app. Also, the topic of colour came up. Having a more colour blind friendly mode or dark mode for users would be beneficial to the app.

___

**Participant #3**

When the user sat down and was comfortable, they slowly picked up the phone with the app. They were investigating every aspect on the home page which had the search bar, navigation bar and timeframe settings on it. After that inspection, they tapped into the news section. The participant then went through every news article available, tapping on each one possible. Dissatisfied that there was no in doubt news, they went into the search page by tapping the navigation bar. They typed Facebook into the search bar, then selected the “Last 30 Days” option of the timeframe setting and then pressed the search icon at the end of the search bar. Some time passes and then participants attempt to stop the search by pressing the back button. After a long while, the participant sees their results. They were visibly confused and thoroughly inspected every word they saw on the screen like they did when they first picked up the app. They slowly scrolled up and down, reading every new bit of data they had received. After that, they put the phone down and privately filled out the questionnaire in a different room.

  

**Key observations**

- A lot of the participant’s time can be taken up by the news feature, which is not the main aspect of the app.

- If the participant tries to stop the search and sentiment analysis while the app is performing both of them, strange issues can occur.

- The app slows down when inputting too many commands at once into the app.

- The user can spend a lot of time looking at the results they receive, but may not want to do anything else after the search is performed.

  

**Questionnaire Answers**

___

Q1: What brand did you input?

A1: Facebook

___

Q2: Was navigating to and from the different pages and menus easy or hard?

A2: It was fine. There was a lot of content on the app.

___

Q3: (if participant said harder to Q1): What made it harder for you?

A3: N/A.

___

Q4: Did you like the results that were displayed?

A4: Not really

___

Q5 (to the previous question, regardless of answer): Why did you like / not like them?

A5: I use Facebook a lot and really enjoy it. I did not like seeing the negativity.

___

Q6: Did you like how the results were displayed?

A6: It was simple. A bit boring.

___

Q7: Was the app performance fast or slow for you?

A7: It did feel a little bit slow and awkward at times.

___

Q8: If you could add an additional feature, what would you add?

A8: A way to make the words on screen bigger.

___

  

**Evaluation #3**

At this point, we have realised that the application may not be as accessible to all users as it should be. Accessibility is vital for any website or application. If there is a lot to do, the user may get easily distracted. If the words are too small, the user might feel discomfort while reading the information displayed on screen. If there is a lot of tapping and scrolling to do, someone with movement issues may find it difficult to navigate all of the app in one sitting. These are all important factors for developers to take into account when developing a website or an application. We saw those issues pop up in this user test. On the bright side, the participant was seemingly impressed by the amount of content the app can provide.

___

**Participant #4**

When they sat down to begin testing the app, they did not pick up the phone. Leaning over the table, they tapped into the search bar and brought up the keyboard. They typed in the word “nintendo” and then paused. After a bit, they noticed the news tab in the navigation bar and tapped that instead. They scrolled down and read some of the titles of the news articles. They tried tapping into an article about Sony unsuccessfully. Going back into the search page of the application, they tapped into the search bar and stopped for a bit. After raising both eyebrows a little, they typed in the word “sony”. After some time passed, the results were displayed. The participant looked at the first results that appeared on screen, giving a nod. After scrolling and viewing the rest of the results, the user locked the phone and privately filled out the questionnaire.

  

**Key observations**

- Not clear if participants are not noticing the timeframe setting or if the default setting of “7 Days Ago” is what they would like to have chosen by default.

- When a user goes from the news section back to the search section, that will likely influence what brand they put into the search bar first

- If a value is entered into the search bar but the user chooses to go into the news section after typing something into it, it will not save. This may come as a surprise to some users who would expect this feature.

- The things that stand out on screen will be the first things the user will most likely interact with. These first few interactions can have a major impact on the first impression and overall experience with an app.

  

**Questionnaire Answers**

___

Q1: What brand did you input?

A1: Just Sony

___

Q2: Was navigating to and from the different pages and menus easy or hard?

A2: Easy. Would have liked more pages and menus though.

___

Q3: (if participant said harder to Q1): What made it harder for you?

A3: N/A.

___

Q4: Did you like the results that were displayed?

A4: They were fine

___

Q5 (to the previous question, regardless of answer): Why did you like / not like them?

A5: I expected the results that I saw from the brand analysis.

___

Q6: Did you like how the results were displayed?

A6: I like it. But would have liked some more colours or pictures.

___

Q7: Was the app performance fast or slow for you?

A7: It was acceptable. Did not expect a perfect app.

___

Q8: If you could add an additional feature, what would you add?

A8: Have the news articles contain videos in case you do not want to read the news.

___

  

**Evaluation #4**

Each user test brings feedback and answers we never expect, and this one is no exception. We never thought of having a feature to play news article videos since it was just one side aspect of the and we anticipated that it would not be popular or time consuming. As well as that, having more pictures / icons on the app could help with readability and visibility. However, it is also important to not make the application too distracting or visually overwhelming as well. It also seems like people who are already aware of the online sentiment of a brand may not have much use for the goal this application accomplishes thought.

  

### 6.3 Evaluation of Testing

  

In order to assess and validate how optimal the testing performed was, we must evaluate how the testing was performed. During the user testing, we encountered some issues while silently observing our participants test the app. Even though they were informed that we would just quietly watch them test the app, this actually can affect how they use the app. They may get nervous, attempt to talk to the observer or ask questions, expect certain tasks to be done or perform strange actions to name a few. If it were possible, maybe recording the phone screen and leaving the room while they use the app could be better. That would include its own set of drawbacks like not witnessing the participant's physical reactions or not getting an complete depiction of what the user is attempting to do though.

  

As well as that, the questionnaire that we had participants fill out at the end requires evaluation. Some of the questions we asked gave us answers we did not anticipate or answers that were not succinct or in enough detail. For example: The question “Did you like how the results are displayed?” was too specific. The information only applied to the results page of the app so we got no feedback on the design of every page within the app. A better question would have involved asking if they like how the app in general is designed. Balancing between not having too many time consuming questions on the questionnaire and getting enough details from the answers from the questionnaire can be difficult.

  

We found it very insightful to be able to write down observations as the users tested the application and comparing it to the answers we got from the same users. We allowed the users to fill out the questionnaires privately in a different room without any observation or interference. We felt this was very good since it allowed the participants to be more honest when filling out the form. Seeing how they physically interacted with the app and comparing it to the questions they mentally answered gave us insight into how we may perceive an experience in a certain way, and then how that experience can form in your mind when asked questions and reflected upon.

  

Overall, we felt like the user testing of our app was very successful. We learned a lot of information and acquired a lot of very useful feedback. We will take this into account while we continue to develop the app.
