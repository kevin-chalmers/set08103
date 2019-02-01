# Lecture 07: The First Way of DevOps - Flow

## Behavioural Objectives

## The Psychology of Flow

<p><a href="https://commons.wikimedia.org/wiki/File:Challenge_vs_skill.svg#/media/File:Challenge_vs_skill.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Challenge_vs_skill.svg/400px-Challenge_vs_skill.svg.png" alt="Challenge vs skill.svg"></a><br>By <a href="https://en.wikipedia.org/wiki/User:Oliverbeatson" class="extiw" title="w:User:Oliverbeatson">w:User:Oliverbeatson</a> - <a href="https://en.wikipedia.org/wiki/File:Challenge_vs_skill.jpg" class="extiw" title="w:File:Challenge vs skill.jpg">w:File:Challenge vs skill.jpg</a>, Public Domain, <a href="https://commons.wikimedia.org/w/index.php?curid=9102943">Link</a></p>

## Create the Foundations of Our Deployment Pipeline

Our goal is to ensure we can recreate the entire production environment from version control.

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

Build quality 

### Step 2: Build a Fast and Reliable Automated Validation Test Suite

### Step 3: Catch Errors as Early in Our Automated Testing as Possible

### Step 4: Ensure Tests Run Quickly (in Parallel if Necessary)

### Step 5: Write Our Automated Tests Before We Write the Code ("Test Driven Development")

### Step 6: Automate as Many of Our Manual Tests as Possible

### Step 7: Integrate Performance Testing into Our Test Suite

### Step 8: Integrate Non-functional Requirements Testing into Our Test Suite

### Step 9: Pull Our Andon Cord When the Deployment Pipeline Breaks

#### Why We Need to Pull the Andon Cord

## Enable and Practice Continuous Integration

### Small Batch Development and What Happens When we Commit Code to Trunk Infrequently

### Adopt Trunk-based Development Practices

## Automate and Enable Low-risk Releases

### Step 1: Automate Our Deployment Process

### Step 2: Enable Automated Self-service Deployments

### Step 3: Integrate Code Deployment into the Deployment Pipeline

### Step 4: Decouple Deployments from Releases

### Environment-based Release Patterns

### Application-based Release Patterns to Enable Safer Releases

## Architect for Low-risk Releases

### An Architecture that Enables Productivity, Testability, and Safety

### Architectural Archetypes: Monliths vs. Microservices

### Use the Strangler Application Pattern to Safely Evove Our Enterprise Application

## Summary

## Further Reading