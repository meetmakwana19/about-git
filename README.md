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

## **_1st time git setup_**

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

`(your username as output)`

```bash
git config --global user.email
```

`(your email as output)`

### STEP 1

(This step is optional is you already have an existing `.gitignore` file)
"touch" creates a new blank file of .gitignore

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

To put all the contents at staging area and `.` means staging all new and modified items excluding deleted ones.

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

To stage a New_folder(\*Remember, don't keep a space in the folder name and keep as eg. New_folder) :

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

- `git commit` means taking a snapshot

- So `git add` and `git commit` makes a snapshot associated to the changes we made

- But right now nothing is added to my repo so using message for commit as "Initial commit"

If this command is executed then an editor will open then press `i` to edit and write the message `Initial commit` and then press `Esc` key and then type `:wq` to save and exit the file.

```bash
git commit
```

---

- ALTERNATE EASY METHOD

```bash
git commit -m "Initial commit"
```

- I prefer the following commands as it skips staging and directly commits :
  - `-a` Commits modified and deleted files
  - Remember this following will mostly work when we have done tracking(staging) with the `git add` command atleast once for tha repository.

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

- If once `push -u origin` is used then next time we just write `git push` which will by default push it the branch which was last commanded with `-u`
- Technically, the `-u` flag adds a tracking reference to the upstream server you are pushing to.

What is important here is that this lets you do a `git pull` without supplying any more arguments.

For example, once you do a `git push -u origin master`, you can later call `git pull` and git will know that you actually meant `git pull origin master`.

Otherwise, you'd have to type in the whole command.

# Getting Started with ➡ Github ⬅

Make a repo on github with no files(no readme, etc) just as an example 😉

TO CONNECT TO GITHUB'S REMOTE REPOSITORY WITH OUR LOCAL REPOSITORY(Folder on the PC which we need to upload on github)

```bash
git remote add origin git@github.com:meetmakwana19/about-git.git
```

`git@github.com:meetmakwana19/about-git.git` is the **SSH** link of the github repository on which we want to connect and upload our local repository.
MEANING A REMOTE NAMED `origin` IS ADDED AND OUR URL CAN BE CALLED AS `origin`

- TO SEE REMOTE

```bash
git remote
```

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

3. To generate Agent pid (Execute this command in git bash if using Windows)
   ```bash
   eval "$(ssh-agent -s)"
   ```
   - Add private key to the ssh agent, change directory to the `.ssh` folder and try to run the folder command.
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

If things are not working out [check this](https://www.codewithharry.com/videos/git-tut-beginners-hindi-5)

4. To read the ssh key I went to the directory given by previous eval command and opened .pub file with notepad

5. Copied the ssh key and added it as a new ssh key on Github's
   Acc settings > SSH Keys > New SSH Key(green button).

6. Went to repo's "Code" tab and clicked on "Code 🔽" green button and copied ssh url.

7. Copied the SSH url which looks like `git@github.com:meetmakwana19/about-git.git`

---

### Using 2 github accounts in one computer (Please Ignore if not needed) :

- Do all the setps as above by starting with generating ssh keys for another email id like the following :

1. `ssh-keygen -t ed25519 -C "other_email@example.com"`
   1. Type the name of new file for saving key with complete path like : `C:\Users\meet.makwana/.ssh/id_ed25519_other`
   2. Copy paste the public key in your another github account's settings.
2. `eval "$(ssh-agent -s)"`
3. Add that other private key to the ssh-agent : `ssh-add ~/.ssh/id_ed25519_other`
4. Now your `.ssh/` folder has 2 private 2 public keys for 2 different github accounts.
5. Make a `config` file without any file extensions in your `.ssh/` folder and write the following into it :

```
# Default account (main account)
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519

# Other account
Host github-other.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_other
```

6. Now change the email id in your required directory for that other github word like `git config user.email "other_email@gmail.com"`
7. Now clone or push the repo related to that other account using that defined host like

```bash
git clone git@github-other.com:meetmakwana19/about-git.git
```

or

```bash
git remote set-url origin git@github-other.com:meetmakwana19/about-git.git
```

---

### Continued :

8. Have to set the Github's SSH url to the local machine

```bash
git remote set-url origin git@github.com:meetmakwana19/about-git.git
```

1. To finally push the "master" branch on "origin" url

```bash
git push -u origin master
```

(If once `push -u origin` is used then next time we just write `git push` which will by default push it the branch which was last commanded with `-u`)

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

`-a` is selecting All for stagging and `-m` is for Message.

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

For a folder (\*Remember, don't keep a space in the folder name and keep as eg. New_folder),

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

## 4) Clone Command

1. Making a new folder on PC and opening git bash(by right click menu) over there to clone into that folder.

2. Will go to any public repository on Github and under code tab will copy the `https` link.

3. In the new folder's git bash we'll write

   ```bash
   git clone https://github.com/meetmakwana19/To-Do-List.git meet
   ```

   where `https....` is the link of repo to be cloned and `meet` is the folder name where the repo to be cloned inside our opened folder.

   ```bash
   git clone https://github.com/meetmakwana19/To-Do-List.git
   ```

   \*If "meet" folder name not given then a folder of remote repository's name will be created.

4. Clone to a specific_branch

   ```bash
   git clone -b specific_branch remote_link_SSH_or_HTTPS
   ```

## 5) Branch

- A branch is used to make a different workspace on the repository to dump/upload on that different branch to work separately without causing any trouble to the anothe branches.
- An analogy of a **Tree** is perfectt example to understand as different branches are separated on the same Tree where Tree is considered to be the repository.

- BY DEFAULT, BRANCH IS **_"MASTER"_**.

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

**_Switched to branch 'feature1'_**

```bash
Meet@LAPTOP ~/OneDrive/Desktop/New folder (feature1)
$ git status
On branch feature1
nothing to commit, working tree clean
```

\*\*Keep the file open and see the changes when switching between branches.

## 6) Playing with branches

- To push to a specific branch to a remote names `origin`

```bash
git push origin branch_name
```

- To merge a specific branch with another branch say `master` branch then switch (`checkout`) to it and do the following

```bash
git merge specific_branch
```

- Delete a specific branch from the local repository

```bash
git branch -d specific_branch
```

- Delete a specific branch from the remote `origin`

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

(press `q` to exit from the log viewer)

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

`.gitignore` file has the list of all the files and folders which we dont want to track with git.
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

Can make a new folder and run `git init` by opening git bash in that folder.

```bash
git clone https_link
```

- Whereas `git pull` on the other hand is not same as clone command.
- So git pull means you are fetching the last modified changes from the remote repository and kinda refreshing your local repository to get the changes.
- It will be often used while a team is collaborating on a repo.
- It is basically `git fetch` + `git merge`.

```bash
git pull https_link
```

So,

> **Clone**: Get a working copy of the remote repository.

> **Pull**: I am working on this, please get me the new changes that may be updated by others.

`git clone <remote-url>`

- create a new directory
- `git init` // init new repository
- `git remote add origin <remote-url>` // add remote
- `git fetch` // fetch all remote branchs
- `git switch <default_branch>` // switch to the default branch

`git pull`

- fetch ALL remote branches
- merge CURRENT local branch with tracking remote branch (not another branch) (if local branch existed)

`git pull <remote> <branch>`

- fetch the remote branch
- merge CURRENT local branch with the remote branch (if local branch existed)

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

### Remove commited files from commit level and unstage them without losing changed data :

```bash
git reset HEAD~1
```

Instead of 1, there could be any number of commits you want to unstage.

## 13) To undo changes in the file at local level :

It's basically `Ctrl+Z`
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

`revert HEAD` reverts the current state(HEAD) to the last commit.

```bash
git revert HEAD
```

### ii) To go back to a specific commmit

`12abc34` is the 7 digit example git commit ID.
To know the git commit IDs of all the commits made.

```bash
git log --oneline
```

Then use that ID for revert command.

```bash
git revert 12abc34
```

After this command your terminal's text editor(Most likely Vim for git bash) will open and don't do anything if you dont want to write a custom commit message.
Just do `:wq` to save and exit the text editor which will make the revert work.

If you want to write your custom git message then press `i` and start editing the first line on the editor and then exit the edit mode by pressing `Esc` key and then `:wq`.

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

**_Then_**,

```bash
git push
```

## 15) `git reset` - To destroy previous commits

Say there are 5 commits, 1 being oldest(first) and 5 being latest.
Now you want to go to 2nd commit and delete all 3rd,4th,5th commits.
I mentioned DELETE i.e remove it's history totally and not like `git revert` command.

`git reset` is very powerfull to destroy those commits.
**_2 types :-_**

### 1) `git reset --hard`

`--hard` will remove the commits history and undo changes of the commits at both local and remote levels.
40 digits commit ID mentioned in the command is where we want to shift our HEAD(Pointer) to and delete every commit above it.

```bash
git reset --hard 4e28d49dc37b66v755b6f95dc70c8e579z3830f8
```

The above ID is example and please dont try to copy paste the same ID.

Then use `-f` flag which means push forcibly.

```bash
git push -f origin myBranch
```

Need to force push like this because we came back in the commits history on local level using `git reset`

But the remote is ahead of local in commits as the changes aren't yet pushed.

Thereforce, will need to force the push using `-f`.

### 2) `git reset --soft`

`--soft` will destroy commits at remote level as well as local level
**BUT** won't undo/revert the changes of the destroyed commits at local repository. Therefore, called as soft reset.

```bash
git reset --soft HEAD~x
```

`~` = Tilde sign
`x` = number how much back in commit history you want to go.
Example : `HEAD~3` means go back three commmits from the HEAD.
Then, we'll offcourse have to push the changes which will delete the commits even from the remote and won't display them.

- 2 ways to push forcibly,
  `git push` or `git push -u origin` wont work as we want to force push🌝

```bash
git push origin +master
```

Or

```bash
git push origin +master --force
```

⚠ However, a huge downside of these `reset` commands(both hard and soft) is that it just makes the commmit invisible from our github repository

But when we have the exact link to the destroyed commit then we can access it's full files like try [this](https://github.com/meetmakwana19/testing/commit/3b008dd555f0933ccdcd5893d4aa71413c41a55f)

⚠Also, if there is only one commit in the repository then that cannot be deleted by these commands as these command take the Head to the mentioned commit by deleting the ones above it and not destroy the mentioned commit.

#### Important lesson I learnt

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

## 16) Rename message of last commit

```bash
git commit --amend
```

After this command your terminal's text editor(Most likely Vim for git bash) will open.

To write your message press `i` and start editing the first line on the editor and then exit the edit mode by pressing `Esc` key and then `:wq`.

## 17) Alter details of previous commits :

If you want to change the dates of multiple commits, you can do so by using an interactive rebase.

1. Start an Interactive Rebase
   1. Decide how many commits back you want to change. For example, if you want to modify the last 3 commits:
   2. This will open your default text editor with a list of the last 3 commits.

```bash
git rebase -i HEAD~3
```

2. Edit the Commits

   1. In the editor, you'll see something like this:
   2. The commits will be arranges in a fashion of newest to be at the bottom.

   ```bash
   pick commit_hash Commit_message_3
   pick commit_hash Commit_message_2
   pick commit_hash Commit_message_1
   ```

   3. Enter `i` key to enter the insert mode.
   4. Change `pick` to `edit` for each commit whose date you want to modify:

   ```bash
   pick commit_hash Commit_message_3
   edit commit_hash Commit_message_2
   edit commit_hash Commit_message_1
   ```

   5. Save and close the editor by pressing `esc` key and the typing `:wq` and press `Entern`.

3. Amend Each Commit

   1. Git will stop at each commit, allowing you to amend it like :

   ```bash
   Stopped at ef121d1...  L25: Added explicit address typecasting theory
   You can amend the commit now, with

   git commit --amend

   Once you are satisfied with your changes, run

   git rebase --continue
   ```

   2. For each commit, run:

   ```bash
   git commit --amend --date="YYYY-MM-DDTHH:MM:SS"
   ```

   3. This will also open the editor. Save and exit it.
   4. Continue the Rebase. This will move on to the next commit in the rebase sequence.

   ```bash
   git rebase --continue
   ```

   5. Edit the Next Commit (If Needed).

4. Rebase and update the branch after completing all the edit :

```bash
git rebase --continue
```

5. Now just push the changes. If you previously pushed these commits to a remote repository, you'll need to force push to update the remote branch with your new commit history:

```bash
git push --force-with-lease
```

## 18) Amend old commit and delete everything above it without losing its content : 

If you want to 
- reset your branch to a specific commit, 
- discard all commits above it, 
- amend that commit with new changes, 
- and push it back to the remote branch. 

Here’s how to do it:

1. Reset your branch to the target commit and get all the changes after that commit to the staging level 

```bash
git reset --soft <commit-hash>
```
--soft keeps all changes staged.

2. Get those staged changes out of staging and make the necessary changes you wished to get in that commit
3. Stage back all the changes 
4. Amend the commit

```bash 
git commit --amend
```
This will update the commit message and include new changes.

5. Force push the updated commit, 

Since this rewrites history, you need to force push:

```bash
git push --force-with-lease
```

## 19) How to insert image in markdown ?

```bash
![alt text for screen readers](/path/to/image.png "Text to show on mouseover")
```

## 20) How to color text in markdown ?

```bash
<span style="color:yellow">some *yellow* text</span>
```

## 21) Stash command

- Used when we want to save current working directory/branch's work which can be incomplete and proceed to some other branch's work
- Useful while switching branches
- Useful when dont wanna commit incomplete progress of current branch.
- Normally we commit and then switch branches
- But if switching without doing a commit then 2 of the following things can either happn
  1. Switch to other branch carrying changes to other changes
  2. Git wont allow to switch and will ask to commit/stash the changes
- The command allows switching branches without commiting to the current branch
- `Stash` meaning is "to store something safely ata hidden place".
- So git temporarily saves the data without committing
- Simple easiest way to stash current work in the current branch is

```
git stash
```

- Giving name to the stash

```
git stash save cool_name
```

- Listing the available stashes

```
git stash list
```

- To get a specific stash back

```
git stash apply `index`
```

- TO get back the stashed changes

```
git stash pop
```

## 22) Commit in the past

```bash
git commit --date='year-month-day hour:minutes:seconds' -m "message"
```

So it would look something like this:

```bash
git commit --date='2024-07-11 12:12:00' -m "message"
```

## 23) Tags

- Tags are ref's that point to specific points in Git history.
- Tagging is generally used to capture a point in history that is used for a marked version release (i.e. v1.0.1).
- A tag is like a branch that doesn’t change.
- Unlike branches, tags, after being created, have no further history of commits.
- Git supports **two types** of tags: `lightweight` and `annotated`.
  - A **lightweight tag** is very much like a branch that doesn’t change — it’s just a pointer to a specific commit.
  - **Annotated tags**, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG).
  - It’s **generally recommended** that you **create annotated tags** so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

### Listing Your Tags :

- Listing the existing tags in Git is straightforward. Just type `git tag` (with optional `-l` or `--list`):

```bash
git tag
```

- This command lists the tags in alphabetical order; the order in which they are displayed has no real importance.
- You can also search for tags that match a particular pattern.

```bash
 git tag -l "v1.8.5*"
```

### Creating Tags :

**Annotated Tags**

```bash
git tag -a v1.4 -m "my version 1.4"
```

- You can see the tag data along with the commit that was tagged by using the `git show` command:

```bash
git show v1.4
```

**Lightweight Tags**

- To create a lightweight tag, don’t supply any of the `-a`, `-s`, or `-m` options, just provide a tag name:

```bash
git tag v1.4-lw
```

### Tagging Later :

- You can also tag commits after you’ve moved past them.

```bash
git tag -a v1.2 9fceb02 - m "my version v1.2"
```

### Push tags :

- By default, the git push command doesn’t transfer tags to remote servers
- This process is just like sharing remote branches — you can run `git push origin <tagname>`.

```bash
git push origin v1.5
```

- OR you can also use the `--tags` option to transfer all the tags.

```bash
git push origin --tags
```

```bash
git push --tags
```

### Deleting Tags :

- On local level

```bash
git tag -d v1.4-lw
```

- On remote level

```
git push origin --delete v1.4
```


## 24) Rebasing your branch with the base branch 

1. To rebase your branch on the latest main and maintain a linear history, run:

```base
git fetch origin
git rebase origin/main
```

2. If there are conflicts, Git will prompt you to resolve them. After resolving, continue rebase with:

```bash
git rebase --continue
```

3. Once the rebase is done, push the updated history. Again, this requires a force push since you rewrote the commit history.

```bash
git push origin <your-branch> --force
```

## 25) Get back committed changes from commit level to stage level 

- Say you have a series of linear commits like the following 

```bash
62a1b7d (HEAD -> updates, origin/updates) chore: fixed messed up serial numbers
0071e39 Merge remote-tracking branch 'origin/master' into updates
2c3957a feat: added rebasing info
2675d8d (origin/master, origin/HEAD) Merge pull request #2 from meetmakwana19/updates
```

- And you wish to get all the changes done in the top 3 commits back to stag level so you reset your branch to the commit below it i.e. `2675d8d`.

```bash
git reset 2675d8d
```

- Now your git history will look like : 

```bash 
2675d8d (origin/master, origin/HEAD) Merge pull request #2 from meetmakwana19/updates
.
.
```
- Now your committed changes will be brought back to the staging level from where you can bring it out of stag and edit and restage and commit back.

## Error :Object file is empty ? .git is corrupt ?

Error can look something like this :

```
error: object file .git/objects/5c/e7c038a18323acee48ad13 is empty

fatal: loose object 5ce7c038a213 (stored in .git/objects/5c/e7c038a183d883) is corrupt
```

Solution learned from https://stackoverflow.com/a/31110176/17796286

Solution :

```
find .git/objects/ -type f -empty | xargs rm
git fetch -p
git fsck --full
```

1. Finding empty .git object files and then `xargs rm` takes the list of empty files provided by find and passes them as arguments to the rm command, which removes the files
   1. `|` pipe connects the standard output (stdout) of the command on the left side of the pipe to the standard input (stdin) of the command on the right side
2. `git fetch` updates the remote-tracking branches in your local repository to match the state of the remote repository.
   1. The `-p` or `--prune` option is used to remove any remote-tracking branches that no longer exist on the remote repository.
   2. This command is used to retrieve the latest changes and objects from the remote repository.
3. `git fsck --full` This command performs a full object store check in the Git repository.
   1. `git fsck` (file system consistency check) is a command used to check the integrity of the Git repository's object database.
   2. The `--full` option ensures that all objects are checked, including those that are not reachable from any branch or tag.
   3. The purpose of this line is to verify the integrity of the object store and ensure there are no remaining corruption issues.
      Overall, these commands aim to fix a broken Git repository by removing empty object files, fetching missing objects from the remote repository, and performing a comprehensive integrity check.

in Short,

1. remove any empty object files that cause corruption
2. fetch down the missing objects (as well as latest changes)
3. do a full object store check

- If Error on

```bash
find .git/objects/ -type f -empty | xargs rm

rm: missing operand
```

So add `-r` flag in the `rm` command like

```bash
find .git/objects/ -type f -empty | xargs -r rm
```

- If Error on

```bash
git fetch -p

error: refs/heads/main does not point to a valid object!
fatal: bad object HEAD
```

Try this shell script : [Refer](https://stackoverflow.com/questions/6265502/getting-rid-of-does-not-point-to-a-valid-object-for-an-old-git-branch)

```bash
git for-each-ref --format="%(refname)" | while read ref; do
    git show-ref --quiet --verify $ref 2>/dev/null || git update-ref -d $ref
done
```

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
