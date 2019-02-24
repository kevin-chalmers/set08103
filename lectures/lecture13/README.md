# Lecture 13: The Second Way of DevOps - Feedback

## Behavioural Objectives

- [ ] TODO

## Create Telemetry to Enable Seeing and Solving Problems

Telemetry is defined in *The DevOps Handbook* as:

**Telemetry**: an automated communications process by which measurements and other data are collected at remote points and are subsequently transmitted to receiving equipment for monitoring.

We need to create telemetry from applications, environments, build pipelines, etc. in our pre-production, production and deployment environments.  Our aim is to provide information to allow developers and operations to solve problem collaboratively.  This is to overcome the following scenario:

> When something goes wrong in production, we just reboot the server.  If that doesn't work, reboot the server next to it.  If that doesn't work, reboot all the servers.  If that doesn't work, blame the developers, they're always causing outages.
>
> -The DevOps Handbook

Rebooting servers is not a good sign of service profession.  It has been shown that organisations with higher service levels reboot servers 20% less often.  Rather, we use telemetry to understand contributing factors.

To enable problem-solving our systems need to continuously provide telemetry.  Developers should add telemetry to their features as part of daily work to make deployments safe.

### Create Our Centralised Telemetry infrastructure

We have to go beyond the standard methods: more than logs that are useful to developers, or system status that is interesting to operations.  We must develop applications and environments that sufficient telemetry that will allow us to understand system behaviour.  We enable capabilities such as graphing and visualising metrics, anomaly detection, proactive alerting and escalation, etc.  We also need information from deployment.  How long to build?  How long to test?  And so on.

Telemetry architecture has the following components:

- Data collection at the business logic, application, and environments layer.
- An event router responsible for storing our events and metrics.

Ideally we should have APIs to allow easy access to the telemetry data.  We want these to transform logs into metrics.  This allows statistical analysis to, for example, detect anomalies.  Instead of *SQL query failed* we get *10 SQL query fails per week*.

### Create Application Logging Telemetry That Helps Production

If you've built it, you should measure it:

> Every feature should be instrumented: if it was important enough for an engineer to implement, it is certainly important enough to generate enough production telemetry so that we can confirm that it is operating as designed and that the desired outcomes are being achieved.
>
> -The DevOps Handbook.

*The DevOps Handbook* also provides a list of logging events:

- Authentication/authorization decisions (including logoff).
- System and data access.
- System and application changes (especially privileged changes).
- Data changes, such as adding, editing, or deleting data Invalid input (possible malicious injection, threats, etc.).
- Resources (RAM, disk, CPU, bandwidth, or any other resource that has hard or soft limits).
- Health and availability.
- Start-ups and shutdowns.
- Faults and errors.
- Circuit breaker trips.
- Delays Backup success/failure.

Finally, these events can be logged at different levels:

Logging levels:

- **DEBUG**: anything that happens in the program.
- **INFO**: actions that are user-driven or system specific.
- **WARN**: conditions that could potentially become an error.  Should initiate an alert.
- **ERROR**: error conditions (e.g., API call failures, internal error conditions).
- **FATAL**: when we must terminate (e.g., failed to create network socket).

### Use Telemetry to Guide Problem-solving

Remember we want to promote a culture of learning and collaboration.  In a culture of blame, outages and problems are not documented and displaying telemetry where everyone can see them to avoid being blamed for outages.  In a culture of learning and collaboration, telemetry enables the scientific method to formulate hypotheses about what is causing problems and what we need to do to solve them.

Examples of questions we can answer (from *The DevOps Handbook*):

- What evidence do we have from our monitoring that a problem is actually occurring?
- What are the relevant events and changes in our applications and environments that could have contributed to the problem?
- What hypotheses can we formulate to confirm the link between the proposed causes and effects?
- How can we prove which of these hypotheses are correct and successfully effect a fix?

### Enable Creation of Production Metrics as Part of Daily Work

Production telemetry as part of daily work means we improve out capability to visualise problems as they appear for both development and operations. It should be as simple as writing one line of code to create a new metric that is displayed in a dashboard for everyone to see.

### Create Self-service Access to Telemetry and Information Radiators

Telemetry must be fast, easy to get, and sufficiently centralized.  This allows everyone to see what is happening.  Telemetry should be highly visible as so to be where people work.  Therefore everyone know how services are working.

An information radiator is defined by the Agile Alliance as:

> the generic term for any of a number of handwritten, drawn, printed, or electronic displays which a team places in a highly visible location, so that all team members as well as passers - by can see the latest information at a glance: count of automated tests, velocity, incident reports, continuous integration status, and so on.

Placing information radiators in highly visible places promotes team responsibility.  The team has nothing to hide from visitors (customers, stakeholders, etc.), and the team has nothing to hide from itself.  The team acknowledges and confronts problems.  We may also broadcast internally and externally to customers.

### Find and Fill Any Telemetry Gaps

We must create telemetry for all levels of the application and environment, as well as the deployment pipeline.  This includes the following levels:

- **Business level**: e.g., the number of sales transactions, revenue of sales transactions, user signups, churn rate, A/B testing results, etc.
- **Application level**: e.g., transaction times, user response times, application faults, etc.
- **Infrastructure level**: e.g., web server traffic, CPU load, disk usage, etc.
- **Client software level**: e.g., application errors and crashes, user measured transaction times, etc.
- **Deployment pipeline level**: e.g., build pipeline status, change deployment lead times, deployment frequencies, test environment promotions, and environment status.

#### Application and Business Metrics

Not only application health (e.g., memory usage, transaction counts, etc.), but also meeting of business goals (e.g., number of new users, user login events, user session lengths, percent of users active, how often certain features are being used. and so forth).  Business metrics should be actionable - how to change our product and inform experimentation and A/B testing.  If they cannot be actioned they are vanity metrics.

The information radiators should make sense to everyone and align to business goals (e.g., revenue, user attainment, etc.).  Each metric should link to a business outcome and measure these in production.

#### Infrastructure Metrics

We need telemetry to see if problems are occurring in the environment.  The telemetry needs to highlight which part of the infrastructure is a problem, e.g.,:

- database.
- operating system.
- storage.
- networking.
- etc.

#### Overlaying Other Relevant Information Onto Our Metrics

Changes should be visibly mapped to the graphs.  This makes work visible and highlights where a problem may have occurred.  For example, a system with a large number of transactions may take time to return to normal operation.  We want to see how quickly this is, and to spot any anomalies.  

## Analyse Telemetry to Better Anticipate Problems and Achieve Goals

The whole point of having telemetry is to spot problems and measure success.  But having data is not enough.  We need to analyse the data and from this analysis highlight issues or take action.  Data analysis is a large field in its own right, so we will skim some of the ideas only.

### Use Means and Standard Deviations to Detect Potential Problems

Calculating the mean (or average) of our data is a useful starting point.  Combining with standard deviation (the amount of variation in the data) allows to filter events so that we only respond to results outside the norm.  Below is a diagram illustrating a normal (or Gaussian) distribution and standard deviations.

<p><a href="https://commons.wikimedia.org/wiki/File:Empirical_Rule.PNG#/media/File:Empirical_Rule.PNG"><img src="https://upload.wikimedia.org/wikipedia/commons/a/a9/Empirical_Rule.PNG" alt="Empirical Rule.PNG" height="464" width="640"></a><br>By <a href="//commons.wikimedia.org/w/index.php?title=User:Mathprofdk&amp;action=edit&amp;redlink=1" class="new" title="User:Mathprofdk (page does not exist)">Dan Kernler</a> - <span class="int-own-work" lang="en">Own work</span>, <a href="https://creativecommons.org/licenses/by-sa/4.0" title="Creative Commons Attribution-Share Alike 4.0">CC BY-SA 4.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=36506025">Link</a></p>

We are trying to improve the signal-to-noise ratio by spotting outliers.  We analyse the data set for a metric and alert if it is significantly varied from the mean.  For example, if failed login attempts for a day is three standard greater than the mean.

### Instrument and Alert on Undesired Outcomes

Post-mortems of severe incidents allows us to determine what telemetry would have helped spot the problem earlier.  *The DevOps Handbook* details such indicators for a web server going down:

- Application level: increasing web page load times, etc.
- OS level: server free memory running low, disk space running low, etc.
- Database level: database transaction times taking longer than normal, etc.
- Network level: number of functioning servers behind the load balancer dropping, etc.

By continually undertaking this post-mortem work we allow faster problem finding and therefore improve our quality of service.

### Problems that Arise When Our Telemetry Data Has Non-Gaussian Distribution

If our data does not form a normal distribution we have to use other techniques of analysis.  At this point, deeper statistical analysis is required.  Although under-reporting is a major problem, over-reporting will mean people do not take errors seriously, or people may be woken up in the middle of the night for a non-event.

### Using Anomaly Detection Techniques

Anomaly detection is *the search for items or events which do not conform to an expected pattern.*  One such technique is smoothing, where we average across a range of the data points rather than at a single data point.  Other techniques include Fast Fourier Transforms, and the Kolmogorov-Smirnov tests.

## Enable Feedback So Development and Operations Can Safely Deploy 

Deployment should be a safe act.  This can be done via improved telemetry, peer review, and automated testing.  The aim is to encourage small yet well informed changes so that risk is reduced.  Small changes that anyone can understand is the goal.

### Use Telemetry to Make Deployments Safer

Telemetry for application and system health is important, but don't forget gathering metrics about the deployment pipeline.  Again, using the techniques of finding gaps, doing post-mortems, etc., will help identify what telemetry will make our deployments safer.

### Dev Shares Pager Rotation Duties With Ops

We are trying to avoid developers marking work as done because they have finished a feature and passed it to the operations team.  The goal of DevOps is to have development and operations working together.  By ensuring everyone on the team (dev and ops) has responsibility for operational incidents, everyone will take ownership of the decisions they make.

We do this so defects are given priority by the development team.  If problems keep occurring and operations cannot resolve these problems, then our system is becoming more fragile and our quality of service is reducing.  The side effect of this practice is development sees done as features working in production rather than code being written.

### Have Developers Follow Work Downstream

User Experience (UX) design uses contextual inquiry.  This is a practice where product teams watch a customer use an application in their natural environment.  We can use this approach for developers.

Developers normally do not watch people using their software.  When they do, developers are often dismayed by how users actually work, stating that they didn't realise all the problems they were causing their customers.

Developers should follow their work downstream.  That includes testing and operations as well as customers.  By doing so, development better understands the problems that occur with the work they do, and thereby improve their practices.

### Have Developers Initially Self-manage Their Production Service

When new products are initially worked on, development should self-manage their production environment.  This helps development understand production.  Once the product is of a significant size, operations can come in to support the production.

Product launch guidance can be produced to support new development teams.  *The DevOps Handbook* defines such guidance and requirements:

- Defect counts and severity: Does the application actually perform as designed?
- Type/frequency of pager alerts: Is the application generating an unsupportable number of alerts in production?
- Monitoring coverage: Is the coverage of monitoring sufficient to restore service when things go wrong?
- System architecture: Is the service loosely - coupled enough to support a high rate of changes and deployments in production?
- Deployment process: Is there a predictable, deterministic, and sufficiently automated process to deploy code into production?
- Production hygiene: Is there evidence of enough good production habits that would allow production support to be managed by anyone else?

## Integrate Hypothesis-Driven Development and A/B Testing into Our Daily Work

Our aim is to meet business goals.  Developers working on long-term features and products need to confirm that the work they are doing is meeting these business goals, or indeed is being used at all.

Before building a feature, 

Before we build a feature , we should rigorously ask ourselves , “ Should we build it , and why ? ” We should then perform the cheapest and fastest experiments possible to validate through user research whether the intended feature will actually achieve the desired outcomes .

The faster we can experiment , iterate , and integrate feedback into our product or service , the faster we can learn and out - experiment the competition .

### A Brief History of A/B Testing

A / B testing techniques were pioneered in direct response marketing , which is one of the two major categories of marketing strategies .

In previous eras , before email and social media , direct response marketing meant sending thousands of postcards or flyers via postal mail , and asking prospects to accept an offer by calling a telephone number , returning a postcard , or placing an order . In these campaigns , experiments were performed to determine which offer had the highest conversion rates . They experimented with modifying and adapting the offer , re - wording the offer , varying the copywriting styles , design and typography , packaging , and so forth , to determine which was most effective in generating the desired action ( e.g . , calling a phone number , ordering a product ) .

Well - documented cases of A / B testing include campaign fundraising , Internet marketing , and the Lean Startup methodology . Interestingly , it has also been used by the British government to determine which letters were most effective in collecting overdue tax revenue from delinquent citizens .

### Integrate A/B Testing into Our Feature Testing

The most commonly used A / B technique in modern UX practice involves a website where visitors are randomly selected to be shown one of two versions of a page , either a control ( the “ A ” ) or a treatment ( the “ B ” ) . Based on statistical analysis of the subsequent behavior of these two cohorts of users , we demonstrate whether there is a significant difference in the outcomes of the two , establishing a causal link between the treatment ( e.g . , a change in a feature , design element , background color ) and the outcome ( e.g . , conversion rate , average order size ) .

If we are not performing user research , the odds are that two - thirds of the features we are building deliver zero or negative value to our organization , even as they make our codebase ever more complex , thus increasing our maintenance costs over time and making our software more difficult to change 

Our countermeasure is to integrate A / B testing into the way we design , implement , test , and deploy our features . Performing meaningful user research and experiments ensures that our efforts help achieve our customer and organizational goals , and help us win in the marketplace .

### Integrate A/B Testing into Our Release

Fast and iterative A / B testing is made possible by being able to quickly and easily do production deployments on demand , using feature toggles and potentially delivering multiple versions of our code simultaneously to customer segments .

### Integrating A/B Testing into Our Feature Planning

how we can frame hypotheses in feature development in the following form : We Believe that increasing the size of hotel images on the booking page Will Result in improved customer engagement and conversion We Will Have Confidence To Proceed When we see a 5 % increase in customers who review hotel images who then proceed to book in forty - eight hours .

## Create Review and Coordination Processes to Increase Quality of Or Current Work

Our goal in this chapter is to enable Development and Operations to reduce the risk of production changes before they are made .

The peer review process at GitHub is a striking example of how inspection can increase quality , make deployments safe , and be integrated into the flow of everyone’s daily work .

Scott Chacon , CIO and co - founder of GitHub , wrote on his website that pull requests are the mechanism that lets engineers tell others about changes they have pushed to a repository on GitHub . Once a pull request is sent , interested parties can review the set of changes , discuss potential modifications , and even push follow - up commits if necessary . Engineers submitting a pull request will often request a “ + 1 , ” “ + 2 , ” or so forth , depending on how many reviews they need , or “ @ mention ” engineers that they’d like to get reviews from . At GitHub , pull requests are also the mechanism used to deploy code into production through a collective set of practices they call “ GitHub Flow ” — it’s how engineers request code reviews , gather and integrate feedback , and announce that code will be deployed to production ( i.e . , “ master ” branch ) .

GitHub Flow is composed of five steps : To work on something new , the engineer creates a descriptively named branch off of master ( e.g . , “ new - oauth2 - scopes ” ) . The engineer commits to that branch locally , regularly pushing their work to the same named branch on the server . When they need feedback or help , or when they think the branch is ready for merging , they open a pull request . When they get their desired reviews and get any necessary approvals of the feature , the engineer can then merge it into master . Once the code changes are merged and pushed to master , the engineer deploys them into production .

### The Dangers of Change Approval Processes

The Knight Capital failure is one of the most prominent software deployment errors in recent memory . A fifteen minute deployment error resulted in a $ 440 million trading loss , during which the engineering teams were unable to disable the production services . The financial losses jeopardized the firm’s operations and forced the company to be sold over the weekend so they could continue operating without jeopardizing the entire financial system .

John Allspaw observed that when high - profile incidents occur , such as the Knight Capital deployment accident , there are typically two counterfactual narratives for why the accident occurred . † The first narrative is that the accident was due to a change control failure , which seems valid because we can imagine a situation where better change control practices could have detected the risk earlier and prevented the change from going into production . And if we couldn’t prevent it , we might have taken steps to enable faster detection and recovery . The second narrative is that the accident was due to a testing failure . This also seems valid , with better testing practices we could have identified the risk earlier and canceled the risky deployment , or we could have at least taken steps to enable faster detection and recovery .

The surprising reality is that in environments with low - trust , command - and - control cultures , the outcomes of these types of change control and testing countermeasures often result in an increased likelihood that problems will occur again , potentially with even worse outcomes .

### Potential Dangers of "Overly Controlling Changes"

Traditional change controls can lead to unintended outcomes , such as contributing to long lead times , and reducing the strength and immediacy of feedback from the deployment process . In order to understand how this happens , let us examine the controls we often put in place when change control failures occur : Adding more questions that need to be answered to the change request form Requiring more authorizations , such as one more level of management approval ( e.g . , instead of merely the VP of Operations approving , we now require that the CIO also approve ) or more stakeholders ( e.g . , network engineering , architecture review boards , etc . ) Requiring more lead time for change approvals so that change requests can be properly evaluated

These controls often add more friction to the deployment process by multiplying the number of steps and approvals , and increasing batch sizes and deployment lead times , which we know reduces the likelihood of successful production outcomes for both Dev and Ops . These controls also reduce how quickly we get feedback from our work .

One of the core beliefs in the Toyota Production System is that “ people closest to a problem typically know the most about it . ”

As has been proven time and again , the further the distance between the person doing the work ( i.e . , the change implementer ) and the person deciding to do the work ( i.e . , the change authorizer ) , the worse the outcome .

At one extreme , we cannot reliably predict whether a change will be successful either by reading a hundred - word description of the change or by merely validating that a checklist has been completed . At the other extreme , painfully scrutinizing thousands of lines of code changes is unlikely to reveal any new insights . Part of this is the nature of making changes inside of a complex system . Even the engineers who work inside the codebase as part of their daily work are often surprised by the side effects of what should be low - risk changes .

we need to create effective control practices that more closely resemble peer review , reducing our reliance on external bodies to authorize our changes .

### Enable Coordination and Scheduling of Changes

Whenever we have multiple groups working on systems that share dependencies , our changes will likely need to be coordinated to ensure that they don’t interfere with each other ( e.g . , marshaling , batching , and sequencing the changes ) .

For more complex organizations and organizations with more tightly - coupled architectures , we may need to deliberately schedule our changes , where representatives from the teams get together , not to authorize changes , but to schedule and sequence their changes in order to minimize accidents .

### Enable Peer Review of Changes

Instead of requiring approval from an external body prior to deployment , we may require engineers to get peer reviews of their changes . In Development , this practice has been called code review , but it is equally applicable to any change we make to our applications or environments , including servers , networking , and databases .

A logical place to require reviews is prior to committing code to trunk in source control , where changes could potentially have a team - wide or global impact .

The principle of small batch sizes also applies to code reviews . The larger the size of the change that needs to be reviewed , the longer it takes to understand and the larger the burden on the reviewing engineer .

Furthermore , our ability to meaningfully critique code changes goes down as the change size goes up . As Giray Özil tweeted , “ Ask a programmer to review ten lines of code , he’ll find ten issues . Ask him to do five hundred lines , and he’ll say it looks good . ”

Guidelines for code reviews include : Everyone must have someone to review their changes ( e.g . , to the code , environment , etc . ) before committing to trunk . Everyone should monitor the commit stream of their fellow team members so that potential conflicts can be identified and reviewed . Define which changes qualify as high risk and may require review from a designated subject matter expert ( e.g . , database changes , security - sensitive modules such as authentication , etc . ) . § If someone submits a change that is too large to reason about easily — in other words , you can’t understand its impact after reading through it a couple of times , or you need to ask the submitter for clarification — it should be split up into multiple , smaller changes that can be understood at a glance .

Code reviews come in various forms : Pair programming : programmers work in pairs ( see section below ) “ Over - the - shoulder ” : One developer looks over the author’s shoulder as the latter walks through the code . Email pass - around : A source code management system emails code to reviewers automatically after the code is checked in . Tool - assisted code review : Authors and reviewers use specialized tools designed for peer code review ( e.g . , Gerrit , GitHub pull requests , etc . ) or facilities provided by the source code repositories ( e.g . , GitHub , Mercurial , Subversion , as well as other platforms such as Gerrit , Atlassian Stash , and Atlassian Crucible ) .

### Potential Dangers of Doing More Manual Testing and Change Freezes

When testing failures occur , our typical reaction is to do more testing . However , if we are merely performing more testing at the end of the project , we may worsen our outcomes .

Instead of performing testing on large batches of changes that are scheduled around change freeze periods , we want to fully integrate testing in our daily work as part of the smooth and continual flow into production , and increase our deployment frequency . By doing this , we build in quality , which allows us to test , deploy , and release in ever smaller batch sizes .

### Enable Pair Programming to Improve All Our Changes

Pair programming is when two engineers work together at the same workstation ,

In one common pattern of pairing , one engineer fills the role of the driver , the person who actually writes the code , while the other engineer acts as the navigator , observer , or pointer , the person who reviews the work as it is being performed . While reviewing , the observer may also consider the strategic direction of the work , coming up with ideas for improvements and likely future problems to address . This frees the driver to focus all of his or her attention on the tactical aspects of completing the task , using the observer as a safety net and guide . When the two have differing specialties , skills are transferred as an automatic side effect , whether it’s through ad - hoc training or by sharing techniques and workarounds .

Another pair programming pattern reinforces test - driven development ( TDD ) by having one engineer write the automated test and the other engineer implement the code .

Pair programming has the additional benefit of spreading knowledge throughout the organization and increasing information flow within the team 

#### Evaluating the Effectiveness of Pull Request Processes

Because the peer review process is an important part of our control environment , we need to be able to determine whether it is working effectively or not . One method is to look at production outages and examine the peer review process for any relevant changes .

When asked to describe the difference between a bad pull request and a good pull request , he said it has little to do with the production outcome . Instead , a bad pull request is one that doesn’t have enough context for the reader , having little or no documentation of what the change is intended to do .

### Fearlessly Cut Bureaucratic Processes

These approval processes can significantly increase lead times , not only preventing us from delivering value quickly to customers , but potentially increasing the risk to our organizational objectives . When this happens , we must re - engineer our processes so that we can achieve our goals more quickly and safely .

As Adrian Cockcroft observed , “ A great metric to publish widely is how many meetings and work tickets are mandatory to perform a release — the goal is to relentlessly reduce the effort required for engineers to perform work and deliver it to the customer . ”

## Summary

## Recommended Reading