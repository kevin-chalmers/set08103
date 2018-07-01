# Lab 01: Setup

## IntelliJ Setup

Create a new Maven project.  If necessary add new SDK.

GroupID: com.napier.sem

ArtefactID: seMethods

Version: 0.1.0.1 (0.1-alpha-1)

## Git with IntelliJ

Select VCS, enable VCS integration

Select Git -> OK

Ass .gitignor file, select yes to add to Git.

Go to Java .gitignore and paste in

Add .idea

Add README.md and add to Git

Create a repo on GitHub

- SET08103, public
- Add a license Apache 2.0
- No README

Add remote to IntelliJ

- VCS, Git, Remotes
- (+ add)
- Name origin, URL, as from Git
- Start ssh-agent.cmd
- Have .ssh folder

Pull

- Select origin, just default
- Should now have a license file

Add files - VCS->Git->Add

Commit

- VCS->commit
- Message "First commit, adding initial files"
- Set, another
- Commit

Push - VCS->Git->Push

Check GitHub

## Hello World Sanity Check

Add package com.napier.sem

Add class App

Select Yes to add to Git

Enter code

Select Build->Run

If OK, VCS->Git->Add, VCS->Commit, VCS->Git->Push

## Create Dockerhub Account

