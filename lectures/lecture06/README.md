# Lecture 06: The Three Ways - Underpinning Principles of DevOps

In this lecture we will explore the key principles of DevOps and how these are mapped to the work in the rest of the module.  DevOps, and the culture surrounding it, has become a desirable trend for graduates.  In this module we skate over the principles with a software engineering lens.  The principles you will find are similar to ones already discussed in the module.

## Behavioural Objectives

- [ ] TODO

## Overview of DevOps

DevOps tries to address the boundary between the developers (the creators of software) and operations (the management of software).  DevOps is a set of principles and techniques that enable improved working between these two groups, driven by a number of the ideas we have already presented in this module:

- The Lean Movement (we covered [Lean Software Development in Lecture 04](../lecture04)).
- The Agile Manifesto (we covered [Agile in Lecture 01](../lecture01)).
- Agile Infrastructure and Velocity Movement ([modern software architectures in Lecture 05](../lecture05) is related to this idea).
- The Continuous Delivery Movement (we cover [Continuous Delivery in Lecture 16](../lecture16)).
- The Toyota Kata - which is about continuous improvement.

In [Lecture 05](../lecture05) we examined modern software architecture.  The following table summarises how these trends have affected business practices.

|       | **1970s-1980s** | **1990s** | **2000s-Present** |
|-------|-----------------|-----------|-------------------|
| **Era** | Mainframes | Client/server | Cloud |
| **Technology** | COBOL, DB2 | C++, Oracle | Java, MySQL, etc. |
| **Cycle time** | 1-5 years | 3-12 months | 2-12 weeks |
| **Cost** | $1M-$100M | $100k-$10M | $10k-$1M |
| **At risk** | The whole company | Product line or division | Product feature |
| **Cost of failure** | Bankruptcy | Revenue miss | Negligible |

This is taken from Adrian Cockcroft's talk *Velocity and Volume (or Speed Wins)* which you can watch below.  Adrian was Cloud Architect at Netflix at the time, and is now Vice President for Cloud Architecture Strategy at Amazon Web Services.

[![Velocity and Volume (or Speed Wins)](https://img.youtube.com/vi/wyWI3gLpB8o/0.jpg)](https://www.youtube.com/watch?v=wyWI3gLpB8o)

These forces has led to two conflicting goals in IT organisations:

- Respond to the rapidly changing competitive landscape.
- Provide stable, reliable, and secure service to the customer.

### An Example

Why is this a problem?  Let us consider an abstract scenario in an IT business (adapted from *The DevOps Manual*).

First, our applications and infrastructure can become fragile over time.  This is due to system complexity, poor documentation, and work arounds being used.  **Technical debt** (where quick and easy solutions lead to long-term problems) means that systems get into a mess.  Operations promise to fix the problems, but the costs is prohibitive.  Any change is also considered dangerous as it may break the system.

Then bigger promises are made.

![The Three Ways of DevOps](img/three-ways.jpg)

## The First Way of DevOps: The Principles of Flow

### Make Work Visible

### Limit Work in Progress (WiP)

### Reduce Batch Sizes

### Reduce the Number of Handoffs

### Continually Identify and Elevate Our Constraints

### Eliminate Waste in the Value Stream

## The Second Way of DevOps: The Principles of Feedback

### Working Safely with Complex Systems

### See Problems as They Occur

### Swarm and Solve Problems to Build New Knowledge

### Keep Pushing Quality Closer to the Source

### Enable Optimising for Downstream Work Centres

## The Third Way of DevOps: The Principles of Continual Learning and Experimentation

### Enabling Organisational Learning and a Safety Culture

### Institutionalise the Improvement of Daily Work

### Transform Local Discoveries into Global Improvements

### Inject Resilience Patterns into Our Daily Work

### Leaders Reinforce a Learning Culture

## Mapping the Module

So far we have covered the following topics in the module:

- Lecture 1: Introduction.
- Lecture 2: Scrum.
- Lecture 3: Version Control.
- Lecture 4: Lean Software Development.
- Lecture 5: Modern Software Architecture.
- Lecture 6: Introduction to DevOps.

The rest of the module is influenced by the three ways:

- The First Way: Flow.
  - Lecture 7: The First Way of DevOps: Flow.
  - Lecture 8: Kanban.
  - Lecture 9: Requirements Gathering.
  - Lecture 10: Use Cases and User Stories.
  - Lecture 11: UML Diagrams.
  - Lecture 12: UML Workflow.
- The Second Way: Feedback.
  - Lecture 13: The Second Way of DevOps: Feedback.
  - Lecture 14: Unit Testing and Test Driven Development.
  - Lecture 15: Continuous Integration.
  - Lecture 16: Continuous Delivery.
  - Lecture 17: Deploying Software.
  - Lecture 18: Monitoring Software.
  - Lecture 19: Bug Tracking.
- The Third Way: Continual Learning and Experimentation.
  - Lecture 20: The Third Way of DevOps: Continual Learning and Experimentation.

We then finish the module with more professional concerns:

- Lecture 21: Ethics and Professionalism.
- Lecture 22: Legal Issues.
- Lecture 23: Security Concerns.

The mapping is loose and based on our need to cover methods and develop our application.  However, being aware of the three principles is important as we go through the rest of the module:

- Flow.
- Feedback.
- Continual Learning and Experimentation.

## Summary

## Further Reading

The goto book on DevOps if *The DevOps Handbook: How to Create World-class Agility, Reliability & Security in Technology Organisations* by Gene Kim, Jez Humble, Patrick Debois, and John Willis.

![The DevOps Handbook](img/devops-book.jpg)

If you like reading novels and would like a story introduction to DevOps and the culture, then *The Pheonix Project* by Gene Kim, Kevin Bahr, and George Spafford might be a good starting place.

![The Phoenix Project](img/phoenix-project-book.jpg)