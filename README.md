# about-git
A single place where all I know about using Git and Github can be found.

A repository is a folder consisting of one or more than one file along with a hidden folder named as ".git".
This ".git" folder has all the information regarding our performed gut operations and handles all the git services.
".git' spits the required files we need into our working directory which is known as Repository.

Please checkout just the guide.txt and simple-steps.txt file as others were just sample files which were experimented on.
The commands written inside the text files are UNIX based git commands executed in git bash command line.





# Git Cheatsheet 

All the following steps are prefered to be followed and executed on 'Git Bash' after installing it on your machine.


## 1st time git setup
### STEP 0.1 

```bash 
git config --global user.name yourname
```

### STEP 0.2

```bash
git config --global user.email "yourmail@gmail.com"
```

To know it is set up or not :

```bash
git config --global user.name
```
```(your username as output)```

```bash
git config --global user.email
```
```(your email as output)```



### STEP 1

"touch" creates a new blank file  of .gitignore

```bash 
touch .gitignore
```

edit the .gitignore file and add the name of the folder which we dont want to upload 
    
### STEP 2 

FYI : If we want to have a repository then 2 options we have, 

	1. git init (it initializes from the start)
	OR
	2. clone (it clones a repo we want and clones it's whole data from server)

Will create a .git file, keep hidden files enable to see it

```bash
git init
```

### STEP 3 

 Very imp Flow of git -

	    Untracked file(On local device)----> Staged(filewhich we wish to put on git) <---|
						    |					     |
						    |	{ Commit }			     |
						    v					     |
					Unmodified file on git				     |
			(Goes on git which we can edit/remove)[snapshot taken by git]	     |
						    |					     |
						    |  (If edited)			     |
						    v					     |
				          Modified file on git >------(Back to staging)------|

To put all the contents at staging area and . means all

```bash
git add .  
```

OR If dont want to put all files then use the following syntax 

```bash
git add filename
```

OR If want to put all the files at staging then, 

```bash
git add -A
```

👉🏻 Can check status now by 

```bash
git status
```


### STEP 4

- ```git commit``` means taking a snapshot 

- So ```git add``` and ```git commit``` makes a snapshot associated to the changes we made

- But right now nothing is added to my repo so using "Initial commit"

If this command is executed then an editor will open then press ```i``` to edit and write the message ```Initial commit``` and then press ```Esc``` key and then type ```:wq``` to save and exit the file.

```bash
git commit
```
- ALTERNATE EASY METHOD

```bash
git commit -m "Initial commit"
```

- I prefer this as it skips staging and directly commits :

```bash
git commit -a -m "msg"
```

## Commit done 🎉 , now Push remaining 

To finally push the "master" branch on "origin" url 

```bash
git push -u origin master
```

- If once ```push -u origin``` is used then next time we just write ```git push``` which will by default push it the branch which was last commanded with ```-u```

# Getting Started with ➡ Github ⬅

Make a repo on github with no files(no readme, etc) just as an example 😉

TO CONNECT TO GITHUB'S REMOTE REPOSITORY WITH OUR LOCAL REPOSITORY(Folder on the PC which we need to upload on github)


```bash
git remote add origin git@github.com:meetmakwana19/about-git.git
```
```git@github.com:meetmakwana19/about-git.git``` is the **SSH** link of the github repository on which we want to connect and upload our local repository.

MEANING A REMOTE NAMED ```origin``` IS ADDED AND OUR URL CAN BE CALLED AS ```origin```

- TO SEE REMOTE
~~~bash 
git remote
~~~
Output:
```bash
origin
```

- TO SEE URL 
```bash
git remote -v
```
Output :
```bash
origin  git@github.com:meetmakwana19/about-git.git (fetch)
origin  git@github.com:meetmakwana19/about-git.git (push)
```


**⚠⚠ NOW GITHUB IS NOT LINKED WITH OUR PC 
SO TO PUSH THE LOCAL REPO TO GITHUB DO THE FOLLOWING :** 

1. Go to this Github documentation by [clicking here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?utm_source=Blog) to generate new ssh key.

2. Paste the text below, substituting in your GitHub email address.
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

3. To generate Agent pid
   ```bash
   eval "$(ssh-agent -s)"
   ```

4. To read the ssh key I went to the directory given by previous eval command and opened .pub file with notepad

5. Copied the ssh key and added it as a new ssh key on Github's 
   Acc settings > SSH Keys > New SSH Key(green button).

6. Went to repo's "Code" tab and clicked on "Code 🔽" green button and copied ssh url. 

7. Copied the SSH url which looks like ``` git@github.com:meetmakwana19/about-git.git ```

8. Have to set the Github's SSH url to the local machine 
```bash
git remote set-url origin git@github.com:meetmakwana19/about-git.git
```

9. To finally push the "master" branch on "origin" url 
```bash
git push -u origin master
```
(If once ```push -u origin``` is used then next time we just write ```git push``` which will by default push it the branch which was last commanded with ```-u```)

- To push another branches on GitHub ,
1. ```bash
   git checkout newBranch
   ```

2. ```bash
   git push -u origin 
   ```


# Miscellaneous 

### 1) Directly commit by skipping staging area

```bash
git commit -a -m "Skipped staging area and commited directly"
```
```-a``` is selecting All for stagging and ```-m``` is for Message.

### 2) Remove the file 

From local storage & staging area

```bash
git rm `filename`
```
From staging area only, local one will remain the same
```bash
git rm --cached `filename`
```

### 3) Shorthand for status

```bash
$ git status -s
MM  about.html(this will be in green meaning modified in staging area)(2nd M will be in red meaning modified in working tree)
M site.html (this will be in red meaning modified in working tree )
?? waste.html
```


### 4)  Clone Command 
   
1. Making a new folder on PC and opening git bash(by right click menu) over there to clone into that folder.

2. Will go to any public repository on Github and under code tab will copy the ```https``` link.

3. In the new folder's git bash we'll write 

   ```bash
   git clone https://github.com/meetmakwana19/To-Do-List.git meet
   ```
   where ```https....``` is the link of repo to be cloned and ```meet``` is the folder name where the repo to be closed inside our opened folder.

   ```bash
   git clone https://github.com/meetmakwana19/To-Do-List.git
   ```
   *If "meet" folder name not given then a folder of remote repository's name will be created.

### 5) Branch

- A branch is used to make a different workspace on the repository to dump/upload on that different branch to work separately without causing any trouble to the anothe branches.
- An analogy of a **Tree** is perfectt example to understand as different branches are separated on the same Tree where Tree is considered to be the repository.

- BY DEFAULT, BRANCH IS ***"MASTER"***.

TO CREATE A BRANCH

```bash
git branch `name_of_branch`
```

TO KNOW THE NAMES OF ALL BRANCHES:

```bash
git branch
```

SHORTHAND FOR CREATING AND ENTERING(SWITCHING TO IT) THE BRANCH AT THE SAME TIME

```bash
git checkout -b newBranch
```

TO SWITCH TO ANOTHER BRANCH

```bash
Meet@LAPTOP ~/OneDrive/Desktop/New folder (master)
$ git checkout feature1
```

***Switched to branch 'feature1'***

```bash
Meet@LAPTOP ~/OneDrive/Desktop/New folder (feature1)
$ git status
On branch feature1
nothing to commit, working tree clean
```

**Keep the file open and see the changes when switching between branches.

### 6) Logs

TO GET LOG OF ALL OUR COMMITS
```bash
git log
```

TO FILTER OUT LOGS OF COMMITS.

FOR EG. TO GET LAST 2 COMMITS (it also shows the changes)
```bash
git log -p -2
```
(press ```q``` to exit from the log viewer)

### 7)Comparison

WILL COMPARE AND SHOW THE DIFFERENCES BETWEEN THE CURRENT FILES(WORKING TREE) AND STAGED FILES
```bash
git diff
```

WILL COMPARE AND SHOW THE DIFFERENCES BETWEEN THE LAST COMMIT AND STAGED FILES
```bash
git diff --staged
```

### 8) .gitignore

```.gitignore``` file ignores all the files which are even in the the folders

SHOULD BE KNOWN : 
1. TO IGNORE ALL THE FILE-TYPES(.log), ADD THIS IS IN .gitignore
   eg: (.log)
   ```bash
   *.log
   ```

2. TO IGNORE A FOLDER USE A FORWAD SLASH
   ```bash
   `folder_name`/
   ```

### 9) Restore files

To restore files from last commit
Used to get back the last version of the file if someone has wrongly edited and saved it.
Essentially matching with the last commit !!
```bash
git checkout `filename`
```

To match all the files with last commit and change and them according to the last commit !!
```bash
git checkout -f
```



