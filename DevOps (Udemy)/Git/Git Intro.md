#git 

# Git Introduction

Git allows for version control, a remote and local repository, and allows multiple users to collaborate on projects together. 


## Local Repository

The local repository is comprised of three separate sections:

### Working Area 

All files will be written locally and then pushed to a staging area. I.e. Story1.txt and Story2.txt from the local repository will be pushed up to the staging area.

### Staging Area

This is where all files will be placed before a developer is ready to commit the files which will then update the remote repository.
### Committed Files

Once a developer commits the files, the remote repository will be updated with the files, to include version contol.



### Sandbox Lab:

I am running this all from Windows so I am going to use Windows syntax instead of Linux but I want to document how I would do it in both OS's. My background is within windows.

1. Changed to a directory, and created a new directory for my project.
2. `Mkdir DevOps`
3. `Git init`
4. `echo "" >> story1.txt`
	1. In Linux you would utilize the **touch** command to make a new file
5. `echo "This is a beautiful story" > story1.txt`
6. `git status` to see untracked files and no commits yet

From here we want to add the file from the working area to the staging area
1. `git add story1.txt`
	1. I ran git status to ensure the file was in the "Changes to be committed section"
2. Add story to the committed files: `git commit -m "Added first story"` 
	1. I received errors with this as I never configured the actual user email or user name in my config settings. After I configured these I resubmitted the commit command successfully.
		1. `git config --global user.email jeromy.exe@gmail.com`
		2. `git config --global user.name "Jeromy"`
3. Added a second line to the file to view the modified file and see how git sees it
	1. `echo "This is my second line in my file." >> story1.txt`
		1. I then opened the file to ensure it took the line.
		2. `git status` shows: modified: story1.txt
		3. I see I can restore the file to the last commit before the modification, or i can run the add the modified file to the staging area
		4. `git add story1.txt`
			1. I run **git status** and I can see the file is staged, it can be undone if I wanted, and I am ready to commit the new file if I want
		5. `git commit -m "Updated the first story file."`

#### Using GIT to commit multiple files

1. `echo "This is line 3 of my story." >> story1.txt`
2. `echo "Git is fun" >> story2.txt`
3. `git status`
From here we can see story1.txt is in a modified state, while story2.txt is in a untracked state. If we wanted to we could add both files to the staging area to be committed.
4. `git add .`
5. `git status`
6. `git commit -m "Updated first story, and added second story."`
7. `git status` shows there is nothing to commit

Note: If multiple files were changed as part of a single change or for the same purpose, you can commit them together, HOWEVER, it is best practice to separate them and use separate commits if the two files are unrelated to each other. Each commit should be to solve a single problem, or add a single feature. When working with others it is important to keep the commits for a single specific feature, as it makes it easier to revert if there are ever any issues. Maybe even add a naming convention for changes?

### Other helpful commands:

`git rm --cached <file>` - this will pull the file back to a modified or "untracked" state.

`**Echo "<file>" >> .gitignore**` - this adds the file to the .gitignore file and will not be tracked, etc. 
For example, **.idea/** is a good directory to exclude as it is created by the IntelliJ Idea IDE, and is personal to the user. We do not want these to be checked in so you could add **.idea/** to the .gitignore file.


`git log` - this command shows you the username, time, file hash, and messages associated with commits.

By default this shows the author, date of commit, file hash, and commit message, but with **--name-only** switch you can also see the file name. 

`git log -n 1` - you can use this command to pull the last update


### Branches 

`git checkout -b <name>` - this creates a new branch named whatever you chose and then immediately switches to it

`git branch <name>` - this also creates a branch but does not switch to it

`git branch -d <name>` - this deletes a branch of your choosing

`git branch` - this shows all of the current branches that are available

HEAD is where you are currently located in the git repository. It points to the last commit in the branch you are currently on. Whenever you switch branches, the HEAD moves with you.



