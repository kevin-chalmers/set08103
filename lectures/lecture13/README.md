# Lecture 13: The Second Way of DevOps - Feedback

## Behavioural Objectives

## Create Telemetry to Enable Seeing and Solving Problems

> In operations, we may deal with this problem with the following rule of thumb: When something goes wrong in production, we just reboot the server.  If that doesn't work, reboot the server next to it.  If that doesn't work, reboot all the servers.  If that doesn't work, blame the developers, they're always causing outages.
>
> - The DevOps Handbook

Organisations with higher service levels reboot servers 20% less often.

Use telemetry to understand contributing factors.

To enable problem-solving our systems need to continuously provide telemetry.

Telemetry - an automated communications process by which measurements and other data are collected at remote points and are subsequently transmitted to receiving equipment for monitoring.

Need to create telemetry in our applications and environments, both production and pre-production.

Developers should add telemetry to their features as part of daily work to make deployments safe.

### Create Our Centralised Telemetry infrastructure

More than logs that are useful to developers, or system status that is interesting to operations.

We must design and develop our applications and environments so that they generate sufficient telemetry  allowing us to understand how our system is behaving as a whole.  We enable capabilities such as graphing and visualising metrics, anomaly detection, proactive alerting and escalation, etc.

Telemetry architecture has the following components:

- Data collection at the business logic, application, and environments layer.
- An event router responsible for storing our events and metrics.

The aim is to transform logs into metrics.  This allows statistical analysis to, for example, detect anomalies.  Instead of *SQL query failed* we get *10 SQL query fails per week*.

We also need information from deployment.  How long to build.  How long to test.  etc.

Ideally we should have APIs to allow easy access to the telemetry data.

### Create Application Logging Telemetry That Helps Production



### Use Telemetry to Guide Problem-solving

### Enable Creation of Production Metrics as Part of Daily Work

### Create Self-service Access to Telemetry and Information Radiators

### Find and Fill Ant Telemetry Gaps

## Analyse Telemetry to Better Anticipate Problems and Achieve Goals

### Use Means and Standard Deviations to Detect Potential Problems

### Instrument and Alert on Undesired Outcomes

### Problems that Arise When Our Telemetry Data Has Non-Gaussian Distribution

### Using Anomaly Detection Techniques

## Enable Feedback So Development and Operations Can Safely Deploy Code

### Use Telemetry to Make Deployments Safer

### Dev Shares Pager Rotation Duties With Ops

### Have Developers Follow Work Downstream

### Have Developers Initially Self-manage Their Production Service

## Integrate Hypothesis-Driven Development and A/B Testing into Our Daily Work

### A Brief History of A/B Testing

### Integrate A/B Testing into Our Feature Testing

### Integrate A/B Testing into Our Release

### Integrating A/B Testing into Our Feature Planning

## Create Review and Coordination Processes to Increase Quality of Or Current Work

### The Dangers of Change Approval Processes

### Potential Dangers of "Overly Controlling Changes"

### Enable Coordination and Scheduling of Changes

### Enable Peer Review of Changes

### Potential Dangers of Doing More Manual Testing and Change Freezes

### Enable Pair Programming to Improve All Our Changes

### Fearlessly Cut Bureaucratic Processes

## Summary

## Recommended Reading