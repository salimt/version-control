### How to use Git and GitHub

This Notes were taken based on the How to use Git and GitHub course on [Udacity](http://udacity.com).
***

![alt tag](http://i.imgur.com/Pvq1Ej0.png)

## Lession 1 Notes:
***

### Git
***

A Version Control System

##### Git command description

**git commit -m "message"**

```
This command is used to save a version of your working file
and save a message indicating the changes made in the file.

When to commit:  commit per logical change. For example, if you fixed a typo, then fixed a bug in a separate part of the file.

Tracking across files?
	Is important if all the files in the repository have a dependency in each other to the program or project to work.
	commad git log --stat
	give you some statisty of what files have change when working and tracking across multiple files.
	
Commits with Miltiple Files.

Entering commit IDs

If it is easier, you may enter the first four or more characters of the commit ID rather than pasting the entire ID.
```
**git log**

```
This command is used to see all file versions and commets made. Each commit does an unique id, the author's name, a date, and the message associated with the commit. You can compare two file by ids to see changes btwn two file versions.
    commad to compare two files
    git diff <id-1> <id-2>
    
    NOTES:
    
    To stop viewing git log output, press q (which stands for quit).
    
    To get colored diff output, run git config --global color.ui auto
    
```

**git clone**
***
```
The 'git clone' is used to clone an existen repository to a local host.
For example cloning an existen repo on a coding sharing and colaboration platform. You the type the commad follow by its HTTPS or URL like
	git clone https://github.com/udacity/asteroids.git
	
	The above command will clone a repo in cloud to a local host machine.
	

```
**git chekout**
***
This command is uses for checking out prior commits<br/>
**Note**: it is not the same as SVN checkout if you are comming from the Version Control System enviroment.

The command Caroline types to checkout the "Revert controls" commit is<br/>
`git checkout b0678b161fcf74467ed3a63110557e3d6229cfa6`

`git checkout -b branchName	` create and to switch directly to a new branch.
The code is like doing `git branch jose` + `git checkout jose`

__Using Git commads__

```
/* Set up Git Configuration */

git config --global user.email "you@yourdomain.com"

git config --global user.name "Your Name"

git config --global core.editor "vi"

git config --global color.ui true

/* See Git configuration */

git config --list

/*  To initialise a local repository */

git init 

/*  Add a file to the repo */

git add 

/* commit the change to git */

git commit -m "Message goes here" 

/*  see the commits */

git log 

/*  Git has a 3 Tier Architecture:  Working - Staging - Repo
Changes to files are put in a Checksum SHA-1 hash 40digit value containing parent hash, author and message.
HEAD is the latest commit of the checked out branch */

/*  Basic Commands  */

git status  /*  the command 'git status' tells which files are not added or committed from Working to Staging to Repository */

git commit -m "" /*  Commits and changes to all files that are in Staging into Repo  */

git diff /*  show changes between Working and Local Repo, no file supplied shows all files  */

git diff --staged /*  shows changes between Staged and Local Repo  */

git rm file.txt /*  will remove file from working then git commit -m "" to also remove from Repo */

git rm --cached file.txt /* leaves copy of file in Working but removes from Staging and Repo */

git mv /*  rename or move files - then git commit -m "" to move to Repo */

git commit -am "text goes here" /* adds all files straight to Repo from Staging if they have changes - meaning they skip git add */

git checkout -- file.txt /*  restore Repo file to Working Directory using current branch  */

git reset --soft HEAD^ /* restore repo file to staging */

git reset HEAD file.txt /*  Move a Stage file out of Stage back to Working */

git commit --amend -m "message" file.txt /* Change last commit to Repo (only last one can change) */

/* Reverting --soft --mixed --hard will go back to previous commits*/
git log /* gets the sha1s so you can see the coomits where you want revert  back to  */

git reset --soft sha /* changes Repo but not Staging or Working */

git reset --mixed sha /* changes Repo and Staging but not Working */

git reset --hard sha /* changes all 3 Tiers */

git clean -f /* remove untracked files from Working  */

.gitignore /* ignores files to track in Working / track the .gitignore file */

Global Ignore /* create in home folder  */ 
.gitignore_global
/* Add in  */
.DS_Store
.Trashes
.Spotlight_V100



git config --global core.excludesfile ~/.gitignore_global /* add to gitconfig */

/* Stop tracking changes */

git rm --cached file.txt /* leaves copy in Repo and Working */


/* Track Folders changes
Add an invisble file to a folder like .gitkeeper then add and commit */

/* Commit Log  */
git ls-tree HEAD
git ls-tree master
git log --oneline
git log --author="Neil"
git log --grep="temp"

/* Show Commits */

git show dc094cb /*  show SHA1 */

/* Compare Commits
Branches */

git branch /*  Show local branches * is the one we are on */

git branch -r /* Shows remote branches */

git branch -a /* Shows local and remote */

git branch newbranch /* creates a new branch */

git checkout newbranch /* switch to new branch */

git checkout -b oldbranch /* creates and switches to new branch  */

git push origin newbranch /* Push new branch to remote */


/* Diff in Branches */

git diff master..otherbranch /*  shows diff */

git diff --color-words master..otherbranch /*  shows diff in color */

git branch --merged /*  shows any merged branches */

/* Rename Branch */

git branch -m oldname newname

/* Delete  Branch */

git branch -d nameofbranch

/* Merge Branch  */

git merge branchname /* be on the receiver branch to merge the other branch */

/* Merge Conflicts between the same file on 2 branches are marked in HEAD and other branch */

git merge --abort /*  Abort basically cancels the merge */

/* Manually Fix Files and commit
The Stash */

git stash save "text message here"

git stash list /* shows whats in stash */

git stash show -p stash@{0} /* Show the diff in the stash */

git stash pop stash@{0} /*  restores the stash deletes the tash */

git stash apply stash@{0} /*  restores the stash and keeps the stash */

git stash clear /*  removes all stash */

git stash drop stash@{0}


/* Remotes
You can push and fetch to the remote server, merge any differences - then push any new to the remote - 3 branches work remote server branch, local origin master and local master
Create a repo in GitHub, then add that remote to your local repo */

git remote add origin https://github.com/neilgee/genesischild.git /*  origin can be named whatever followed by the remote */

git remote /* to show all remotes */

git remote show origin /*to see remote URL*/

git remote remove origin /* to remove remote */

git remote rm origin /* to remove remote */

/* Push to Remote from Local */

git push -u origin master /* push to remote(origin) and branch(master)
/* Cloning a GitHub Repo - create and get the URL of a new repository from GitHub, then clone that to your local repo, example below uses local repo named 'nameoffolder' */

git clone https://github.com/neilgee/genesischild.git nameoffolder

/* Push to Remote from Local - more - since when we pushed the local to remote we used -u parameter then the remote branch is tracked to the local branch and we just need to use... */

git push

git push origin newbranch /* Push a branch to a remote */

/* Fetch changes from a cloned Repo */

git fetch origin /*  Pulls down latest committs from remote origin/master not origin, also pull down any branches pushed to Repo
Fetch before you work
Fetch before you pull
Fetch often */

/* Merge with origin/master */

git merge origin/master

git pull /* you can also do git pull which is = git fetch + git merge
Checkout/Copy a remote branch to local */

git branch branchname origin/branchname /*  this will bring the remote branch to local and track with the remote */

/* Delete branch */

git branch -d branchname

/* Checkout and switch branch and track to remote */

git checkout -b nontracking origin/nontracking

/* Remove remote branch */

git push origin --delete branch


/*Undoing*/

git checkout path-to-file /*restores a file before it is staged */

git reset HEAD path-to-file /*if it is staged - restores a file from last commit and then git checkout path-to-file */

git checkout HEAD^ path-to-file /*if is staged and committed - restores from last commit */

git reset --hard HEAD^ /*restore prior commit */

/*Keeping a Fork synced with the original repo*/

git remote add upstream https://github.com/user/originalrepo /* From the forked repo - add the original master repo */

git pull upstream master /* Sync it up */

/*Tags*/

git tag -a v1.0.0 -m "add message here" /*tagging a commit with a version number*/

git push --tags /* pushes tag info to master remote */

/*You can checkout a commit and add a tag to that commit by checking out its SHA */

git checkout f1f4a3d /*checking out a commit - see the commit SHAS by git log */
```

#### Version Control
***

A Version Control System is useful to save preview copies of your file. And it is really handy to compare two different version of two files.

**As a programmer**: is important to save version or changes of sources code at a regular intervals ( e.g every hour or less).

Examples of Version control system:

* Git
* SVN
* CVS
* SBM

#### GitHub
***
Code sharing and collaboration platform
***
Note: It is important to know Unix Command Line Basic

##### What will be cover
***
LESSION 1: Why version control?
			install Git + read-only usage.
			
LESSION 2: read + write Git.

LESSION 3: Share + Collaborate with others in GitHub platform.
***

#### Finding Diffs Between Larger Files
* * *
##### Automatically Compare Files
**Windows** - FC (File Compare) is an utility on the cmd (Command Prompt)

```
Command =  FC 1st-Argument-FileName 2st-Argument-FileName
```

**Mac and Linux** - Diff (Difference).

**Note**: it may differ depending on the command for the terminal using by the user.

```
Command =  diff -u 1st-Argument-FileName 2st-Argument-FileName
```
### Downloading necessary files

* Save [this file](https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash) in your home directory with the name `git-completion.bash`.
* Save [this file](https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh) in your home directory with the name `git-prompt.sh`.
* Download `bash_profile` from the Downloadables section.
* If you already have a file in your home directory named `.bash_profile`, copy the content from bash_profile_course and paste it at the bottom of `.bash_profile`. Otherwise, move `bash_profile` to your home directory and rename it to `.bash_profile`. If you use Linux, you may need to name this file `.bashrc` instead of `.bash_profile`. (If you're curious to learn more about how bash prompts work, see [this page](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html).)
* [.bash_profile](https://www.udacity.com/api/nodes/3333158951/supplemental_media/bash-profile-course/download) example download. just rename it the download file with the dot at the biginning.

### Make sure you can start your editor from the terminal

If you use Sublime, you can do this by add the following line to your `.bash_profile` (you may need to change the path if Sublime is installed in a different location for you):

```
alias subl="/Applications/Sublime\ Text\ 2.app/Contents/SharedSupport/bin/subl"
```

### Making Git configurations

Run the following Git configuration commands. The first one will need to be modified if you are using a text editor other than Sublime, or if Sublime is installed in another location for you. See [this page](https://help.github.com/articles/associating-text-editors-with-git/) for the correct command for a couple of other popular text editors. For any other editor, you'll need to enter the command you use to launch that editor from the terminal.

```
git config --global core.editor "'/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl' -n -w"

git config --global push.default upstream

git config --global merge.conflictstyle diff3
```
(Instead of the first command, you may be able to use the simpler `git config --global core.editor "subl -n -w"` as shown in the video, but many students have found this does not work for them.)

### Restart the terminal

You'll need to close and re-open the terminal before all your changes take effect.
***

#### General Notes:

##### Relationshipts
    type -> of
    part-> of
    operates -> on
	refers -> to
#### Git Errors and Warnings Solution

***
**Should not be doing an octopus**
<br />
Octopus is a strategy Git uses to combine many different versions of code together. This message can appear if you try to use this strategy in an inappropriate situation.
***
**You are in 'detached HEAD' state**
<br />
HEAD is what Git calls the commit you are currently on. You can “detach” the HEAD by switching to a previous commit, which we’ll see in the next video. Despite what it sounds like, it’s actually not a bad thing to detach the HEAD. Git just warns you so that you’ll realize you’re doing it.

***
**Panic! (the 'impossible' happened)** 
This is a real error message, but it’s not output by Git. Instead it’s output by GHC, the compiler for a programming language called Haskell. It’s reserved for particularly surprising errors!

***
**Takeaway** We hope these errors and warnings amused you as much as they amused us! Now that you know what kind of errors Git can throw, you’re ready to start checking out previous versions of files with Caroline.
***

***
## Lession 2 Notes:
***

#### Repository

**Note:** The content of **Git** is in a hidden file .git </config, /object>
<br/>**?** Read about Meta data, git diff --staged, git reset --hard, and  issue tracker IDs, Resolving Merge Conflicts, also this command `git log -n 1`. Automatic vs. Manual Merging?.
<br>

##### How to initialize git an exist repository?
Run the command `git init` to initialize git in an exist repo or create a new folder or directory and run the command once you have navigate to the directory in the command line.<br/>

working directory
Staging Area
Repository

##### git diff `compare working directory VS staging area.`
##### git diff --staged `compare staging area VS commit 1.`
##### git diff commit1 commit2 `compare commit 1 area VS commit 2.`

[Udacity Git Commit Message Style Guide](http://udacity.github.io/git-styleguide/).


Choosing what changes to commit

If you accidentally add a file to the staging area, you can remove it using `git reset`. For example, if you accidentally add lesson_2_reflections.txt, but don’t want it to be committed yet, run `git reset lesson_2_reflections.txt` and the file will be removed from the staging area, but it will still be in your working directory.<br/>

If you are following along, you should run git checkout master before you commit. This is because your HEAD is still 'detached' from Lesson 1 when you checked out an old commit, and running this command will fix that. You'll learn more about what this command does later this lesson.

#### Branches
***
**What is a branch?**<br/>
a branch is a copy of your repository, and you make one branch when you want to try new feature or do some crazy stuff without messing up the original repository. Branches are really useful for collaboration with other developers.<br/>
**master**: Master is the name given to main branche of the repository.<br/>

`git branch` command show you all the branches in your repo.<br/>
`git branch < "new branch name" ">` for example `git branch dev-area`. will create/make a new branch/copy with the name dev-area.<br/>

`git checkout < branch name>` is use to switch btwn branches.
`git log --graph --oneline` show you a list or graph of commits in you working branch.<br/>

`git log --graph --oneline branch 1 branch 2` show you a more dealing graph of commits of two brach. And you can compare and see the different commits in two or more branches.

### Read about
***
Detached HEAD Revisited
***

Combining Simple Files.
##### merging files.
**Merging on the Command Line**<br/>
**A note about git merge**

`git merge` will also include the currently checked-out branch in the merged version. So if you have branch1 checked out, and you run `git merge branch2 branch3`, the merged version will combine branch1 as well as branch2 and branch3. That’s because the branch1 label will update after you make the merge commit, so it’s unlikely that you didn’t want the changes from branch1 included in the merge. For this reason, you should always checkout one of the two branches you’re planning on merging before doing the merge. Which one you should check out depends on which branch label you want to point to the new commit.

Since the checked-out branch is always included in the merge, you may have guessed that when you are merging two branches, you don't need to specify both of them as arguments to `git merge` on the command line. If you want to merge branch2 into branch1, you can simply `git checkout branch1` and then type `git merge branch2`. The only reason to type `git merge branch1 branch2` is if it helps you keep better mental track of which branches you are merging.

Also, since the two branches are merged, the order in which they are typed into the command line does not matter. The key is to remember that `git merge` always merges all the specified branches into the currently checked out branch, creating a new commit for that branch.

#### Merge conflict

If you get a message like this

```
Auto-merging game.js
CONFLICT (content): Merge conflict in game.js
Automatic merge failed; fix conflicts and then commit the result.
```
then your files were not in the same state as Caroline's when you started the merge. To fix this, complete the following steps:

1. Restore your files to their state before you started the merge by running `git merge --abort`

2. Double check the state of your files. If you run `git log` while the master branch is checked out, you should see Caroline's "Add color" commit as the second-most-recent, and the most recent should be your commit fixing the bullet bug. If you use `git diff` to compare your commit to Caroline's, your commit should introduce the line `this.delayBeforeBullet = 10;` on line 424. The line should be indented to the same level as the line below it using only spaces (no tabs), and the line should have no spaces after it.

3. Once your file is in the correct state, create a new commit with your changes.

4. Try the merge again.

#### Merge conflict (Newline characters between Windows and Unix systems)

Context: Whenever we hit the "Enter" key on the keyboard, we are actually telling the computer to insert an invisible character into our text file to indicate to the computer that there should be a new line. Unix systems adds one character called the "line feed" character or LF or \n while Windows systems adds two characters, "carriage return" and "line feed" or CRLF or \r\n.

Caroline's files have LF because her files were edited on Mac OSX, which uses LF. If a Windows user were to edit Caroline's files, the Windows text editor might convert all LF to CRLF to make editing files possible. When the Windows user merges her file with Caroline's files, a merge conflict will result due to the different LF and CRLF characters.

To fix this, Windows users should set the global autocrlf attribute to true: `git config --global core.autocrlf true`. More information can be found here: https://help.github.com/articles/dealing-with-line-endings/#platform-all

#### Comparing a commit to its parent

The command Caroline mentions to compare a commit to its parent is `git show commit_id`

#### Deleting branches
run `git branch -d branch_name`

If a branch is deleted and leaves some commits unreachable from existing branches, those commits will continue to be accessible by commit id, until Git’s garbage collection runs. This will happen automatically from time to time, unless you actively turn it off. You can also run this process manually with `git gc`.
***
### Update Easy Mode

### Motivation

Master has updated since the easy-mode branch was created. In this case, it has the addition of coins, which you might like to include in the easy-mode branch. In general, it’s very common that if you make a branch, either an experimental branch or to work on a new feature, you want to periodically merge master into that branch. This is because master usually contains the official version of the code, and it’s common to want experimental changes to include all of the changes to master.

### Previous version of the diagram
Here’s what the history looks like right now. 
![alt tag](https://lh6.ggpht.com/4Z1H9ULiwr6p2zn8ISqJtlleMX7BFMLAEpXbXEqNoQz4JboVxjdJNN2leARBL6lzPFBTHy-V4WS0XIZccQ=s600#w=1920&h=1080)

### Draw an updated diagram

If you merge master into the easy-mode branch, what will the history look like afterward? Take a minute to draw the new history using whatever method you like best. You might want to use pencil and paper, or create a text file with stars and dashes similar to the output of `git log --graph`, or maybe use an online diagramming tool like gliffy or yUML. Once you’re finished, watch the solution to compare your diagram to Sarah’s.

### Diagramming Tools

* [gliffy](https://www.gliffy.com/)
* [yUML](http://yuml.me/diagram/activity/draw)

If you have a favorite that we don't have listed here, mention it in a forum post so that others can find it!
***
## Lession 3 Notes:
***

#### Create a GitHub account

In this lesson, you'll be sharing changes on GitHub, so you'll need a GitHub account. If you don't already have one, you can create an account by visiting [github.com](https://github.com/) and clicking "Sign up for GitHub".

When you're asked to choose a plan, you can choose a free plan, since we won't be using any of the paid features in this course.

#### Set up Password Caching

Every time you send changes to GitHub via the command line, you'll need to type your password to prove that you have permission to modify the repository. This can get annoying quickly, so many people like to set up password caching, which will let you type your password once and have it auto-filled on that computer in the future. To do this, follow the instructions [here](https://github.com/). If you're using Windows and you followed our Git installation instructions earlier, you're using msysgit, so you can follow the instructions for msysgit.

#### Keeping Repositories in Sync
***
### Copy the HTTPS URL, not the SSH URL!

At 1:29, Caroline copies the URL to the repository. The video mistakenly shows the URL to use if the repository is accessed over SSH. The course assumes that the student will use HTTPS, not SSH. Please click on the `HTTPS` button and copy the URL that shows up for HTTPS. It will begin with `https://` rather than `git@github.com`.

If you are interested in using SSH instead, you can follow the instructions here, but this is not recommended unless you are already familiar with SSH keys.

### Sharing your reflections

We encourage you to be bold in sharing your reflections on GitHub. If you're not happy with any of your responses, the best solution is to update that response in one or more new commits. The previous response will still be visible in the commit history, but updating your perspective over time is part of the learning process! Having a commit history that shows your updating perspective will reflect well on you, not poorly.

That said, if you've written anything in your reflections repository that you are not comfortable sharing, you can checkout the commit before you introduced that change, create a new branch at that point, and commit any other changes you are willing to share to the new branch. Then, by only pushing your new branch, you can keep the changes on your original branch private.

### Make changes on GitHub

Now that you've seen how to create a remote repository and push changes to it, **use the GitHub website** to create a new file for your lesson 3 reflections and add the below question and your thoughts on it.

If you prefer to start from the file lesson_3_reflection_prompts.txt in the Downloadables section, you can download that file, commit it locally, push to GitHub, then add your response **using the GitHub website.**

### Reflect: Using a remote repository

Use the following reflection prompt:

**When would you want to use a remote repository rather than keeping all your work local?**

When you're finished committing your changes, click "Next" to see how to pull those changes to your own computer.

##### Pulling Changes
***
`git pull` to pull update from cloud repo in GitHub.<br/>
`git pull origin master` to specify an branch
***

#### Forking a repository
***
**Forking** is almost or work similar with cloning. But instead of cloning a repository to your local machine your clone in the same github server using forking. Forking also is useful which contributing to other people.

***
**Updating Local Copies of Remote Changes**<br/>

```
							git fetch origen
git pull origen master =	git merge master origin/master
```

### Making a Pull Request
***
Making a pull request 
	* Collaborating using GitHub 
	1. Make a new branch
	2. Make a pull request: the purpuse of a pull request is to ask for cheching a changing that you want to merge to the master branch.
		Note: When you make a pull request to a contributor or an owner of a repo he o they will be notify by email in addition than GitHub.
	3. 
	
Fork the repository and clone your fork

Now that you've learned how to fork a repository, push changes to your fork, and make a pull request, you’re ready to contribute to the create-your-own-adventure story that you saw at the beginning of the lesson. To do this, first you should fork this repository. Then clone your fork, and make a branch to make your changes in.

Note: You could make your changes directly to the master branch in your fork, but when contributing to a public repository, it’s standard practice to make the changes in a non-master branch within the fork. This way, you can easily keep your master branch up-to-date with master of the original repository, and merge changes from master into your branch when you are ready.

Make a change to the story

Next, you should actually make a change to the story. For instructions on how to do so, please read the README in the create-your-own-adventure repository.

Make a pull request

Next, you should make a pull request containing your changes to the original repository. To do this, click the "pull request" button from your branch like you did before, but this time, leave the original repository as the base.

Ask for your pull request to be merged

You don't have permission to modify this repository, so you'll need someone at Udacity to merge your pull request. Our helpful bot Casey may be able to merge your pull request automatically. To have your pull request automatically merged, you'll need to follow the guidelines in the README of the repository, and in addition you won't be able to delete or modify lines. That restriction on deletions is because Casey doesn't want to merge a request that accidentally deletes part of the story, and she can't tell the difference between an accidental deletion and an intentional modification. To request auto-merging, leave a comment on the pull request containing "@casey-collab". For example "Please review this, @casey-collab". Make sure to leave the comment on the "Conversation" tab of the pull request, not the "Files changed" tab.

There are some valid pull requests that Casey won't be able to merge. For example, she won't accept a pull request that fixes a typo, since that modifies a line. If you'd like to make a pull request Casey can't merge, feel free to do so, and someone from Udacity will merge the pull request if we have time. However, we can't guarantee a response to these pull requests.

If needed, update your pull request

If someone merges your pull request or leaves a comment, GitHub will email you and let you know. If you're asked to make some changes, push those changes to your fork to update the pull request. Make sure you let the reviewer know that they should take another look!

If your pull request would result in a merge conflict, and you're not sure how to resolve it, see the next video for instructions.

NOTE: Upstream is the name use to call the original repo of someone else on the cloud. upstream is the origen of the original repo but since you have your  origin after your cloned the repo you called upstream.

### Merge conflicts in Pull request

1. Add the original repository as a remote in your clone.

	
		* `get remote add upstream + URL`
		* `git checkout master`
		* `get pull upstream master`
		* `git checkout branchName`
		* `git merge master + branchName`
	
2. Pull the master branch from the original repository.
3. Merge the master branch into your chanfe brange.
4. Push your change branch to your fork.
***
#### ERRORS
***
* fatal: your current branch 'master' does not have any commits yet
<br/> the above error show up when you have 0 commit in a repo. 
But nothing is wrong with the repo, don't panic yet lol.


###Clarifications

```
* how fetch works?
* merging remote changes?

```

#### Resources:
***
* [Become a GitHub Pro](http://blog.udacity.com/2015/06/become-github-pro.html)

* [How to write the perfect pull request](https://github.com/blog/1943-how-to-write-the-perfect-pull-request)


 


