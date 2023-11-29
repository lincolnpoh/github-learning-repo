# Practicing Git & Github
# This README.md will be displayed as the main description when commited to Github.

--------------------------
Git command cheatsheet
--------------------------

- "git init": Setup Git for the current working project folder

- "git config --list": Display all the current config info of Git

- "git config --global user.name": Set the user.name property for Git config

- "git config --global user.email": Set the user.email property for Git config

- "git status": Will display all the current Git status of the working project, such as untracked files, etc.

- "git add .": Add files to the staging area, so that those objects will be included when the next commit is made.
The period "." represents all the files in the current working directory/ project folder.
When executed in Visual studio code, notice objects/files with those "U" icons, which stands for "Untracked", 
will be changed to "A", which stands for "Added" to the staging area.

- "git add [insert filename here]": This will add a specified file to the staging area. Eg: "git add README.md"

- "git reset .": This will reset the state of those objects/files pended to be added to the staging area, back to "U" (Untracked) status.
The period here refers to all the files/objects within the current working directory.

- 'git commit -m "[Insert message/comment/description/reason here]"': This will commit the currently staging files to the repository, along with the provided message.
Eg: git commit -m "Initial commit"

- "git log": This will give us a log of all the past commits. If the log is too long, we could exit by pressing "q" button in the terminal.

- 'git commit -a -m "[Insert message]"': This command is a shortcut for the combination of "git add ." and 'git commit -m "[Insert message]"'. 
We could further shorten this command to 'git commit -am "[Insert message]"'

- "git remote -v": This will return the current info of the remote repo (in this case, GitHub) that we are working with. If Null, it will return nothing.

- "git remote show origin": This will show even more information like branches, etc, within the origin, of the remote Git (in this case, GitHub).

- "git remote add origin [Insert https for remote .git which can be found in GitHub here]": This command will add a remote https to the current git for us to work with git remotely via GitHub.
The origin here refers to the name of our remote repository (this is different from the https), which typically has a name of origin, which is ALSO the main source of truth for our code.

- "git push [Insert name of remote repo. Eg: origin] [Insert branch we want to push to. Eg: master] [-u: This flag will set our specified repo name to upstream remote in the git config file] ": Take local repostitory and upload it/ sync to the remote repository (in this case, GitHub). Without push command, source code will only be commited to the local git repository.
In other words, we can think of push as the remote version of commit. Take note that we should add in the "-u" flag when the remote repository is the final source of truth.

- "git fetch": Fetches the latest source code from the remote repostitory to local. Take note that at this point, our local source code does not reflect the latest changes from the GitHub. The reason is that, we need to MERGE the local with the remote target branch (eg: master).

- "git merge [Insert the target remote repo name/branch we want to merge from the remote repo with the local repo. Eg: origin/master]": Once we fetches the latest source code from the remote repository, we need to merge it to the local repo to get our project folder to reflect those changes.
If we are unsure of what name/branch we should merge with, click on the branch at the bottom left of Visual studio code to confirm it.

- "git merge --abort": This command is self-explanatory, as it will abort any merge. We might need to execute this command when there is a merge conflict.

- "git merge --squash [Insert target branch to merge & squash]": This command will merge the target branch, into the currently checkout branch, as well as "squashing" (which literally mean to crush or squeeze something with force so that it becomes flat) everything commited in the target branch, so that the final result in the merged (checked-out) branch will only show the summary of "Merge branch [Target branch] into branch [Checked out branch]" in git log.
Basically this is the same as merge, except for the fact that it leaves a clean git log history in the merged branch.

- "git rebase [Insert the target remote repo name/branch we want to merge from the remote repo with the local repo. Eg: origin/master]": Has the same purpose as merge, in we use it to merge two different branches. We usually use rebase when working with a forked repo, in our local repo, to be in sync with the upstream for the master or main branch.
Before using rebase, remember the golden rule: Do NOT rebase any of our own repo into ANY public branches, potentially used by other developers. 
This will cause the public branch history to get altered (eg: the master or main branch git history will get altered with our own repo).
Why is this the case? Merge and rebase achieve the same merge result, but the process and its real end result is kind of different.
Rebase will merge specified branch to the current checkout branch, by moving the entire current checkout branch to begin on the tip of the specified branch.
Eg: if we execute "git rebase master" while "feature" branch has been checked out, it will end up with the following result:
[master commit 1] <- [master commit 2] <- [feature commit 1] <- [feature commit 2] <- [feature done commit].
Rebasing will effectively incorporate all of the new commits of "feature" branch in "master" branch, as if we developed "feature" directly INSIDE the "master" branch. 
Whereas if we were to git merge "master" into "feature" branch, it will result in the "merging" being logged: 
[master commit 1] <- [master commit 2] <- [feature commit 1] <- [feature commit 2] <- [feature done commit] <- [Merged feature branch with master branch].
Rebasing has several benefits: 
(1) eliminates the unnecessary merge commits required by git merge. 
(2) results in a perfectly linear project history—we can follow the tip of "feature" branch all the way to the beginning of the project.
However, by using rebase, we have the following demerits:
(1) users can’t track how and when commits were merged on the target branch
(2) rebase won’t work with pull requests since we can’t see minor changes someone else made
(3) rebase makes us resolve conflicts in the order that were created to continue the rebase. Unfortunately, this means more work for us, as we may need to fix the same conflicts repeatedly
(4) rebase lowers the feature down to a small number of commits, making it challenging to see the context

- "git pull <[Insert name of repo/ remote name. Eg: origin] [Insert name of target branch. Eg: master] (if we have specified "-u" flag during the git push command, we can skip specifying the remote branch, because Git already know where to pull from.)>": This command combines both the fetch and the merge command into one. 

- "git clone [Insert URL of remote repo which ends with ".git".] [Optionally include destination directory to be cloned to. Eg: cloned_project]": Clones an exact copy of a remote repository to our local repo. It also keeps a reference to the original repo that allows us to run command such as git pull, git log, etc from that remote repo.

- "git branch": Will display all the existing branches in the current project directory.

- "git branch [Insert name of new branch. Eg: new_feature]": This will add a new branch to our project. Take note that we have to switch to the new branch manually. Take note that VScode will NOT switch to the newly created branch automatically, unless we specifically instruct it to by using "checkout" command. 
OR, we could more simply checkout to the newly created branch with the command "git checkout -b [Insert name of the new branch. Eg: new_feature]". This is kind of like the git pull, which combines two commands into one (fetch and merge commands).

- "git branch -M [Insert name of the primary branch. Eg: main]": This command allows us to move or rename our branch to something else. Take note that we HAVE to capitalize the flag M.
Eg: If we execute "git branch -M main", we will be renaming our primary/master branch to "main".

- "git branch -d [Insert name of target branch. Eg: new_feature]": This command will delete the specified branch. Take note that it's SAFER and BETTER to use the lowercase "-d" instead of the uppercase "-D". In Git, lowercase "-d" will ONLY allow deletion of branches which have been FULLY merged with the master/main branch, whereas uppercase "-D" will delete branches regardless whether if they have been merged to master/main or not.

- "git checkout [Insert name of target branch]": This will allow us to "switch" or "checkout" to the specified branch. More information regarding checkout could be found under the "Git knowledge section" below. Fun fact: We could replace "checkout" command with "switch" and the result will be the same.

- "git checkout -b [Insert name of the new branch. Eg: new_feature]": This command allows us to checkout to the newly created branch which we specified through the -b flag. 
This is kind of like the git pull, which combines two commands into one (fetch and merge commands).

- "git checkout -": This command will allow us to switch between master/main branch with the branch that we are currently working on. Running it once from another branch other than master/main will check out the master/main branch. Running it once more will allow us to switch back to the branch we were previously working on.

- "git reset": This command will unstage all files which have been added (known as staged as well). It won't modify or delete anything, just unstage all staged files.

- "git reset [Insert commit ID found through "git log" command. Eg: 63756711834cbb6a5e56c48db770bf1d440b2190]": This will allow us to reset back to a previous commit state. The HEAD will now be moved to that specified commit ID. 

- "git reset --hard [Insert commit ID we want to reset it back to. Eg: 63756711834cbb6a5e56c48db770bf1d440b2190]": This will allow us to HARD reset everything back to the specified commit ID. What this exactly mean is that, if we added or modified ANY files after the specified commit ID, files which have been added will be COMPLETELY DELETED, and files which were modified will be reset to the state of that commit ID we specified. This is a dangerous reset, so handle with care before proceed with executing this command. It is usually much safer to just execute without the "--hard" flag. 
*** Be careful, DO NOT RESET code on a remote repository in GitHub if it has been PUSHED to it. Other developers might have already been working on that particular code, and if we were to remove it, chaos will fall upon all. If were have to, use "git revert" instead. More explanation below.

- "git revert [Insert commit ID to want to revert back to. Eg: 63756711834cbb6a5e56c48db770bf1d440b2190]": Revert command works almost like reset, in that it will revert our changes back to the point of commit Id where we specified. It will also remove any files that were added after the specified commit ID.
When a commit has been pushed to a remote repo in GitHub



-----------------
Git knowledge
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

- A "HEAD" in Git refers to US. It points to whatever WE checked out. It follows us wherever we go, whatever we do. 
If we make a commit, HEAD will move to it. If we checkout something, HEAD will move to it. Whatever we do, if we have moved somewhere new in our commit history, HEAD will move along with us.
Eg: If we saw something like "HEAD -> master" in git log, 
it means that we (HEAD) are currently in the most current commit of the master branch.

- "Check-out" is a concept where a file could not be checked out by more than a single developer, because once a file/ source code/ class has been assigned for work under someone, another guy CANNOT make any changes to that same file, as it would technically be really chaotic for multiple developers trying to make changes to a single file. 
So, what happens is that once a checked out file is done with any edits, it should be staged (by adding it to staging area) and commited, before another developer could check out and work on that same file again.

- Once a file which has been added to staging or a repository, was modified or changed, Git will recognize it as "M", which stands for "Modified".
If we want to commit those changes to a repository, we need to treat it like a new file, which will require us to add it to staging, and THEN commiting it again.

- GitHub is just a Remote version of Git. There are many other Remote versions of Git products available in the market, such as GitLab, Bitbucket, etc

- Git has a concept of "remotes". These are like easy nicknames for a repository, so you don't have to use its full URL every time you want to refer to another repository.
An "origin" is an example of that, and it is just an ALIAS on OUR system/PC for a particular remote repostitory. It's not actually a property of THAT repository.
In that sense, the same repository could have a different ALIAS, other than origin, for another developer. 
By doing "git push origin [Insert branchname. Eg: master]", we are pushing to the origin repository, which we setup through the command 
"git remote add [Name of ALIAS we want to assign. Eg: origin (could be any name we like, but a more commonly known naming convention is origin)] [Insert https for remote .git found in GitHub]".
We could technically specify the URL directly, when working with git push command, and it will still work out. Eg: "git push git@github.com:git/git.git master"
However, it is not really practicaly to keep trying to memorize the long URL. Shorten it up with an ALIAS such as origin, and we could simply just specify it to: "git push origin/master"
We can see what URL belongs to each remote by using: "git remote -v"

- There are a few Github terminology which we should understand. 
1) Fork: It means copying the code from someone's GitHub repository to our GitHub repository, without affecting the original repository. We can then work with it and call it another product.
One good thing to note is that when we fork, we can fetch updates from the original GitHub repo, which is known as the upstream repository.
Eg: Very famous example would be Ubuntu, which is a fork of Debian OS.
Once we forked a Github repo, we need to clone (through "git clone" command) it into our local system so that we can make our own changes to it. 
Before making any changes, make sure to create a new branch.
After making changes to the new branch, push it to our forked remote git repo, and then finally make a pull request to the upstream.
A good thing to take note is that, when working with the forked locally, we can keep it in sync with the original, by adding the target upstream/original link to a remote/alias. A good alias/remote name for it would be "upstream". The command for it is: "git remote add upstream [Insert target upstream/original URL .git]". 
We can confirm we have added by running "git config --list" and locate the "upstream" property.
*If there is any update or changes in source code in the upstream/original repo, we can first fetch from the upstream to our local repo through the fetch command: "git fetch upstream".
Next, once we have fetched the data, we apply the changes to our local system through the rebase command: "git rebase upstream/master". This will sync our local repo "master" branch with the latest upstream repo source code. ***Be very careful NOT to rebase our created branch with the master branch, as it will integrate our own created branch into the master branch, which alters the git history of the master branch, once we make a pull request in the upstream. This will have fatal consequences since master branch is a public branch, used by other people.
For more info regarding rebase, refer to the command section above.

2) Upstream: This refers to the original repository that we forked from. This is the repository that we originally copied when we created our fork. More explanation of upstream and downstream below.

3) Push: This is the remote version of commit. Once we commit locally to Git through "git commit", it will not be uploaded/sync to our remote Git (in this case, GitHub).
We need to manually commit it to the remote repository, through the command push. Refer to the command section above.

4) Fetch: Fetches the latest source code from the remote repostitory to local. Take note that at this point, our local source code does not reflect the latest changes from the GitHub. The reason is that, we need to MERGE the local with the remote target branch (eg: master).

5) Merge: Once we fetches the latest source code from the remote repository, we need to merge it to the local repo to get our project folder to reflect those changes.

6) Pull: Pull is a combination of Fetch and Merge into one command. Very convinient, though some from the community mentioned it's safer to Fetch and Merge manually. A thing to note is that if we have any modified/ uncommitted source code in our local repostiory, this operation will fail when trying to pull from the remote repo, because the system will not be able to judge which source code to merge since both the local and the remote repo contain latest source code. Git WILL NOT overwrite our local changes with the remote source code. We must have a clear working directory. 
One way is to commit our local repo first. Another way is to use a technique called "Stash".
Another important thing is, if our local code is modifying the same line of code that we are trying to pull and merge in from the remote, a Merge conflict will occur.

7) Pull request: In GitHub, where open-source projects were being worked on by multiple developers, people tend to fork from one project, add new features to it, and when it's done, they would like to have it implemented into the original upstream. This is where Pull request comes in, where people could request and notify the original developer/s of the upstream (original project) to pull (fetching and merging combined) from the forked, so that future versions of the project will have those new features implemented into the core system.

- More detailed definition of Upstream and downstream: In terms of source control, we're downstream when we copy (clone, checkout, etc) from a repository. Information flowed "downstream" to us.
When we make changes, we usually want to send them back "upstream" so they make it into that repository so that everyone pulling from the same source is working with all the same changes. 
This is mostly a social issue of how everyone can coordinate their work rather than a technical requirement of source control. 
We want to get our changes into the main project so we're not tracking divergent lines of development.
Sometimes we'll read about package or release managers (the people, not the tool) talking about submitting changes to "upstream". That usually means they had to adjust the original sources so they could create a package for their system. They don't want to keep making those changes, so if they send them "upstream" to the original source, they shouldn't have to deal with the same issue in the next release.

- Merge conflicts: A merge conflict is one of the scariest thing when working with Git. In VScode, any files that has a merge conflict will be highlighted with an exclamation mark symbol.
It happens when a particular file, under the has same line, with different code modification while trying to merge two branches, as Git cannot figure out which code to use.
Once there is a merge conflict, we have to two options:
1) to abort the merge, by executing "git merge --abort". This will get us to the original state before the merge started.
2) solve the conflict. Then, we WILL have to manually make a commit (with the "git add ." and "git commit -m" commands, or simply "git commit -am" command), which is called a merge commit, which is required if we are dealing with conflicts. 
In normal cases, where we don't have to deal with merge conflicts, merging and commiting happens automatically with a fast-forward. However, with merge conflicts, we handle the commit ourself.


------------------------
GitHub cool features
------------------------

- Did you know we could press the period "." button inside any repo to access the codespaces? A cloud-based version of VScode is also known as a codespace. 
It is a paid-per-second service. We could access the codespace according to our GitHub plans. Apparently, Free plan users could access it for 120 minutes per month. Just a good-to-know.

