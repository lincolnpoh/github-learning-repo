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

"git remote -v": This will return the current info of the remote repo (in this case, GitHub) that we are working with. If Null, it will return nothing.

"git remote show origin": This will show even more information like branches, etc, within the origin, of the remote Git (in this case, GitHub).

"git remote add origin [Insert https for remote .git which can be found in GitHub here]": This command will add a remote https to the current git for us to work with git remotely via GitHub.
The origin here refers to the name of our remote repository (this is different from the https), which typically has a name of origin, which is ALSO the main source of truth for our code.

"git push [Insert name of remote repo. Eg: origin] [Insert branch we want to push to. Eg: master] [-u: This flag will set our specified repo name to upstream remote in the git config file] ": Take local repostitory and upload it/ sync to the remote repository (in this case, GitHub). Without push command, source code will only be commited to the local git repository.
In other words, we can think of push as the remote version of commit. Take note that we should add in the "-u" flag when the remote repository is the final source of truth.

"git fetch": Fetches the latest source code from the remote repostitory to local. Take note that at this point, our local source code does not reflect the latest changes from the GitHub. The reason is that, we need to MERGE the local with the remote target branch (eg: master).

"git merge [Insert the target name/branch we want to merge from the remote repo with the local repo. Eg: origin/master]": Once we fetches the latest source code from the remote repository, we need to merge it to the local repo to get our project folder to reflect thsoe changes.
If we are unsure of what name/branch we should merge with, click on the branch at the bottom left of Visual studio code to confirm it.

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

- GitHub is just a Remote version of Git. There are many other Remote versions of Git products available in the market, such as GitLab, Bitbucket, etc

- There are a few Github terminology which we should understand. 
1) Fork: It means copying the code from someone's repository to ours (only when permitted). We can then work with it and call it another product.
Eg: Very famous example would be Ubuntu, which is a fork of Debian OS.

2) Upstream: This refers to the original repository that we forked from. This is the repository that we originally copied when we created our fork.

3) Push: This is the remote version of commit. Once we commit locally to Git through "git commit", it will not be uploaded/sync to our remote Git (in this case, GitHub).
We need to manually commit it to the remote repository, through the command push. Refer to the command section above.
