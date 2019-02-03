# Lecture 07: The First Way of DevOps - Flow

In this lecture we will cover the technical practices of flow.  Flow is our ability to keep work moving from the left (development) to the right (customer) as quickly as possible.  There are a number of practices that we can adopt to increase flow in our environment; however, we will start by looking at the psychology of flow.

## Behavioural Objectives

- [ ] **Explain** the *psychology of flow*.
- [ ] **Describe** *good deployment pipeline practice*.
- [ ] **Describe** *good testing practices for flow*.
- [ ] **Describe** *release methods to encourage flow*.

## The Psychology of Flow

The concept of [Flow](https://en.wikipedia.org/wiki/Flow_(psychology)) was initially defined by  Mihály Csíkszentmihályi.  A Flow state involves the following six characteristics (taken from [Wikipedia](https://en.wikipedia.org/wiki/Flow_(psychology))):

1. Intense and focused concentration on the present moment.
2. Merging of action and awareness
3. A loss of reflective self-consciousness
4. A sense of personal control or agency over the situation or activity
5. A distortion of temporal experience, one's subjective experience of time is altered
6. Experience of the activity as intrinsically rewarding.

Another three identified components are:

1. Receiving immediate feedback.
2. Feeling that you have the potential to succeed.
3. Feeling so engrossed in the experience, that other needs become negligible.

The following diagram illustrates how flow features when mapped to skill level against challenge level.

<p><a href="https://commons.wikimedia.org/wiki/File:Challenge_vs_skill.svg#/media/File:Challenge_vs_skill.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Challenge_vs_skill.svg/400px-Challenge_vs_skill.svg.png" alt="Challenge vs skill.svg"></a><br>By <a href="https://en.wikipedia.org/wiki/User:Oliverbeatson" class="extiw" title="w:User:Oliverbeatson">w:User:Oliverbeatson</a> - <a href="https://en.wikipedia.org/wiki/File:Challenge_vs_skill.jpg" class="extiw" title="w:File:Challenge vs skill.jpg">w:File:Challenge vs skill.jpg</a>, Public Domain, <a href="https://commons.wikimedia.org/w/index.php?curid=9102943">Link</a></p>

As illustrated, flow occurs when the skill required to do a task is high (from the individual's point-of-view), and challenge is equally high (from the individual's point-of-view).

- [ ] Reflect on your own experiences when you might have experienced flow (playing video games is one known area for example).
- [ ] Reflect on which of the mental states as illustrated above you might have been in during the following tasks:
    - Attending a lecture.
    - Watching a movie.
    - Working on a lab for university.
    - Working on a coursework for university.
    - Doing an exam for university.

A further seven conditions of flow (taken from [Wikipedia](https://en.wikipedia.org/wiki/Flow_(psychology))) are:

1. Knowing what to do.
2. Knowing how to do it.
3. Knowing how well you are doing.
4. Knowing where to go (if navigation is involved).
5. High perceived challenges.
6. High perceived skills.
7. Freedom from distractions.

These seven are more inline with our thinking in the module, incorporating DevOps, Scrum, and general lean-agile ideas:

1. We need to know what to do, via clear information and agreement with the team (e.g., we understand the user story).
2. We know how to do the work, again via information and agreement with the team (e.g., user story) and our skillset.
3. Knowing how well we are doing comes from the feedback we get from the system.
4. Is not relevant from a navigation point of view, but we do have clear ideas of the direction of work from our Sprint planning and reviews.
5. High perceived challenges is basically stretching your capabilities as a developer.
6. High perceived skills is about you continuously learning and improving.
7. Freedom from distractions means only working on one item at a time.  It also means not being distracted via external factors such as your phone during a lecture!

## Create the Foundations of Our Deployment Pipeline

In this module we are slowly building a deployment pipeline.  In the real world, you would do so at the start of the project.  However, as you are learning in the module, we are taking our time and not necessarily doing things in the best manner to start with.

A key factor we are working on is the use of version control.  We have been submitting almost everything to version control, as this ensures we can recreate the entire production environment from version control.  This is good practice in modern software development.

### Step 1: Enable On-demand Creation of Dev, Test, and Production Environments

We want developers to run production-like environments on their own workstations.

Developers can run and test their code in production-like environments as part of their daily work.

For example, use containers and deploy to the cloud.

### Step 2: Create Our Single Repository of Truth for the Entire System

Ensure all parts of out software system are shared in VCS.

For example, code, database, configuration (Docker), tests, etc.

Not sufficient to recreate previous state; recreate entire build process.

### Step 3: Make Infrastructure Easier to Rebuild than to Repair

Automated configuration systems (e.g., Puppet, Ansible, etc.).

Create new VMs or containers and deploy them, destroying the old ones.

Immutable infrastructure - no manual changes, must be rebuilt from VCS.

### Step 4: Modify our Definition of Development "Done" to Include Running in Production-like Environments

DoD is beyond correct code.

Each development increment:

- Integrated.
- Tested.
- Working and potentially shippable.
- Demonstrated in production-like environment.

Prevents a feature being called done because it ran on a developer's machine and no where else.

## Enable Fast and Reliable Automated Testing

Without automated testing larger code bases cost more to test.  This is unscalable.

Without automate testing, developers become afraid to commit changes.  New team members don't understand, and existing team members understand too well the problems in the system.

From Google's automated testing and integration approach, in 2013 4000 teams of developers were changing 50% of their code per month.  Also:

- 40,000 code commits per day.
- 50,000 builds per day, sometimes up to 90,000.
- 120,000 automated test suites.
- 75 million test cases per day.

### Step 1: Continuously Build, Test, and Integrate our Code and Environments

Build quality into our product at the earliest stage by developers building automated tests as part of daily work.

![Deployment Pipeline](img/deploy-pipeline.png)

Taken from *Continuous Delivery* by Humble and Farley.

Commit Stage builds and packages software, runs unit tests, static analysis, etc.

Acceptance Stage deploys into production-like environment for automated acceptance tests.

Continuous integration practices require three capabilities:

- comprehensive and reliable set of automated tests to validate software is deployable.
- culture to stop the entire production line when validation tests fail.
- developers working in small batches on trunk rather than long-lived feature branches.

### Step 2: Build a Fast and Reliable Automated Validation Test Suite

Three types of automated test:

1. **Unit tests**.
2. **Acceptance tests** to check operates as designed - does what the customer wants.
3. **Integration tests** to check application interacts with other applications and services correctly.

Ten-minute build and test is reasonable for local tests.

### Step 3: Catch Errors as Early in Our Automated Testing as Possible

[![Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid/testPyramid.png)](https://martinfowler.com/articles/practical-test-pyramid.html)

Taken from Martin Fowler, *The Practical Test Pyramid* https://martinfowler.com/articles/practical-test-pyramid.html

- [ ] Read Martin Fowler's post on *The Practical Test Pyramid* for a deeper understanding of test automation.

### Step 4: Ensure Tests Run Quickly (in Parallel if Necessary)

![Parallel Testing Pipeline](img/parallel-testing.png)

Taken from *Continuous Delivery* by Humble and Farley.

### Step 5: Write Our Automated Tests Before We Write the Code ("Test Driven Development")

Begin every change to the system by writing the automated test to test the expected behaviour.  Test fails, and we write code to pass the test.

Three steps of Test-Driven Development:

1. Ensure the test fail.  Write a test for the functionality to add.  Commit.
2. Ensure the test passes.  Write the code to pass the test.  Commit.
3. Refactor old and new code to make it well structured.  Ensure test still passes.  Commit.

### Step 6: Automate as Many of Our Manual Tests as Possible

Having humans executing tests that can be automated is a waste of human potential.

Start with a small number of automated tests and grow them over time, increasing the level of assurance that we can quickly detect changes to the system that break the build.

### Step 7: Integrate Performance Testing into Our Test Suite

Build performance testing environment at the start of the project.

### Step 8: Integrate Non-functional Requirements Testing into Our Test Suite

For example, security, scalability, availability.

Can be managed via correct configuration.

### Step 9: Pull Our Andon Cord When the Deployment Pipeline Breaks

When our deployment pipeline breaks at a minimum we notify the entire team of the failure so anyone can fix the problem or we can rollback the build.

#### Why We Need to Pull the Andon Cord

We end up with an unpredictable "stabilization phase" where the team is doing fixes to get the tests to pass, accumulating technical debt, and effectively back in a waterfall method.

## Enable and Practice Continuous Integration

The longer developers work in isolated branches the more difficult it becomes to integrate and merge everyone together.

If merging code is painful, we will do it less often, making the problem worse over time.

Multiple builds per day.

Multiple commits per day.

1000s new lines of code per day.

### Small Batch Development and What Happens When we Commit Code to Trunk Infrequently

[![Small](https://cdn-images-1.medium.com/max/2000/1*YtshITZLqxYGzfYBHqTZNA.gif)](https://medium.com/@stefanluyten/single-piece-flow-5d2c2bec845b)  Taken from *Single Piece Flow* by Stefan Luyten: https://medium.com/@stefanluyten/single-piece-flow-5d2c2bec845b.

When changes break the build, swarm to bring the deployment pipeline back up.

Spectrum of methods of working with branches:

- **Optimise for individual productivity** - bad as collaboration becomes extremely difficult.  Everyone only sees their own problems.
- **Optimise for team productivity** - better as everyone sees everything.  A single commit can break everything though, and stop progress.

If merging is difficult, we don't do it.  Then we don't do refactoring work to improve code quality.  This leads to an ongoing build-up of technical debt.

A lack of refactoring means normal changes become difficult over time, slowing down the rate of new feature development.

### Adopt Trunk-based Development Practices

All developers commit to `develop` at least once per-day.

Reduces batch size to the work of a developer per day.

More frequent check-ins lead to smaller batch sizes and better single-piece flow.

Can have *gated commits* - if the commit breaks deployment then reject it.

DoD becomes:

At the end of each development interval, we must have integrated, tested, working, and potentially shippable code, demonstrated in a production-like environment, created from develop using a one-click process, and validated with automated tests.

## Automate and Enable Low-risk Releases

[![Developers Deploying Per Week at Facebook](https://scontent.flhr4-1.fna.fbcdn.net/v/t1.0-9/418740_10151076511697200_122890827_n.jpg?_nc_cat=108&_nc_ht=scontent.flhr4-1.fna&oh=7bbd9b4ca7e32135b2cae9c777c3ab65&oe=5CBC8A57)](https://www.facebook.com/notes/facebook-engineering/ship-early-and-ship-twice-as-often/10150985860363920/)

Taken from *Ship Early and Ship Twice as Often*: https://www.facebook.com/notes/facebook-engineering/ship-early-and-ship-twice-as-often/10150985860363920/

### Step 1: Automate Our Deployment Process

Fully document the steps in the deployment process.

Simplify and automate manual steps:

- Packaging code for deployment.
- Creating virtual machines and containers.
- Deployment of middleware.
- Copying to production servers.
- Restarting servers, applications, or services.
- Generating configuration files from templates.
- Running test procedures.

Deployment pipeline should:

- Deploy the same to every environment.
- Smoke test (sanity check core functionality) our deployments.
- Ensure environments are consistent.

### Step 2: Enable Automated Self-service Deployments

Developers can commit and it appears directly in deployment.

Affects following stages:

- **Build** - create packages from version control to deploy.
- **Test** - anyone able to run test suite.
- **Deploy** - execute script in version control.

### Step 3: Integrate Code Deployment into the Deployment Pipeline

Ensure packages created during continuous integration are suitable for deployment.

Show readiness of production environments at a glance.

Provide push-button, self-service deployment.

Record automatically which commands were run when, where, and by who.

Run smoke test on deployment machine to ensure everything is correct.

Provide fast-feedback so developers know if deploy was successful.

### Step 4: Decouple Deployments from Releases

Deployment is the installation of a specified version of the software.

Release is a feature (or set of features) made available.

#### Environment-based Release Patterns

![Blue-Green Deployment Pattern](img/blue-green.png)

Database can follow blue-green, or decouple database from application change.

Deploy to internal, then sub-set of users, then full-deployment (Canary Pattern)

#### Application-based  Release Patterns

Feature toggles.

Dark launches.

## Architecture

We covered [modern software architecture in Lecture 05](../lecture05).  Microservice architectures enable small batch sizes, thus supporting flow.

## Summary

## Further Reading