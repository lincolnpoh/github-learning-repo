# Practicing Git & Github
# This README.md will be displayed as the main description when commited to Github.

--------------------------
--Git command cheatsheet--

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





--Git knowledge--

- Git does not work globally, but rather per each and individual project folder. 
So if a Git has been messed up for a particular project, we could just directly delete the ".git" folder to reset Git.

- Create a ".gitignore" file and include every name of all files/folders which we want to exclude from Git.
Examples would be secret.json, build folders which aren't required for source code, etc.

- A repository is just a collection of snapshots of a file changes. 
Before we can take a snapshot, or more precisely "commit", we need to add objects/files to the staging area.
