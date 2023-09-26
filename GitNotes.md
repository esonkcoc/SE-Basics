# Git Notes

Programming produces four actions that result in changes to a codebase:
1. Creating,
2. Modifying,
3. Checking the status of,
4. And deleting files

A **version control system**, like Git, tracks codebase changes, such as the operations performed on the objects that comprise it.

## Git

Git is a version control system that seed, data integreity and suort for non-linear workflows.  
Git provides answers to the following questions to anyone with access to the Git repository (repo):

- What files exist in the codebase?
- Of those files, which ones comrise the lastest version of the codebase?
- Which files have been modified but not saved?
- Which have been saved but not shared with the team?
- What are the changes that led to a particular file looking the way it does?
- What alternative versions of the file are there?
- Who has edited a given file and when?

## Git Workflow

There's no single valid workflow but there are more Git-typical ones that fully leverage its distributed and dynamic capablities. For local repositories there is *pretty much* one way to use Git.  
That is:

1. Create files or perform changes.
2. Collect one or more of the changes performed in a unit called a **commit**.
3. Save that set of changes to the history of a givn development line.
4. Make changes available to others.

## Setup

1. Initialise the repo.
2. Configuer the repo.
3. Create the initial line of development in the repo.

These steps are also the *usual* life cycle of a given files when working with Git locally. They are usually only performed once.

## Git File Life Cycle

Ostensibly, Git tracks files, performs changes and takes 'snapshots',known as **commits**, of a codebase at the point said changes are saved.

Once a file has been introduced to a Git repo, it exists as **untracked**; Git is not tracking changes made to it. To track file changes, issue the command `git add newfile`. Git now *knows* to track **newfile**, as issuing `git add newfile` instructed it to add **newfile** to a list of codebase changes. If another file were added, **newfile2**, that too would be added to the list of codebase changes. After grouping several codebase changes in a single list, known as the **stage** or **index**, they can be saved into the current version of the codebase. A change or group of changes prepared for storeage in this way is known to have been **staged**. **Staging** allows you to selectively choose which changes to **commit** while keeping other changes availble for modifications.The act of saving such changes is **committing** and results in the creation of a unit known as a **commit** in a project's history.

A file's current state, saved in a project's history, is deemed **unmodified** and requires no further action. At this point, the file can be removed or edited. If removed from the repo, it returns to being **untracked** and will require **committing** again. If edited, it is now deemed **modified**, meaning its current state differs from that of version **commited** to the projects's history. It too can then be **staged** and **committed**

![The Git file life cycle](<Screenshot 2023-09-25 at 19.14.56.png>)

## Glossary

- **User**: That which erforms actions upon a codebase or other artifacts related to or being tracked by Git.
- **Working Tree**: The contents of the **directory** where a Git repo has been initialised.
- **Repo**: Any directory that has been initialised as a Git repo. A repo develops from being ostensibly empty to a compilation of **branches**, i.e., lines of development, and **commits**, i.e., snapshots, that have led to the codebase being what it currently is.
- **Object Identifier**: The identifier by which the objects, like **branches** and **commits**, that comprise a codebase are tracked by Git. Every object has an identifier.
- **Configuration**: Git is highly customisable, it therefore relies on numerous configuration files. The local config for a Git repo is located at `.git` in the subdirectory. Git also looks for configs at: `/etc/gitconfig`, `~/.gitconfig`, `.git.config`. Furthermor, `.gitignore` defines which files Git should never track nor be seen as part of the codebase, despite existing in the **working tree**, while `.gitmodules` deals with Git submodules, which is a way of referenceing and managing repos within repo.

## Git Setup

After installing Git on to your system, issue the command `git --version` in your terminal to see what version you are running.

A repo can be **initialised** by issuing the command `git init`. This will **initialise** an empty repo in the /Users/abhi/.git/ **directory**. By default, the .git directory is created hidden within the ***root*** **directory** (/Users/abhi) you chose to create it in. To see hidden files in the ***working*** **directory** issue the command `ls -a /Users/abhi`, where 'ls' represents 'lists' and '-a' 'all'. To confirm the path of the ***working*** **directory**  issue the command `pwd`, which represents 'print working directory'. To change the ***working*** **directory** issue the command `cd`, which represents 'confirm directory', followed by the path to your new ***working*** **directory**, e.g., `cd /path/to/new/working/directory` (whatever the new path might actually be). Alternatively, `~/newworkingdirectory`, where '~' represents your ***root*** **directory** relative to your 'newworkingdirectory', can be used.  

You can check if a repo has already been **initialised** in a **directory** by issuing the command
    `cd /path/to/directory/for/inspection`
    `git rev-parse --is-inside-work-tree`
where 'git' is the command, 'rev-parse' is the subcommand that parses and inspects aspects of Git, and ` --is-inside-work-tree` flags to check if you are inside a Git repo. If you are, terminal will output 'True', if not, there will be no output or an error. Alternatively, issuing the command `ls -a` will output a list of all files within the ***working*****directory**, you can then look for the presence of a .git file. 

Config the name and e-mail address associates with your Git setup, and thus all comprising repos and objects, by issue the commands 
    `git config --global user.name "Your Name"`
    `git config --global user.email "your.email@example.com"`
Here, ` --global` represents that the config is used for all users and all repos. Omit ` --global` from the command to set a specific config to an individual repo and by issuing the modified command within that repo's **directory**. To see the name and e-mail configured to your Git setup issue the command
    `git config --get user.name`
    `git config --get user.email`

## Stage

The **stage**, or **index**, is where changes are held for **committing** later on. For any file to be tracked by Git, a change in its status from **untracked** to 'aware of by Git' is made by its **staging**. 