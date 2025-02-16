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
		1. `git config --global user.email $email
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

`git checkout $branch` - swaps to a different branch

`git merge branch` - If you are in the master branch or any branch and want to merge with another. Once this comes up, you will be dumped into the vim editor, and can close this via ESC, then :quit

`git branch -a` - view all branches, both local and remote, remote branches will have the remotes/ prefix



### Remote Repos

Most commonly used platforms:

1. GitHub
2. GitLab
3. Bitbucket

Once you have initialized a repo on one of the platforms you can use the connection string (or URL) location.

Steps:
1. Log into Github or whatever
2. Create repository
3. Get connection string/url
4. Git remote add $alias $connectionstring

When adding a remote repository use the cmd below:

`git remote add origin $connectionstring`  - set origin to remote connection string so you know what you are working on

`git remote -v` - view all of your remote repositories

This will show fetch and pushes to the remote repository.

#### Pushing to remote Repo

`git push origin master` - This command always need two parameters, the alias of the remote repo (origin) and the branch you are currently on (master)

`git push $alias $remoteBranch` - sample of how structure is setup

Troubleshooting: If you end up getting 403 errors, (access denied) you may need to be given permissions (write) to the project within the platform you are using, i.e. Github, etc. Settings > Users > Collaboration > Find User > Grant Write


#### Cloning Repositories

`git clone [ ssh link ]` - clone repository

Within github, you can get the SSH key from the GitHub repo and the green Clone dropdown.

Pull down the repo to work with locally. 

Will have all of the git history in `git log`


#### Pull Requests

Also called PR.

Pull Requests have multiple properties that can be filled out for additional logging:
1. Title
2. Description
3. Labels
4. Specific Reviewers

Once a PR has been opened, other team members can see it and comment on it. When everything has been approved you can merge your pull request via the button to merge the changes into the Master branch. By default, not everyone has the privilege to merge pull requests <- this is by design.

Best practice is NEVER allow users push directly to Master, you have each contributor push to their own branch, then create a pull request, and after it is reviewed, someone will merge the pull request to master.

The master is supposed to be the clean production copy of the code.

When setting up the Pull Request, you can add a reviewer. The reviewer will have to login, click on the pull request, browse to the files changed folder, and then approve/reject (and can also add a comment).

It is possible someone approves the PR, but the owner of the master (or someone who has the appropriate permissions) will then have to login, view the PR, and actually merge it.



#### Git Fetch 

`git fetch origin master` - local repo is not automatically aware of the changes on the remote repository, this will update the local origin with the remote master repo. 

Next we need update the local master with the origin/master we just fetched.

`git merge origin/master` - merge the updates from the remote repo with your local master branch.

In addition to doing this, we can also pull the new contents down.

`git pull origin master` - fetch and merge the remote changes, directly into your local master branch



#### Merge Conflicts

Conflicts can occur when two people are editing the same file on their remote machine at the same time, and then attempt to push it back to the remote master. Git has a way of handling this.

If one user edits the file and updates it in master, that the other user attempts to push changes to master of his version of the file, the file will contain merge conflicts. How GIT handles this, is it can be viewed from the GUI or in the file there are additional lines added with both changes; i.e.:

file.txt
`## Story 4`
`<<<<< HEAD`
`This is the first to merge.`
`========`
`This is the second to merge.`
`>>>>>> second user`

Once the file has been edited, you will have to add the file again, i.e. `git add files.txt` and then it can be added via the merge command.
`git merge` - push the final copy that was edited to the master.

My notes: When editing the version of the file in vim, :w to save, :quit to quit, MAKE SURE you remove the <<<<<< line at the top, this took me a bit to figure out why the file was having issues. 

`git push origin master` - push the local edited file back up to the remote repo, after you have added and committed it.

#### Fork 

When wanting to collaborate on a project, you can fork which takes a copy of the remote project, and creates a remote copy for yourself to do with it as you please. Many times when multiple people are all working on the same open source project, you can allow them to fork and do all of the work on a separate instance of the project. At a later date, they can then initiate a pull request to merge the projects back with the original.

Checking user permissions in GitHub. Log into the platform, select the project. View settings > contributors, to see who has access, and what permissions. 

Steps to collaborate when forking a repository:
1. Browse to project
2. Select Fork
3. View your version of the project and get SSH or URL
4. Local machine clone the remote project `git clone $connectionstring`
5. Create files, add to stage, commit, push to remote repo
6. Create PR from your version of project > remote project







