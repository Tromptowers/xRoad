# xRoad
A metadata based database backend written in POJ. This is backend deploys a data abstraction strategy to allow for any or multiple data backends.
 
TL;DR
 
An enterprise software application aims to automate processes, and all business processes generate & use data. This framework forms a single simple methodology for managing data that the application needs/generates and how/where it is stored. 

Over the years, I have developed dozens of enterprise applications from the ground up. I have always come back to the principle that a strong foundation is a baseline for any practical application. That baseline is how an application manages the data streams it generates and needs. Typically, a lot of effort will go into the front-end GUI and processes (rightfully so), but the data processing is often treated as an afterthought. The impact is that the application's day-to-day maintenance becomes very complicated and, thus, time-consuming. Building a framework that addresses simplicity and ease of use to take care of the data-oriented tasks (and add a few side benefits) makes a lot of sense.

I have become tired of reinventing myself and building another back-end. It was about time to design and develop a simple-to-use framework based on timeless design principles: abstract business rules from data structures and abstract the data structure from the requirements of the underlying database flavor.

<rant> Let me expand on one pet peeve about complexity, which is one reason I built this framework (indulge me here for a moment). There are many frameworks out there, and adding one does not make it easier. Still, everywhere I looked, I needed help finding one that was easy to understand, easy to maintain, and did not have a multi-week learning curve. Come on; most frameworks need you to buy & read a book to grok … fully? Complexity is the death of software development. I have always tried to build software that could be understood within an hour. You will notice this framework does not contain hundreds of classes and methodologies, maybe not even all the sexiest stuff that Java can bring to bear, but it works … it is quick …. and it is reliable.</rant>
