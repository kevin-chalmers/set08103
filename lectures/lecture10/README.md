# Lecture 10: User Stories and Use Cases

## User Stories

As opposed to requirements ( which by common definition represent something the system must do to fulfill a business need or contractual obligation ) , user stories are brief statements of intent that describe something the system needs to do for some user . As commonly taught , the user story often takes a standard user - voice form of the following

As a < user role > , I can < activity > so that < business value > .

Conditions of Satisfaction

For more detailed tracking of the activities involved in delivering stories , teams typically decompose stories into tasks that must be accomplished by individual team members in order to complete the story . Indeed , some agile training uses the task object as the basic estimating and tracking metaphor

Epics represent the highest - level expression of a customer need . Epics are development initiatives that are intended to deliver the value of an investment theme and are identified , prioritized , estimated , and maintained in the portfolio backlog . Prior to release planning , epics are decomposed into specific features , which in turn are converted into more detailed stories for implementation . Epics may be expressed in bullet form , in user - voice story form , as a sentence or two , in video , in a prototype , or indeed in any form of expression suitable to express the intent of the product initiative . With epics , clearly , the objective is strategic intent , not specificity . In other words , the epic need only be described in detail sufficient to initiate a further discussion about what types of features an epic implies

Define:Even if the story is well - elaborated , the developer will likely still interact with the product owner to understand what is meant by the story . Also , some design will likely be present in the developer’s mind , and if not , one will quickly be created and communicated to the product owner , peer developers , and testers . We use the word define to communicate that this function is a combination of both requirements and design . They are inseparable ; neither has any meaning without the other . ( If you don’t know how to do IT , then you don’t really know what IT is ! ) • Build:The actual coding of the story provides an opportunity for new discovery as well . Conversations will again ensue between developer / product owner , developer / other developers , and developer / tester . Story understanding evolves during the coding process . • Test:A “ story ” is not considered complete until it has passed an acceptance test ( the topic of Chapter 10 ) , which assures that the code meets the intent of the story . Building functional acceptance tests ( plus unit tests ) before , or in parallel with the code , again tests the team’s understanding of the subject story .

We’ll define a user story as follows : A user story is a brief statement of intent that describes something the system needs to do for the user . As commonly taught , the user story takes a standard ( user voice ) form : As a < role > , I can < activity > so that < business value > .

A task is a small unit of work that is necessary for the completion of a story .

Tasks have an owner ( the person who has taken responsibility for the task ) and are estimated in hours ( typically four to eight ) .

Task 51.1 : Define acceptance test — Juha , Don , Bill Task 51.2 : Code story — Juha Task 51.3 : Code acceptance test — Bill Task 51.4 : Get it to pass — Juha and Bill Task 51.5 : Document in user help — Cindy

However , for flexibility , the model also supports stand - alone tasks and tasks that support other team objectives . With this construct , a team need not create a story simply to parent an item such as “ install more memory in the file server . ”

we represent the confirmation function as a type of acceptance test , one that confirms the story has been implemented correctly . To separate it from other types of acceptance tests ( an overloaded term in software ) , we’ll call them story acceptance tests and treat them as an artifact distinct from the ( user ) story itself , as shown in Figure 3 - 10 . Figure 3 - 10 . Every story has one or more story acceptance tests .

Acceptance tests are functional tests that verify that the system implements the story as intended .

Quality is built in , one story at a time . Continued assurance of quality is achieved by continuous and automated execution of the aggregated functional and unit tests .

Define a user value story , implement and test it in a short iteration , demonstrate / and or deliver it to the user , repeat forever !

The story is the unit of functionality in an XP project . We demonstrate progress by delivering tested , integrated code that implements a story . A story should be understandable to customers , developer - testable , valuable to the customer , and small enough that the programmers can build half a dozen in an iteration .

A user story is a brief statement of intent that describes something the system needs to do for the user .

User Stories Are Not Requirements Although user stories do most of the work previously done by software requirements specifications , use cases , and the like , they are materially different in a number of subtle yet critical ways . • They are not detailed requirements specifications ( something a system shall do ) but are rather negotiable expressions of intent ( it needs to do something about like this ) . • They are short , easy to read , and understandable to developers , stakeholders , and users . • They represent small increments of valued functionality that can be developed in a period of days to weeks . • They are relatively easy to estimate , so effort to implement the functionality can be rapidly determined . • They are not carried in large , unwieldy documents but rather organized in lists that can be more easily arranged and rearranged as new information is discovered . • They are not detailed at the outset of the project but are elaborated on a just - in - time basis , thereby avoiding too - early specificity , delays in development , requirements inventory , and an over - constrained statement of the solution • They need little or no maintenance and can be safely discarded after implementation . 2,3 • User stories , and the code that is created quickly thereafter , serve as inputs to documentation , which is then developed incrementally as well .

Card , Conversation , and Confirmation

As a < role > , I can < activity > so that < business value > . where : • < role > represents who is performing the action or perhaps one who is receiving the value from the activity . It may even be another system , if that is what is initiating the activity . • < activity > represents the action to be performed by the system . • < business value > represents the value achieved by the activity .

Acceptance criteria are not functional or unit tests ; rather , they are the conditions of satisfaction being placed on the system . Functional and unit tests go much deeper in testing all functional flows , exception flows , boundary conditions , and related functionality associated with the story .

Bill Wake coined the acronym INVEST6 to describe the attributes of a good user story . Independent Negotiable Valuable Estimable Small Testable

Take responsibility for an assigned backlog item ( for example , user story , defect fix , other ) . Develop ( refine , design , code , integrate , and test ) the backlog item . Deliver the backlog item by integrating it into a system build . Declare the backlog item as developed , signaling that it is ready for acceptance testing . Get the backlog item accepted by the product owner .

We understand that stories ( requirements ) , implementation ( code ) , and validation ( acceptance tests , unit tests , and others ) are not separate activities but a continuous refinement of a much deeper understanding ; therefore , our thinking is different :

UML of a user story.

### Cockburn's Use Case Symbols

A commonly cited text on use cases is *Writing Effective Use Cases* by Alistair Cockburn.  Many of the ideas around use cases in this module are taken from Cockburn's work.  In particular, we consider two aspects: **scope** and **goal level**.

#### Scope

*Design scope* allows us to consider what should be part of our discussions and work to deliver valuable software.  It is *very easy* to add features to software which are not required, add no value, and are therefore doing work for no point.  **As a student you should always be thinking about the scope of your work.**  You may think it best to just do everything, or not plan what you are going to do, but this just leads to wasted effort.  And remember, **waste is our biggest problem when trying to be lean.**

Cockburn suggests a simple simple table

| Topic | In    | Out    |
| ----- | ----- | ------ |
| Invoicing in any form | | Out |

- [ ] TODO: ch3 of Writing Effective Use Cases.

| **Scope** | **Icon** |
| --------- | -------- |
| Organisation (black-box) | ![Filled House](img/Scope-icons-filled-house.png) |
| Organisation (white-box) | ![Unfilled House](img/Scope-icons-unfilled-house.png) |
| System (black-box) | ![Filled Box](img/Scope-icons-filled-box.png) |
| System (white-box) | ![Unfilled Box](img/Scope-icons-unfilled-box.png) |
| Component | ![Screw or Nut](img/Scope-icons-screw-bolt.png) |


| **Goal Level** | **Icon** | **Symbol** |
| -------------- | -------- | ---------- |
| Very High Summary | ![Cloud](img/Goal-level-icons-cloud.png) | ++ |
| Summary | ![Flying Kite](img/Goal-level-icons-flying-kite.png) | + |
| Use Goal | ![Waves at Sea](img/Goal-level-icons-waves-at-sea.png) | ! |
| Subfunction | ![Fish](img/Goal-level-icons-fish.png) | - |
| Too Low | ![Seabed Clam-shell](img/Goal-level-icons-seabed-clam-shell.png) | -- |

<a title="Menner [CC0], from Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Cockburnstyle_use_cases.svg"><img width="1024" alt="Cockburnstyle use cases" src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/82/Cockburnstyle_use_cases.svg/512px-Cockburnstyle_use_cases.svg.png"></a>

![Cockburn's Dimensions of Use Cases](img/Cockburns-dimensions-of-use-cases.png)

Metrics for use cases: A survey of current proposals - Scientific Figure on ResearchGate. Available from: https://www.researchgate.net/figure/Cockburns-dimensions-of-use-cases_fig1_279404900 [accessed 4 Jan, 2019]