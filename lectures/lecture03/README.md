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
- [ ] 

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

- [**Git**](https://git-scm.com/) which is commonly associated with popular repository sites such as [**GitHub**](https://github.com/), [**GitLab**](https://about.gitlab.com/), and [**Bitbucket**](https://bitbucket.org/).  Git is independant of these platforms and should not be confused with them.
- [**Mercurial**](https://www.mercurial-scm.org/) is a popular alternative to Git, and developed as a replacement for *BitKeeper* which itself led to the development of Git.  The history of why BitKeeper is not popular and led to both Git and Mercurial is [interesting](https://en.wikipedia.org/wiki/BitKeeper).
- [**Subversion (SVN)**](https://subversion.apache.org/) which is an *Apache* project that derived from an older tool called *Concurrent Versions System (CVS)*.
- [**Visual SourceSafe**](https://msdn.microsoft.com/en-us/library/ms181038(v=vs.80).aspx) and [**Visual Studio Team Services**](https://visualstudio.microsoft.com/team-services/) are both Microsoft products, although the latter can use Git as a backend.

### Version Control Approaches

There are three approaches a Version Control System (VCS) can take:

- **Localised**, which means developers must be working on the same filesystem.  These were early approaches and no longer relevant today.
- **Client-server** where multiple developers (*clients*) can work locally and push changes to a single server repository.
- **Distributed** where the complete codebase and history is stored by each developer locally, thus replicating the repository.  Developers can collaborate via remote repositories - such as on GitHub.

Of the tools mentioned above:

- *SVN*, *Visual SourceSafe*, and *Visual Studio Team Services* are client-server based.
- *Git*, *Mercurial*, and *Visual Studio Team Services* are distributed based (yes VSTS can be either).

### Some Terminology

Before looking at the history of version control let us define some common terms in a VCS:

- **Repository** is where the code and history is stored.  In a *client-server* model this is on the server.  In a *distributed* model this is any local version.
- **Checkout** or **clone** is the process of getting a copy of the code from the repository.  In a *client-server* model, we *checkout* the code.  In a *distributed* model, we *clone* the entire repository, including the history.
- **Working copy** is the local version of the codebase.  We can make any changes we want to the working copy as it is not reflected anywhere else - it is a sandbox.
- **Fetch** or **pull** is to get the most recent version of the codebase from the remote repository.  In *Git*, *fetch* and *pull* are different in that pull will also merge any changes into the local working copy.
- **Push** is when we push our local changes to the remote repository.  To do this we have to create a commit.
- **Commit** is a new version of the codebase.  Typically a commit contains the changes added in the local *working copy* which can then be sent to the remote repository if need be.  In *distributed* models, working copies are repositories, so we can undertake numerous commits before pushing all the changes to the remote repository.
- **Tag** or **label** is extra information we can add to a particular commit, such as `v0.1.0`.
- **Head** is a special *tag* or *label* for the most recent *commit* on a *branch*.
- **Branch** is another version of the codebase.  Branches are independant, meaning they can be worked on without causing conflicts.  We *merge* branches when we wish to synchronise them.
- **Master** or **trunk** is the name of the main *branch* in a repository.  Git uses the term *master* and SVN uses the term *trunk*.
- **Merge** is the process of combining one *branch* into another.  Any differences between files in the branches have to be resolved before the merge can be completed.
- **Conflict** occurs when different change versions of the same document exist while merging branches which must be fixed.
- **Resolve** is the process of fixing *clonflicts*.  There are tools that can support this process, but it does require human intervention.

## History of Version Control

## What is Git?

## Principles of Git

## Teminology of Git

## Summary