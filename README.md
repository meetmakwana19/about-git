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
(your username as output)
```
```bash
git config --global user.email
(your email as output)
```



## Step 1

"touch" creates a new blank file  of .gitignore

```bash 
touch .gitignore
```

edit the .gitignore file and add the name of the folder which we dont want to upload 
    
## Step 2 

FYI : If we want to have a repository then 2 options we have, 

	1. git init (it initializes from the start)
	OR
	2. clone (it clones a repo we want and clones it's whole data from server)

Will create a .git file, keep hidden files enable to see it

```bash
git init
```

## Step 3 

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

