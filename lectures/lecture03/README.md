# Lecture 03: Version Control and Git

## Reminder - Our Learning Environment

1. Toyota Improvement Kata:
    1. In consideration of the outcomes of your education...
    2. Grasp your current level of knowledge and understanding.
    3. Define what you want to learn next - e.g. the ideas in this module.
    4. Move toward that target level iteratively, which will uncover areas you don't know that need to be worked on.
2. Ideas from the book *A Mind for Numbers*:
    - We let ourselves get too distracted or too engaged with multiple attentional things to think deeply (focused), for example using your phone or laptop during a lecture.
    - We fool ourselves into thinking that following and copying is the same as understanding - related to *ego is the enemy*.
    - We think focused attention is all we need and fail to use diffuse thinking
3. An industry perspective - *Meeting Norms at Skyscanner*:
    - **Be present** both physically and mentally.
    - **Ask why** to me and yourself.
    - **All voices are equal**.
    - **Listen actively** which normally means close your laptop - take written notes instead.
    - **Don't call people resources** which is more about the work place than studying, but keep it in mind when working in teams.
    - And one addition from me - remember that **ego is the enemy**.
4. Ideas from Lean and Continuous Improvement:
    - **Respect for people** supports **continuous improvement**.
    - **Continuous improvement** does not in itself support **respect for people**.
    - **Education is not a competition** - better learning comes from cooperation.

## Behavioural Objectives

At the end of this lecture you will be able to:

- [ ] **Define** what *version control is*.
- [ ] **Describe** the *key differences* between *client-server* and *distributed VCS*.
- [ ] **Define** what *Git is*.

## What is Version Control?

Version control is about the management of changes to documents or collections of information.  Although you might think of version control as an inherently software development tool, it can be used for anything really.  From a software development perspective, version control is a component of **Software Configuration Management (SCM)**.  Git's main website has the address [https://git-scm.com/](https://git-scm.com/) as it is a part of SCM.

Version control is embedded in a number of tools.  For example, Google Docs automatically versions your document as you make edits:

![Google Doc Versioning](img/google-doc-version.png)

Track changes and similar functionality exists in Microsoft Word.  The key point is that version management is seen as a key feature of documents in general, not just software.  It allows two key pieces of meta-data to be tracked:

1. **When** a change was made.
2. **Who** made the change.

Both pieces of information allow us to track back to where problems arose, and know where to fix the issue.  When working in a team this information can be fundamental to ensure everyone is working on the same version of the document, or at least know which changes have been made between different working versions.

Another key idea in version control is that we can return to previous versions of our document.  Therefore, if we make an error (e.g. add a bug) we can **rewind** to the previous version - or any previous version - and continue our work from there:

![Version Control Rewind](img/rewind.png)

A further idea is the concept of working and managing multiple versions of the document using a concept called **branching**.  Different branches allow different versions of the information to be worked on discretely by several people.  When work needs to be combined we can **merge** the information together into one of the branches:

<p><a href="https://commons.wikimedia.org/wiki/File:Revision_controlled_project_visualization-2010-24-02.svg#/media/File:Revision_controlled_project_visualization-2010-24-02.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Revision_controlled_project_visualization-2010-24-02.svg/1200px-Revision_controlled_project_visualization-2010-24-02.svg.png" alt="Revision controlled project visualization-2010-24-02.svg"></a><br>By <a href="//commons.wikimedia.org/wiki/File:Revision_controlled_project_visualization.svg" title="File:Revision controlled project visualization.svg">Revision_controlled_project_visualization.svg</a>: *<a href="//commons.wikimedia.org/wiki/File:Subversion_project_visualization.svg" title="File:Subversion project visualization.svg">Subversion_project_visualization.svg</a>: Traced by <a href="//commons.wikimedia.org/wiki/User:Stannered" title="User:Stannered">User:Stannered</a>, original by <a href="https://en.wikipedia.org/wiki/User:Sami_Kerola" class="extiw" title="en:User:Sami Kerola">en:User:Sami Kerola</a>
derivative work: <a href="//commons.wikimedia.org/wiki/User:Moxfyre" title="User:Moxfyre">Moxfyre</a> (<a href="//commons.wikimedia.org/wiki/User_talk:Moxfyre" title="User talk:Moxfyre"><span class="signature-talk">talk</span></a>)
derivative work: <a href="//commons.wikimedia.org/w/index.php?title=User:Echion2&amp;action=edit&amp;redlink=1" class="new" title="User:Echion2 (page does not exist)">Echion2</a> (<a href="//commons.wikimedia.org/wiki/User_talk:Echion2" title="User talk:Echion2"><span class="signature-talk">talk</span></a>) - <a href="//commons.wikimedia.org/wiki/File:Revision_controlled_project_visualization.svg" title="File:Revision controlled project visualization.svg">Revision_controlled_project_visualization.svg</a>, <a href="http://creativecommons.org/licenses/by-sa/3.0/" title="Creative Commons Attribution-Share Alike 3.0">CC BY-SA 3.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=9562807">Link</a></p>

### Popular Version Control Tools

There are many version control tools available to the software engineer.  A few of the more popular ones are:

- [**Git**](https://git-scm.com/) which is commonly associated with popular repository sites such as [**GitHub**](https://github.com/), [**GitLab**](https://about.gitlab.com/), and [**Bitbucket**](https://bitbucket.org/).  Git is independent of these platforms and should not be confused with them.
- [**Mercurial**](https://www.mercurial-scm.org/) is a popular alternative to Git, and developed as a replacement for *BitKeeper* which itself led to the development of Git.  The history of why BitKeeper is not popular and led to both Git and Mercurial is [interesting](https://en.wikipedia.org/wiki/BitKeeper).  Mercurial, although less well known, is used by big organisations such as Facebook and Mozilla.
- [**Subversion (SVN)**](https://subversion.apache.org/) which is an *Apache* project that derived from an older tool called *Concurrent Versions System (CVS)*.
- [**Visual SourceSafe**](https://msdn.microsoft.com/en-us/library/ms181038(v=vs.80).aspx) and [**Visual Studio Team Services**](https://visualstudio.microsoft.com/team-services/) are both Microsoft products, although the latter can use Git as a back-end.  *SourceSafe* has had no major releases since 2005, and support was ended in 2017.

### Version Control Approaches

There are three approaches a Version Control System (VCS) can take:

- **Localised**, which means developers must be working on the same file-system.  These were early approaches and no longer relevant today.
- **Client-server** where multiple developers (*clients*) can work locally and push changes to a single server repository.
- **Distributed** where the complete code-base and history is stored by each developer locally, thus replicating the repository.  Developers can collaborate via remote repositories - such as on GitHub.

Of the tools mentioned above:

- *SVN*, *Visual SourceSafe*, and *Visual Studio Team Services* are client-server based.
- *Git*, *Mercurial*, and *Visual Studio Team Services* are distributed based (yes VSTS can be either).

### Some Terminology

Before looking at the history of version control let us define some common terms in a VCS:

- **Repository** is where the code and history is stored.  In a *client-server* model this is on the server.  In a *distributed* model this is any local version.
- **Checkout** or **clone** is the process of getting a copy of the code from the repository.  In a *client-server* model, we *checkout* the code.  In a *distributed* model, we *clone* the entire repository, including the history.
- **Working copy** is the local version of the code-base.  We can make any changes we want to the working copy as it is not reflected anywhere else - it is a sandbox.
- **Fetch** or **pull** is to get the most recent version of the code-base from the remote repository.  In *Git*, *fetch* and *pull* are different in that pull will also merge any changes into the local working copy.
- **Push** is when we push our local changes to the remote repository.  To do this we have to create a commit.
- **Commit** is a new version of the code-base.  Typically a commit contains the changes added in the local *working copy* which can then be sent to the remote repository if need be.  In *distributed* models, working copies are repositories, so we can undertake numerous commits before pushing all the changes to the remote repository.
- **Tag** or **label** is extra information we can add to a particular commit, such as `v0.1.0`.
- **Head** is a special *tag* or *label* for the most recent *commit* on a *branch*.
- **Branch** is another version of the code-base.  Branches are independent, meaning they can be worked on without causing conflicts.  We *merge* branches when we wish to synchronise them.
- **Master** or **trunk** is the name of the main *branch* in a repository.  Git uses the term *master* and SVN uses the term *trunk*.
- **Merge** is the process of combining one *branch* into another.  Any differences between files in the branches have to be resolved before the merge can be completed.
- **Conflict** occurs when different change versions of the same document exist while merging branches which must be fixed.
- **Resolve** is the process of fixing *conflicts*.  There are tools that can support this process, but it does require human intervention.

## History of Version Control

Version control of documents has been around almost as long as writing.  For code, version control likely had primitive approaches in the early days, but the the 1970s is where work seen to begin:

- **1972** *Source Code Control System* developed at Bell Labs - aimed at single mainframe code access model that was prevalent at the time.
- **1977** *SCCS* given general release.
- **1982** *Revision Control System (RCS)* introduced as an alternative to *SCCS*.
- **1986** Original version of *Concurrent Versions Control (CVS)* released as a series of shell scripts as a front-end to *RCS*.
- **1990** *CVS* 1.0 released as a separate tool.
- **1994** *SourceSafe* is bought by Microsoft from One Tree Software.
- **1998** *BitKeeper* first mentioned as a solution to managing the Linux kernel source.
- **1999** *SourceForge* launched - one of the first major web-based code repository platforms or **forges**.
- **2000** 
    - *Subversion (SVN)* released as a generally compatible successor to *CVS*.  
    - *BitKeeper* launched.
- **2002** Linux kernel development moved to *BitKeeper* - this was controversial as BitKeeper was proprietary.
- **2005** 
    - Microsoft release *Team Foundation Server* which includes source code management.  
    - Last major version of *Visual SourceSafe* released.  
    - *BitKeeper* becomes commercially licensed - the **BitKeeper Controversy**.
    - Linus Torvalds releases *Git* to overcome the *BitKeeper Controversy*.
    - *Mercurial* is created in response to the *BitKeeper Controversy*.
- **2006** 
    - Google launch *Google Code Project Hosting* which supports *Subversion*, *Git* and *Mercurial*.
    - Microsoft launch *CodePlex* which supports *Team Foundation Services*, *Subversion*, *Mercurial*, and *Git*.
- **2008** 
    - *GitHub* launches.
    - *Bitbucket* launches originally only supporting *Mercurial* but adds *Git* in 2011.
- **2011** *GitLab* launches.
- **2013** Microsoft launches *Visual Studio Team Services* (originally named *Visual Studio Online*) as an Internet service version of *Team Foundation Server*.
- **2016** 
    - *BitKeeper* moves to an open-source license.
    - *Google Code Project Hosting* shuts down.
- **2017** Microsoft closes *CodePlex*.
- **2018** Microsoft buys *GitHub* - *Git* seen as the major VCS for Microsoft.

As you can see, the 1990s was were version control started to take off, but it was in the 2000s where modern tooling emerged.  The nexus point in 2005 is particularly interesting due to the *BitKeeper Controversy* and managing the development of the Linux kernel.  This module will work using *Git* and using *GitHub* as our *forge*.

## What is Git?

Git is a **distributed VCS** where developers clone a complete copy of the repository, including its history, within the local file system.  Born from the *BitKeeper Controversy*, Linus Torvalds wanted a system that was fast.  He used three points to drive the design of Git:

1. See Concurrent Versions System (CVS) as the model of what **not** to do.
2. Support a distributed workflow, as in BitKeeper.
3. Have strong safeguards against corruption.

So, Git has the following properties:

1. It is fast.
2. It has data integrity features.
3. It is distributed, thus supporting non-linear workflows.

Git is likely the most popular and well known VCS at the moment, although this is partly due to the popularity of GitHub.  The two are often confused, but there is no link between the two beyond GitHub supporting Git repositories.

Let us move onto the principles of Git, which will provide a deeper understanding of how Git works.

## Principles of Git

The following section will step through numerous principles in Git with the relevant commands.  We will look at the basics of repositories, basic workflow for submitting changes, the basic workflow for fetching and merging changes, and the basics of branching.

### Working with Repositories

Git works with *repositories*.  A repository is the code and history of a code-base.  Every time you work with Git you are working within a repository: your local repository.  You may also work with some remote repositories.  That is a key idea with Git - your local machine working copy is also a repository.

You can create your local repository in one of two ways:

1. Initialise an empty repository using `git init` in a folder.
2. Call `git clone <url>` to clone an existing repository from a remote repository as shown below:

![Git Clone](img/git-clone.png)

When you *clone* a repository you also set up a link to the remote repository called `origin`.  We will discuss [remotes later](#Remotes).

There is a special version of empty initialisation: `git init --bare`.  This is usually used on a server that is used to coordinate teams.  In general, you should *not* use `git init --bare`.

### Working with Changes

A Git repository is a folder which contains a hidden folder (`.git`).  The hidden folder contains the history and other status information of the repository.  Otherwise, the repository just looks like a folder - there is nothing extra managed.

Whenever you add, remove or edit a file in the repository, Git can tell based on the information in the hidden `.git` folder.  Any changes at this point are not saved by Git.  To save the changes, we have to go through two steps:

1. **Add** the changes we want to save at this point.
2. **Commit** the changes to the repository.
3. (optional) **Push** the changes to the remote(s).

#### Adding Changes

Before step 1 (adding changes) we are in a working files state.  We are editing files and working on our code but not ready to store the changes long term.  This is usually because we are not finished whatever change we have in mind.

Once we are ready to add the changes we can use the following command:

```shell
git add <filename>
```

We can name each file individually, name a folder, or use a wildcard (e.g., `git add *`).  In any case, we have moved changes from the working area to the **staging area**.

We can see files that are different from the currently Git version or staged using the following command:

```shell
git status
```

`git status` is useful for keeping track of the work we are doing.  You should use it often to remind yourself what you are doing.

Once we have added all the changes we want for a particular feature/task, we create a **commit**.

#### Committing Changes

A **commit** is just a group of changes.  A commit operation takes the changes currently in the staging area and creates a new **snapshot** of our code at this point.  Git stores this snapshot in its history.  To create a commit, we use the following:

```shell
git commit -m "<message>"
```

The `message` should be informative about what the changes are.  A `message` should ideally be simple and to the point (e.g., do not use the word *and* if you can avoid it).  The messages allow others to see the changes made and (hopefully) why, thus providing more information to your fellow software developers.

A commit is a store piece of history, and Git keeps track of all the history in a repository.  This actually has an advantage - *you can ask Git to go back to a previous version*.  In simple terms, Git provides you with a big rewind button that allows you to go back to previous versions of your code, so as advice:

- Create commits often, from simple little changes that don't break the build.
- Experiment in the comfort that you can always go back to a previous working version of your application.

The big idea is to **commit often**.  Commits allow you to **checkout** a previous commit if anything goes wrong.  *But always ensure your commit works!*

#### Pushing Changes

Any commit created on your machine is only stored locally.  So, although you have been keeping a good record of your changes locally, they can not be seen by others.  Your changes have also not been stored on a remote server.  To do this, we use the `git push` command:

```shell
git push
```

`git push` will push the current branch (e.g., `master`) to the current remote (normally `origin`).  You can be more explicit with a push:

```shell
git push <remote> <branch>
```

For example, it is common to see `git push origin master`.  This will push your local version of branch `master` to the `origin` remote.

There are other options with `git push` such as:

- `git push --force` forces your local branch version to become the remote's.  **Not recommended!**
- `git push --all` pushes updates to all local branches to the remote.  Useful shortcut if needed.

#### Diffs

Git keeps track of history by storing the *differences* between files.  We can simplify a difference to four types:

1. The addition of a new file and its initial contents.
2. The removal of a file.
3. The addition of new lines to a file.
4. The removal of lines from a file.

If you edit a line it is considered a new line addition and the old line being removed.  To see the changes made, we can use the `git diff` command:

![Git Difference Between Two Files](img/diff.png)

As Git tracks changes as line additions and removals, it is very good at monitoring text files (such as code files).  It is very bad at binary data such as executables and images.  A couple of rules:

- **Do not store executables in your Git repository** - even those built by the project.
- **Be careful when working with media files** - only store versions that will not change.

The `.git` folder contains all the changes, and so a repository can become large if you do not behave yourself.  If your repository becomes many megabytes in size you are probably tracking something you shouldn't.

#### Going Backwards

### Fetching and Merging Changes

#### Managing Conflicts

### Branching

### Remotes

### Ignoring Files

### A Primitive Git Workflow

1. Modify files to make a working change.
2. Add changes to the staging area with `git add`.
3. Create a commit from the changes with `git commit`.
4. Send the changes to the remote with `git push`.

### Summary

<p><a href="https://commons.wikimedia.org/wiki/File:Git_operations.svg#/media/File:Git_operations.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d8/Git_operations.svg/1200px-Git_operations.svg.png" alt="Git operations.svg"></a><br>By <a href="//commons.wikimedia.org/wiki/User:Duesentrieb" title="User:Duesentrieb">Daniel Kinzler</a> - <span class="int-own-work" lang="en">Own work</span>, <a href="https://creativecommons.org/licenses/by/3.0" title="Creative Commons Attribution 3.0">CC BY 3.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=25223536">Link</a></p>

## Teminology of Git

## Gitflow Workflow / Collaboration Model

## Summary