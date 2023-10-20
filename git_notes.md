# Git Notes

Programming produces four actions that result in changes to a codebase:
1. Creating,
2. Modifying,
3. Checking the status of,
4. And deleting files

A **version control system**, like Git, tracks codebase changes, such as the operations performed on the objects that comprise it.

## Git

Git is a distributed **version control system** that emphasises speed, data integrity and support for non-linear workflows. Git provides answers to the following questions to anyone with access to the Git repository (repo):

- What files exist in the codebase?
- Of those files, which ones comprise the latest version of the codebase?
- Which files have been modified but not saved?
- Which have been saved but not shared with the team?
- What are the changes that led to a particular file looking the way it does?
- What alternative versions of the file are there?
- Who has edited a given file and when?

## Git Workflow

There's no single valid workflow but there are more Git-typical ones that fully leverage its distributed and dynamic capablities. For **local** repos there is *pretty much* one way to use Git. That is:

1. Create files or perform changes.
2. Collect one or more of the changes performed in a unit called a **commit**.
3. Save that set of changes to the history of a given development line.
4. Make changes available to others.

## Setup

1. Initialise the repo.
2. Configuer the repo.
3. Create the initial line of development in the repo.

These steps are also the *usual* life cycle of a given file when working with Git **locally**. They are usually only performed once.

## Git File Life Cycle

Ostensibly, Git tracks files, performs changes and takes 'snapshots',known as **commits**, of a codebase at the point said changes were saved.

Once a file has been introduced to a Git repo, it exists as **untracked**; Git is not tracking changes made to it. To track file changes, execute the command `git add new_file`. Git now *knows* to track 'new_file', as executing `git add new_file` instructed it to add 'new_file' to a list of codebase changes. If another file were added, 'new_file2', that too would be added to the list of codebase changes. After grouping several codebase changes in a single list, known as the **stage** or **index**, they can be saved into the current version of the codebase. A change or group of changes prepared for storeage in this way is known to have been **staged**. **Staging** allows you to selectively choose which changes to **commit** while keeping other changes availble for modifications. The act of saving such changes is **committing** and results in the creation of a unit known as a **commit** in a project's history.

A file's current state, saved in a project's history, is deemed **unmodified** and requires no further action. At this point, the file can be removed or edited. If removed from the repo, it returns to being **untracked** and will require **staging** and **committing** again. If edited, it is now deemed **modified**, meaning its current state differs from that of version **committed** to the projects's history. It too can then be **staged** and **committed**

![The Git file life cycle](<git_file_life_cycle.png>)
*The Git file life cycle*

## Glossary

- **User**: That which performs actions upon a codebase or other artifacts related to or being tracked by Git.
- **Working Tree**: The contents of the **directory** where a Git repo has been initialised.
- **Repo**: Any directory that has been initialised as a Git repo. A repo develops from being ostensibly empty to a compilation of **branches**, i.e., lines of development, and **commits**, i.e., snapshots, that have led to the codebase being what it currently is.
- **Object Identifier**: The identifier by which the objects, like **branches** and **commits**, that comprise a codebase are tracked by Git. Every object has an identifier.
- **Configuration**: Git is highly customisable, it therefore relies on numerous configuration files. The local config for a Git repo is located at `.git` in the subdirectory. Git also looks for configs at: `/etc/gitconfig`, `~/.gitconfig`, `.git.config`. Furthermor, `.gitignore` defines which files Git should never track nor be seen as part of the codebase, despite existing in the **working tree**, while `.gitmodules` deals with Git submodules, which is a way of referenceing and managing repos within repo.

## Git Setup
By default, the .git installation is created hidden within the ***root*** **directory** (/Users/abhi) you chose to create it in. To see hidden files in the ***working*** **directory** execute the command `ls -a /Users/abhi`, where `ls` represents 'lists' and `-a` 'all'. To confirm the path of the ***working*** **directory**  execute the command `pwd`, which represents 'print working directory'. To change the ***working*** **directory** execute the command `cd`, which represents 'change directory', followed by the path to your new ***working*** **directory**, e.g., `cd /path/to/new/working/directory` (whatever the new path might actually be). Alternatively, `~/new_working_directory`, where `~` represents your ***root*** **directory** relative to your 'new_working_directory', can be used. When inputing a path name with potentially awkward charaters, such as '&' or ' ', make sure to enclose the entire path within quotation marks, e.g., `cd ~"/hello/SE & DE Notes"`.  

After installing Git on to your system, execute the command `git --version` in your **terminal** to see what version you are running.

A Git repo can be **initialised** by issuing the command `git init`. This will **initialise** an empty repo in the ***working*** **directory**. You can check if a repo has already been **initialised** in a **directory** by executing the commands:

    `cd /path/to/directory/for/inspection`
    `git rev-parse --is-inside-work-tree`

Here, 'git' is the command, 'rev-parse' is the subcommand that parses and inspects aspects of Git, and ` --is-inside-work-tree` flags to check if you are inside a Git repo. If you are, output to **terminal** will be`True`, if not, there will be no output or an error. Alternatively, issuing the command `ls -a` will output a list of all files within the ***working*** **directory**, you can then look for the presence of a .git file. 

Config the name and e-mail address associates with your Git setup, and thus all comprising repos and objects, by executing the commands:

    `git config --global user.name "Your Name"`
    `git config --global user.email "your.email@example.com"`

Here, ` --global` represents that the config is applicable to all users and all repos. Omit ` --global` from the command to set a specific config to an individual repo and by issuing the modified command within that repo's **directory**. To see the name and e-mail configured to your Git setup execute the command:

    `git config --get user.name`
    `git config --get user.email`

## Stage

The **stage**, or **index**, is where changes are held for **committing** later on. For any file to be tracked by Git, a change in its status from **untracked** to 'aware of by Git' is made by its **staging**.

To **stage** a file execute the command `git add` in the correct ***working*** **directory**, that is the **directory** where your repo is **initialised** and where the file for **staging** exists:

    `cd "/Users/abhi/hello/SE & DE Notes"`
    `git add GitNotes.md`

`git add` **stages** *all* changes in the ***working*** **directory**.

To see what is in a repo but *not* **committed** execute the command `git status`. **Uncommitted** changes will be listed under 'Changes not staged for commit:' These are **modified** files that are **staged** but haven't **committed**. **Untracked** files, that is those that have never been **staged** at all, will be listed under 'Untracked files:'

## Commit

Once **staged**, your file can be **committed** by executing the command `git commit -m`. Following the command, a message within quotation marks about the **commit** can be appended. e.g., `git commit -m "Add git_notes.md"`. `-m` represents the ability to leave a short message, without opening a text editor. Without `-m`, a text editor will open, allowing you to write an extensive or multi-line **commit** message.

## Push

Once **committed**, your file can be **pushed** to another, **remote** repo. First, set the target **remote** repo by executing the command `git remote add origin https://github.com/username/target_repo.git`. e.g., `git remote add origin https://github.com/esonkcoc/SE-Basics.git`. Next, **push** your **local commits** to your **remote** repo by issuing the command `git push -u origin master`. `-u` represents the establishing of a connection between your **local branch** and an **upstream branch**, located in a **remote** repo. Your **local** repo's **master branch** has now been **pushed** to your **remote** repo. Occasionally, a **branch** will have an alternative name, such as 'main' or 'mainline', in which case 'master' will need to be replaced accordingly in the afformention command. Execute the command `git branch` to check the **branch** name. Now that a connection between **local** and **upstream branches** is established, the shorter command `git push` can be executed to **push** future **commits** to the same **remote** repo.

To see a log of all the changes made to a repo execute the command `git log`.

## Merge Remote with Local Repo

If project changes have been made to the **remote branch** which you'd like reflected in your **local branch** you must merge them. In **terminal**, check you are on the **local master branch** by issuing the command `git checkout master`. Fetch updates from your **remote branch** by issuing the command `git fetch origin`. 'origin' May need replacing should you have initially set the **remote** repo's name differently. This command will provide your **local** Git with information about changes made **remotely** without actually making those changes to the **local** ***working*** **directory**. Execute the command `git merge origin/master` to merge the **remote** changes in to the unchanged **local** branch. If you have **uncommitted** changes on your **local master branch**, you should **commit** before merging changes made **remotely** to avoid conflicts.