# 0. Table of contents
A table of contents with pages numbers indicated for all sections / headings should be
included.
# 1. Introduction
**1.1 Overview**
Provides a brief (half page) overview of the system / product that was developed. Include a
description of how it works with other systems (if appropriate).
**1.2 Glossary** 
Define and technical terms used in this document.  _Only include those with which the reader may not be familiar._
# 2. System Architecture
This section describes the high-level overview of the system architecture showing the
distribution functions across (potential) system modules. Architectural components that are
reused or 3rd party should be highlighted. Unlike the architecture in the Functional
Specification - this description must reflect the design components of the system as it is
demonstrated.
# 3. High-Level Design
This section should set out the high-level design of the system. It should include system
models showing the relationship between system components and the systems and its
environment. These might be object-models, DFD, etc. Unlike the design in the Functional
Specification - this description must reflect the design of the system as it is demonstrated.
# 4. Problems and Resolution
This section should include a description of any major problems encountered during the
design and implementation of the system and the actions that were taken to resolve them.
# 5. Installation Guide
This is a 1 to 2 page section which contains a step by step software installation guide. It
should include a detailed description of the steps necessary to install the software, a list of all required software, components, versions, hardware, etc.
## Table of Contents
### 1. Introduction
### 1.1 Overview .................................................................................................................?
### 1.2 Glossary ...................................................................................................................?
### 2. System Architecture
### 2.1 Overall System Architecture ...................................................................................?
### 2.2 3rd Party / Reused Architecture ..............................................................................?
### 3. High-Level Design
### 3.1 Object / Class Diagrams ..........................................................................................?
### 3.2 Context Diagram .....................................................................................................?
### 3.3 Data Flow Diagram .................................................................................................?
### 3.4 Logical Data Structure ............................................................................................?
### 4. Problems and Resolutions
### 4.1 Sentiment Analysis Issues and Solutions ................................................................?
### 4.2 Application Issues and Solutions ............................................................................?
### 4.3 Firebase Issues and Solutions ..................................................................................?
### 5. Installation Guide
### 5.1 Required Software, Hardware, Versions, Components ..........................................?
### 5.2 Step by Step Instructions .........................................................................................?
# 1. Introduction
### 1.1 Overview
Provides a brief (half page) overview of the system / product that was developed.
The name of the product developed is the “Brand Analyzer App”. The goal of this application is to allow any user to input a popular brand name or business to acquire information about them. After a brand name is submitted, the app fetches a large set of posts and comments from Reddit and performs sentiment analysis on the corpus of text. A collection of data from this analysis is gathered and returned to the user. The user can see what is being said about the brand, whether the opinions and reputation of the brand is negative or positive and the most common as well as the most positive / negative things being said about the brand. As well as that, the user will have access to the percentages between how many of the opinions are positive or negative, how much more one sentiment is prevalent compared to the other and the accuracy of the data they have received. (the user can change the time frame from which the data is acquired to see the history etc timeframe meme if applicable here). The user can also see what the popular news articles say about the brand and how it affects the brand’s reputation. As stated previously, all of the above helps the user to quickly and easily see the online reputation of a brand or business at the press of a button.
### 1.2 Glossary
Define the  **technical** terms used in this document.  _Only include those with which the reader may not be familiar._
Sentiment Analysis - A system of natural language processing to identify, obtain, assess, and study information from a text. 
Virtual Environment - 
Application Program Interface -
# 2. System Architecture
This section describes the high-level overview of the system architecture showing the
distribution functions across (potential) system modules. Architectural components that are
reused or 3rd party should be highlighted. Unlike the architecture in the Functional
Specification - this description must reflect the design components of the system as it is
demonstrated.
### 2.1 Overall System Architecture
### 2.2 3rd Party / Reused Architecture
# 3. High-Level Design
This section should set out the high-level design of the system. It should include system
models showing the relationship between system components and the systems and its
environment. These might be object-models, DFD, etc. Unlike the design in the Functional
Specification - this description must reflect the design of the system as it is demonstrated.
#### 3.1 Object / Class Diagrams
 
### 3.2 Context Diagram
 
### 3.3 Data Flow Diagram
 
### 3.4 Logical Data Structure
Our Logical Data Structure from the Functional Specification assisted us in visualising how the data would flow throughout the whole system as we were developing it. Fortunately, even though we made changes to the system during development, we did not have to change how the data flowed through the system. The Logical Data Structure below demonstrates how data flows through the design of the system as demonstrated. The User still inputs the Brand name, the Application analyses the brand and the Results are outputted, being viewed by the User.
 
# 4. Problems and Resolution
This section should include a description of any major problems encountered during the design and implementation of the system and the actions that were taken to resolve them.
### 4.1 Sentiment Analysis Issues and Solutions
With the AFINN-based sentiment analysis system, there were many complex challenges that had to be faced simultaneously. Below are the many issues that needed to be resolved:
- negation, sarcasm
- profanity
- opinion strength accuracy
- abbreviations, poor spelling

The first problem that needed to be dealt with was negation and sarcasm. When a sentence is just read from text, it can be difficult to detect sarcasm or dry humour within a sentence. A sentence like, "I really like the way the app stores my data." can have very negative connotations when the tone of the speaker is sarcastic. Tone is something that a machine can find very difficult to understand effectively. In order to have a method of dealing with this, we had to be able to detect the overall sentiment of the posts and comments. This would allow us to see whether the general emotion of the text where the sarcastic sentence originates from is either positive or negative. If the overall sentiment of the piece is negative, then the sentiment module reads that comment as sarcastic. If the overall sentiment of the text is positive, the comment is not seen as sarcastic. As for negation, we had a file that contained all the words that cause negations to a sentiment. Then, when the system is analyzing the sentiment of the word, if a negation is in front of it the sentiment score (regardless if it is positive or negative) has its sign inverted. So if it was a minus two, it became a plus two and vice versa.

Profanity was a major issue for us to deal with since it was a topic we felt very strongly about. On one hand, the profanity of a piece can contribute both positively or negatively to the sentiment of a text. So it was important from a statistical standpoint to collect and analyze the profane words that a text may have. This would allow our system to be as accurate as possible. However, we did not want to constantly expose ourselves and our possible users to the large amount of profane and potentially hurtful language that can be found in a project similar to this. The key to solving this problem was utilising the global environment configuration files for our functions within Firebase Cloud Functions. We were able to set the environment configurations to a JSON object with unique attributes. We designated one of these attributes as just one long string of profane words connected by full stops so that you could split into a list of words using "split(".")". This allows us to just import that list of profane words without anyone seeing them. Then, during the analysis of the text, the profane words are taken into account for the calculation but are not stored in the stats that the user will see. We wanted to have a professional and academic approach to solving this issue and environmental configurations allowed us to achieve that.

Opinion strength accuracy is very vital to the analysis of a piece's sentiment. Of course, being able to analyze the sentiment of a text is significant but having the ability to test its weight and accuracy are just as important. Some sentences are more positive than other positive sentences, and the same goes for negative sentences. The system should be able to notice this distinction. Fortunately, the sentiment module we have utilises the AFINN 165 academic lexicon, a data set of over 3000 words with each word having a number from -5 to 5 indicating how positive or negative that word is. This allows our system to see which opinions are more positive or negative than other similar opinions. We also must prove that information we gather is accurate. The sentiment modules provide a function called "validate" which takes in a data set and then iterates through and analyzes each element's sentiment. After this, the accuracy of each elements' sentiment is calculated by testing the class and comparative score of the element and whether it passes or fails, a respective counter is incremented. Then the overall accuracy of the piece is calculated and returned by the function. Since the validate function operates quickly, it allows for quick and precise measurements of the accuracy of a data set the app acquires.

Abbreviations and poor spelling can be nightmares to deal with. The almost infinite amount of spelling mistakes alone can make navigating the sentiment of a piece very difficult. We decided not to take spelling mistakes into account and we simply leave any incorrectly spelled words as neutral and give them a sentiment of zero. However, the AFINN 165 lexicon does have plenty of abbreviations already stored within its library. Making use of that, we were able to get the sentiment of words like "lol" and "ftw". This allowed our results to be much more accurate than otherwise possible.
### 4.2 Application Issues and Solutions
### 4.3 Firebase Issues and Solutions
When utilising Firebase and its many available services, there were many steep challenges that needed to be overcome. Below are the many issues that needed to be resolved:
- (Wiki put a major technical issue you had with Firebase here)
- (Wiki put a major technical issue you had with Firebase here)
- function calls and functions triggers, testing
- payment plan changes

A key part of using Firebase Cloud Functions involves using specific triggers or calls that execute the code when a certain condition is made. There are many events that a developer can set for their function. Some examples include when you make a HTTP get request (which causes what is known as a HTTP trigger) or when a file is saved onto their Firebase Storage service (a Cloud Storage trigger). However, performing the testing for whether this event is triggered is difficult. There is a vital lack of a virtual testing environment where the function can be run as if the trigger condition has been met. Testing is absolutely critical to any system being developed. The function must be time consumingly deployed and no information is given as to whether the function operates at that point either. To test the function, the trigger must be manually performed and depending on the trigger that can be costly in time as well. To see the results, you must enter a different tab and check the logs. This process of painstakingly deploying, triggering the event and checking the logs was a major time consuming issue that we needed to overcome. We utilized a Javascript Testing Framework called Mocha that allowed us to quickly run tests of the Firebase-less versions of the code we were developing instead. This saved us a lot of time as we were constantly testing our code in AGILE way. We would test the app, get feedback from users on our app, make more changes, test those iterative changes and get more user feedback in that constant loop. Streamlining and making it easier to perform the testing assisted us immensely for the AGILE approach we took for this app.

When it comes to Firebase, there are different prices and limits depending on what payment plan is chosen. The Spark plan is the free option but it is very limiting in terms of what you can do. For example, you cannot utilise multiple databases for one project, you cannot utilise multiple buckets for storage for one project and the caps set for memory usage and function calls are far too small, even just for a project similar to this one. We found ourselves at the limit of the Spark plan about halfway through the project. This stopped us from continuing working on the project completely. To solve this problem, we were forced to upgrade to the Blaze plan. In order to actually use Firebase for the whole duration of our project, we needed to upgrade to the Blaze plan. This plan operates on a pay as you go system, with less restrictions and bigger caps for service users. The issue was if a user went past these caps, they would have to pay a fee so we had to make sure those limits were never reached in order for the Blaze plan to stay free. Fortunately there is a dashboard where you can view how close you are to the limit so we were able to monitor our usage and progress closely. 

# 5. Installation Guide
This is a 1 to 2 page section which contains a step by step software installation guide. It
should include a detailed description of the steps necessary to install the software, a list of all required software, components, versions, hardware, etc.
### 5.1 Required Software, Hardware, Versions, Components
### 5.2 Step by Step Instructions


