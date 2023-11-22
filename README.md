# Practicing Git & Github
# This README.md will be displayed as the main description when commited to Github.

--------------------------
--Git command cheatsheet--
--------------------------

"git init": Setup Git for the current working project folder

"git config --list": Display all the current config info of Git

"git config --global user.name": Set the user.name property for Git config

"git config --global user.email": Set the user.email property for Git config

"git status": Will display all the current Git status of the working project, such as untracked files, etc.

"git add .": Add files to the staging area, so that those objects will be included when the next commit is made.
The period "." represents all the files in the current working directory/ project folder.
When executed in Visual studio code, notice objects/files with those "U" icons, which stands for "Untracked", 
will be changed to "A", which stands for "Added" to the staging area.

"git add [insert filename here]": This will add a specified file to the staging area. Eg: "git add README.md"

"git reset .": This will reset the state of those objects/files pended to be added to the staging area, back to "U" (Untracked) status.
The period here refers to all the files/objects within the current working directory.

'git commit -m "[Insert message/comment/description/reason here]"': This will commit the currently staging files to the repository, along with the provided message.
Eg: git commit -m "Initial commit"

"git log": This will give us a log of all the past commits

'git commit -a -m "[Insert message]"': This command is a shortcut for the combination of "git add ." and 'git commit -m "[Insert message]"'.


-----------------
--Git knowledge--
-----------------

- Git does not work globally, but rather per each and individual project folder. 
So if a Git has been messed up for a particular project, we could just directly delete the ".git" folder to reset Git.

- Create a ".gitignore" file and include every name of all files/folders which we want to exclude from Git.
Examples would be secret.json, build folders which aren't required for source code, etc.

- A repository is just a collection of snapshots of a file changes. 
Before we can take a snapshot, or more precisely "commit", we need to add objects/files to the staging area.

- When we talk about commit, think of them as a unique photo in an album. 
Every commit contains a unique ID that Git can track those differences in those file than in other commits, which we can rollback to anytime during development.
For example, when we introduced a bug in a code somewhere, we could quickly rollback to a previous state if necessary.

- A "HEAD" in Git refers to the most current commit on a branch. Eg: If we see something like "HEAD -> master" in git log, 
it means that particular commit is the most current commit of the master branch

- Once a file which has been added to staging or a repository, was modified or changed, Git will recognize it as "M", which stands for "Modified".
If we want to commit those changes to a repository, we need to treat it like a new file, which will require us to add it to staging, and THEN commiting it again.