# xRoad
A metadata-based database backend was written in POJ. This backend deploys a data abstraction strategy to allow for any or multiple data backends.
 
TL;DR
 
An enterprise software application aims to automate processes, and all business processes generate & use data. This framework forms a single simple methodology for managing data that the application needs/generates and how/where it is stored. 

Over the years, I have developed dozens of enterprise applications from the ground up. I have always come back to the principle that a strong foundation is a baseline for any practical application. That baseline is how an application manages the data streams it generates and needs. Typically, a lot of effort will go into the front-end GUI and processes (rightfully so), but the data processing is often treated as an afterthought. The impact is that the application's day-to-day maintenance becomes very complicated and, thus, time-consuming. Building a framework that addresses simplicity and ease of use to take care of the data-oriented tasks (and add a few side benefits) makes a lot of sense.

I have become tired of reinventing myself and building another back-end. It was about time to design and develop a simple-to-use framework based on timeless design principles: abstract business rules from data structures and abstract the data structure from the requirements of the underlying database flavor.

<rant> Let me expand on one pet peeve about complexity, which is one reason I built this framework (indulge me here for a moment). There are many frameworks out there, and adding one does not make it easier. Still, everywhere I looked, I needed help finding one that was easy to understand, easy to maintain, and did not have a multi-week learning curve. Come on; most frameworks need you to buy & read a book to grok … fully? Complexity is the death of software development. I have always tried to build software that could be understood within an hour. You will notice this framework does not contain hundreds of classes and methodologies, maybe not even all the sexiest stuff that Java can bring to bear, but it works … it is quick …. and it is reliable.</rant>

Architecture

How a well-designed application should look has evolved over the years (not to be confused with how it is developed, a separate discussion). The most widely accepted and, in my view, the most logical design approach is the MVC model. 

As per Wikipedia: 
A model stores data retrieved according to commands from the controller and displayed in the view.
A view generates new output for the user based on changes in the model.
A controller can send commands to the model to update the model's state (e.g., editing a document). It can also send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document.)
The model is stored in the database, the view is whatever GUI we use to represent the process, and the controller is what will be described here. The view (user interactions) initiates the controller in a model-independent fashion; the controller translates the request between the view and the model. This is called "Data Model Abstraction" here or DMA for short.

For example: "I need a list of customers sorted by name for the sales region Germany." The controller translates this high-level query (query abstraction) into a DB-specific SQL statement that will query the database and return the rows that match the query's criteria.
This is the most crucial component of this framework from a development and maintenance perspective. Applications are implementations of business rules and processes, creating and using data. Much too often, this is implemented so that it is challenging, if not impossible, to review and maintain without much effort. Maintaining and debugging someone else's code can be difficult; comments are often unused, and a single process can be mangled into many (sub)classes and functions. Encapsulating and abstracting data queries and updates under a logical name and removing that logic from the code to a centralized self-documenting XML makes (parallel and agile) development, testing, and maintenance much more manageable.

Databases form the heart of any application. They range from expensive commercial systems to lightweight open-source database management systems. The data layer depends on the application type and how the data will be managed. High levels of fluid transactional data require a different database type than static, read-only data.

The main problem is that design decisions concerning the data model taken when creating the application will influence the application for its complete lifetime. It is challenging to extract all data-relevant structures from an existing application and port it to another one if we move to a new database vendor or into the cloud. This is almost a complete rewrite and needs to be redone each time the data storage layer changes.
It is best practice to design applications that do not have to take implementation decisions (like database vendors) into account in the design phase. A data abstraction layer (DAL) is used to achieve this.

Business processes and corresponding business rules change frequently. This will impact the application, of course, and possibly (probably) the underlying data model. This framework's architecture based on an abstraction between business and data models (the Data Abstraction Layer, OR DAL) is set up to cater to multiple data models per object, allowing for an incremental & agile approach to business changes with minimal impact to an application.
