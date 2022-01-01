
# Git Cheatsheet 

If you have any doubt/question then please feel free to raise the issue on github or can contact me on my other social media profiles and link of those social media profiles
can be found on my github profile page. And also if there's any correction or new addition from your side for my cheatsheet then I would be priviliged to get your contritbution. 🙏🏻
Hope you have a good time here 🥰
 
 All the following steps are prefered to be followed and executed on 'Git Bash' after installing it on your machine.

To check your git version

```bash
git --version
```

- Three cases:

If your Git version is 2.14.1 or earlier:

Uninstall Git, download the latest [Git](https://git-scm.com/downloads), and install it again.

And versions between 2.14.2 and 2.16.1:

Use command 
```bash
git update
```

If the version is equal to or greater than Git 2.16.1(2):

Use command 
```bash
git update-git-for-windows
```
## ***1st time git setup***

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
(This step is optional is you already have an existing ```.gitignore``` file)

"touch" creates a new blank file  of .gitignore

```bash 
touch .gitignore
```

edit the .gitignore file and add the name of the folder which we dont want to upload 
    
### STEP 2 - Initialization

FYI : If we want to have a repository then 2 options we have, 

	1. git init (it initializes from the start)
	OR
	2. clone (it clones a repo we want and clones it's whole data from server)

Will create a .git file, keep hidden files enable to see it

```bash
git init
```

### STEP 3 - Staging

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

To put all the contents at staging area and ```.``` means staging all new and modified items excluding deleted ones.

```bash
git add .  
```

If dont want to put all files then use the following syntax 

```bash
git add filename
```

If want to put **all the files** of the directory at staging then, 

```bash
git add -A
```

If want to put only the modified and deleted items at staging then,

```bash
git add -u
```

To stage a New_folder(*Remember, don't keep a space in the folder name and keep as eg. New_folder) :

```bash
git add New_folder/
```

To stage say a specific.txt file in a nested folder :
```bash
git add folder1/folder2/folder3/specific.txt
```

👉🏻 Can check status ✔ now by 

```bash
git status
```


### STEP 4 - Commit

- ```git commit``` means taking a snapshot 

- So ```git add``` and ```git commit``` makes a snapshot associated to the changes we made

- But right now nothing is added to my repo so using message for commit as "Initial commit"

If this command is executed then an editor will open then press ```i``` to edit and write the message ```Initial commit``` and then press ```Esc``` key and then type ```:wq``` to save and exit the file.

```bash
git commit
```
---
- ALTERNATE EASY METHOD

```bash
git commit -m "Initial commit"
```

- I prefer the following commands as it skips staging and directly commits :
    - ```-a``` Commits modified and deleted files
    - Remember this following will mostly work when we have done tracking(staging) with the ```git add``` command atleast once for tha repository.

```bash
git commit -a -m "msg"
```
Or
```bash
git commit -am "msg"
```
---

- If want to commit one one files separately with seaparate messages then, 


```bash
git add file1.txt
```
```bash
git commit -m "Commiting file1.txt with custom message"
```
Similarly,
```bash
git add file2.txt
```
```bash
git commit -m "Commiting file2.txt with custom message"
```

- To know if commit is done, check the log which will give information about about all commits.

```bash
git log --oneline
```
## Commit done 🎉 , now Push remaining 

To finally push the "master" branch on "origin" url 

```bash
git push -u origin master
```

- If once ```push -u origin``` is used then next time we just write ```git push``` which will by default push it the branch which was last commanded with ```-u```
- Technically, the ```-u``` flag adds a tracking reference to the upstream server you are pushing to. 

What is important here is that this lets you do a ```git pull``` without supplying any more arguments. 

For example, once you do a ```git push -u origin master```, you can later call ```git pull``` and git will know that you actually meant ```git pull origin master```.

Otherwise, you'd have to type in the whole command.
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

If things are not working out [check this](https://www.codewithharry.com/videos/git-tut-beginners-hindi-5)

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

- To push to another branches on GitHub ,
1. ```bash
   git checkout newBranch
   ```

2. ```bash
   git push -u origin 
   ```


# Miscellaneous 

## 1) Directly commit by skipping staging area

```bash
git commit -a -m "Skipped staging area and commited directly"
```
```-a``` is selecting All for stagging and ```-m``` is for Message.

## 2) Remove the file 

From local storage & staging area

```bash
git rm `filename`
```
From staging area only, local one will remain the same
```bash
git rm --cached `filename`
```
---
- Delete file/folder from remote repository :

1] First deleting from local & staging area.
```bash
git rm --cached `filename`
```
For a folder (*Remember, don't keep a space in the folder name and keep as eg. New_folder),
```bash
git rm --cached -r New_folder/
```
2] Then just commit nd push the changes.
```bash
git commit -m "Removed"
```
```bash
git push
```

---

- Delete multiple files in one go 😎

1] From both local and remote repository
```bash
git rm file1.png file2.txt file3.py 
```
Or

1] From only remote repository while keeping the local one untouched. 
```bash
git rm --cached file1.png file2.txt file3.py 
```
2] Then just commit nd push the changes.
```bash
git commit -m "Removed"
```
```bash
git push
```



## 3) Shorthand for status

```bash
$ git status -s
MM  about.html(this will be in green meaning modified in staging area)(2nd M will be in red meaning modified in working tree)
M site.html (this will be in red meaning modified in working tree )
?? waste.html
```


## 4)  Clone Command 
   
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

## 5) Branch

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

## 6) Playing with branches

- To push to a specific branch to a remote names ```origin```

```bash
git push origin branch_name 
```

- To merge a specific branch with another branch say ```master``` branch then switch (```checkout```) to it and do the following

```bash
git merge specific_branch
```

- Delete a specific branch from the local repository

```bash
git branch -d specific_branch
```

- Delete a specific branch from the remote ```origin```

```bash
git push origin --delete specific_branch
```

- To rename any_branch 

```bash
git branch -m new_name
```
---

Then after all these or any of these push changes forcibly,

```bash
git push -f origin myBranch
```

## 7) Logs

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

## 8)Compare changes 

WILL COMPARE AND SHOW THE DIFFERENCES BETWEEN THE CURRENT FILES(WORKING TREE) AND STAGED FILES
```bash
git diff
```

WILL COMPARE AND SHOW THE DIFFERENCES BETWEEN THE LAST COMMIT AND STAGED FILES
```bash
git diff --staged
```

## 9) .gitignore

```.gitignore``` file has the list of all the files and folders which we dont want to track with git.

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

## 10) Restore files

To restore files from last commit.
Used to get back the last version of the file if someone has wrongly edited and saved it.
Essentially matching with the last commit !!
```bash
git checkout `filename`
```

To match all the files with last commit and change and them according to the last commit !!
```bash
git checkout -f
```

## 11) Get the remote repository to local PC

Can make a new folder and run ```git init``` by opening git bash in that folder.

```bash
git clone https_link
```
Or

~~~bash
git pull https_link
~~~

## 12) Removing Staged files from Staging level

```bash
git restore --staged staged_file_name_or_path
```

```bash
git reset staged_file_name_or_path
```

```bash
git reset HEAD staged_file_name_or_path
```
HEAD points to location at which our repository is at current state at current time & space.

- To remove all staged files from staging area

```bash
git restore --staged 
or 
git restore --staged .
```

```bash
git reset 
```

```bash
git reset HEAD 
or
git reset HEAD .
or
git reset HEAD --
```

## 13) To undo changes in the file at local level : 

It's basically ```Ctrl+Z```
IMP : But it's different because the file is not yet commited/staged.

```bash
git revert file.txt
```
Or
```bash
git checkout -- file.txt
```



## 14) Getting back to previous commit 

### i) To go back to previous commit 
```revert HEAD``` reverts the current state(HEAD) to the last commit.
```bash
git revert HEAD
```

### ii) To go back to a specific commmit 

```12abc34``` is the 7 digit  example git commit ID.

To know the git commit IDs of all the commits made. 

```bash
git log --oneline
```

Then use that ID for revert command.
```bash
git revert 12abc34
```
After this command your terminal's text editor(Most likely Vim for git bash) will open and don't do anything if you dont want to write a custom commit message. 
Just do ```:wq``` to save and exit the text editor which will make the revert work.

If you want to write your custom git message then press ```i``` and start editing the first line on the editor and then exit the edit mode by pressing ```Esc``` key and then ```:wq```.

- **Another way**, 

To know the git commit IDs(40 characters long) of all the commits made. 

[Press ```q``` to exit the editor viewer after ```git log``` command.]
```bash
git log 
```

Then use that 40 characters long ID for revert command.
```bash
git revert 4e28d49dc37b66v755b6f95dc70c8e579z3830f8
```
The above ID is example and please dont try to copy paste the same ID

***Then***, 
```bash
git push
```

## 15) ```git reset``` - To destroy previous commits

Say there are 5 commits, 1 being oldest(first) and 5 being latest.
Now you want to go to 2nd commit and delete all 3rd,4th,5th commits.
I mentioned DELETE i.e remove it's history totally and not like ```git revert``` command.

```git reset``` is very powerfull to destroy those commits.

***2 types :-*** 

### 1) ```git reset --hard``` 

```--hard``` will remove the commits history and undo changes of the commits at both local and remote levels.

40 digits commit ID mentioned in the command is where we want to shift our HEAD(Pointer) to and delete every commit above it.

```bash
git reset --hard 4e28d49dc37b66v755b6f95dc70c8e579z3830f8
```
The above ID is example and please dont try to copy paste the same ID. 

Then use ```-f``` flag which means push forcibly.

```bash
git push -f origin myBranch
```

Need to force push like this because we came back in the commits history on local level using ```git reset```

But the remote is ahead of local in commits as the changes aren't yet pushed.

Thereforce, will need to force the push using ```-f```.

### 2) ```git reset --soft```

```--soft``` will destroy commits at remote level as well as local level

**BUT** won't undo/revert the changes of the destroyed commits at local repository. Therefore, called as soft reset. 

```bash
git reset --soft HEAD~x
```
```~``` = Tilde sign

```x``` = number how much back in commit history you want to go.

Example : ```HEAD~3``` means go back three commmits from the HEAD.

Then, we'll offcourse have to push the changes which will delete the commits even from the remote and won't display them.

- 2 ways to push forcibly,

```git push``` or ```git push -u origin``` wont work as we want to force push🌝

```bash
git push origin +master
```
Or
```bash
git push origin +master --force
```

⚠ However, a huge downside of these ```reset``` commands(both hard and soft) is that it just makes the commmit invisible from our github repository

But when we have the exact link to the destroyed commit then we can access it's full files like try [this](https://github.com/meetmakwana19/testing/commit/3b008dd555f0933ccdcd5893d4aa71413c41a55f)

⚠Also, if there is only one commit in the repository then that cannot be deleted by these commands as these command take the Head to the mentioned commit by deleting the ones above it and not destroy the mentioned commit.

## 16) Rename message of last commit 

```bash
git commit --amend
```

After this command your terminal's text editor(Most likely Vim for git bash) will open.

To write your message  press ```i``` and start editing the first line on the editor and then exit the edit mode by pressing ```Esc``` key and then ```:wq```.
# Important lesson I learnt

I wanted to unstage all the staged files so used the command `git reset HEAD`

But unknowingly I deleted dozens of important files from my local repository.

So the followings steps to take in such situation to restore the file of the local repository.

- Git keeps a log of all ref updates (e.g., checkout, reset, commit, merge). You can view it by typing:

```bash
git reflog
```

Somewhere in this list is the commit that you lost. 

Let's say you just typed `git reset HEAD` and want to undo it. My reflog looks like this:

![Screenshot](./ss.png "Preview image")

The first line says that HEAD 0 positions ago (in other words, the current position) is 8efd6f0.
It was obtained by resetting to HEAD~. 
The second line says that HEAD 1 position ago (in other words, the state before the reset) is f7e9df2. 
It was obtained by checking out a particular commit (though that's not important right now). 

So, to undo the reset and go to a specific commit (85bfa92- where I want to go back, from where I lost the data) 
```bash
git reset 'HEAD@{4}'
```
or
```bash
git reset 85bfa92
```

This will give lost of all files which were lost.

To obtain then back, we'll use the command `checkout`

```bash
git checkout 22_Class_Based_Components.md 22_news_app/.gitignore 22_news_app/README.md 22_news_app/SampleResponse.json 22_news_app/package-lock.json 22_news_app/package.json 22_news_app/public/favicon.ico 22_news_app/public/index.html 22_news_app/public/logo192.png 22_news_app/public/logo512.png 22_news_app/public/manifest.json 22_news_app/public/robots.txt 22_news_app/src/App.css 22_news_app/src/App.test.js 22_news_app/src/components/loading.gif 22_news_app/src/index.css 22_news_app/src/index.js 22_news_app/src/logo.svg 22_news_app/src/reportWebVitals.js 22_news_app/src/setupTests.js 23_Components_structuring.md 24_News_API.md 25_rcc_States.md 26_Looping_array.md 27_Fetching_from_API.md 28_Next_Previous_pages.md 29_Loading_Spinner&variable_pageSize.md 30_Categories&propTypes.md
```
Writing the names of all files together to restore them in one go.

## 17) How to insert image in markdown ? 

```bash
![alt text for screen readers](/path/to/image.png "Text to show on mouseover")
```

## 18) How to color text in markdown ?

<span style="color:yellow">some *yellow* text</span>
# Simple Walkthrough for Pushing

## Do the following when understood all of the above steps

### Applicable when want to push a local project to a new github repository

```bash
git init
```
```bash
git remote add origin git@github.com:SSH_LINK.git
```
```bash
git remote
```

```bash
git status
```
Status will show that no commits and untracted files are there excluding the ones which are listed in .gitignore

```bash
git add -A
```
```bash
git commit -m "msg"
```

```bash
git push -u origin master
```




## Related

Here is a related article which is really good and can be used as Git cheat-sheat too.

[javatpoint](https://www.javatpoint.com/git)

