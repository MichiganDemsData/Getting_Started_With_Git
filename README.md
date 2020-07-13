# Getting Started with Git

# Version Control 101
## Introduction
> “The past is never where you think you left it.” — Katherine Anne Porter

Version Control is the process of storing multiple versions of a single project, allowing each version to be recalled at a later date.  

There are a lot of different ways to do version control. You could save a new file every time you make a change, time-stamp that file, and place all of those files into a timestamped folder. You could track all of your changes in a spreadsheet with copious notes. Or you could use dedicated version control software. Guess which method programmers use?

### Objectives
You will be able to:
Describe the purpose of version control and Git

### Why Use Version Control?  

Let's think about the future for a second. You just deployed a new chat feature for the app you're working on. Suddenly, your boss runs over to your desk: "Wait! We can't deploy the chat yet! Revert! Revert!"  

What do you do? You need to find all of the new code you pushed to the server and delete it. Then you need to find the old code, test it, and re-upload it. So much work to do. Well, since you used version control software, it's as easy as 1, 2, 3. Actually, it's as easy as git reset --hard <commit id>... but we'll get to that later. Using version control is useful because it allows you to easily rollback to a previous version of your application, saving you a ton of extra work and time.

There are a lot of advantages to version control. It's a great way to keep a backup of your work, it facilitates collaboration, and it gives you the freedom to experiment and try new things without messing up the code base.

### Local vs Remote Version Control
A local version control system stores all of the information on your computer, locally. This system works great while you work on a project by yourself. However, it becomes cumbersome when you attempt to collaborate.

Some organizations use a centralized repository on a company server. Think of a repository as a big folder that stores all of the files of a particular project. It is simply the location where a project's data is stored. Users pull only the files they need to work on from the server. The advantage is that multiple people can collaborate and work on the same project at once. The disadvantage of this process is that a user must be connected to the network in order to work on the project.

Which brings us to the third system, a distributed version control system. In a distributed system, all users have a complete copy of the entire repository. This means that you can work on the project independent of any network connection. Upon reconnecting, you can push your changes to the server and merge with the server's repository.

### Meet Git
Git is a distributed version control system and the preferred system of most developers, since it has multiple advantages over the other systems available. It stores file changes more efficiently and ensures file integrity better. If you’re interested in knowing the details, the Git Basics page has a thorough explanation on how Git works.

#### Resources
[Getting Started - About Version Control](http://git-scm.com/book/en/Getting-Started-About-Version-Control)  
[Git Basics - What is Git?](http://git-scm.com/video/what-is-git)   

# Starting a new Github Account and Git
## Introduction
Git is a version control system. GitHub is an online hosting platform that uses Git.

### Objectives
You will be able to:
- Create your Github account
- Install Git locally on your computer
- Securely store your credentials with the credential helper
- Setup two-factor authentication

## Prerequisites
You will need these apps before you begin. 1Password and Authy are recommended.  

Password Manager (Installs on your computer. Recommended install on phone)  
 - 1Password: DNC recommended. Subscriptions available to campaigns.   
 - LastPass: Free and widely available.
Mobile Authentication App (For 2 Factor Authentication. Installs on your phone)  
 - Authy: DNC recommended. Free. Can bulk import between Androids and IPhones
 - Google Authenticator: Free. Widely used on android devices.

## Create your Github Account
Go to Github’s home page and create an account user name, email and a password. Use 1Password’s password generator to create and securely store your new password.

Verify your account using your email address.
Email your [administrator](mailto:eric@michigandems.com) with your Github username and associated email address. Contact them via Slack if there are any issues.

## Installing Git locally
Resources: https://www.atlassian.com/git/tutorials/install-git        
https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token

### Install Git on Mac OS X
There are several ways to install Git on a Mac. In fact, if you've installed XCode (or it's Command Line Tools), Git may already be installed.
To find out, open a terminal and enter git --version.  

    $ git --version  
	git version 2.20.1   
Apple actually maintains and ships their own fork of Git, but it tends to lag behind mainstream Git by several major versions. You may want to install a newer version of Git using one of the methods below:
### Git for Mac Installer
The easiest way to install Git on a Mac is via the stand-alone installer:  
Download the latest [Git for Mac installer](https://sourceforge.net/projects/git-osx-installer/files/).
Follow the prompts to install Git.
Open a terminal and verify the installation was successful by typing git --version:

    $ git --version
    git version 2.20.1


Configure your Git username and email using the following commands, replacing Emma's name with your own. These details will be associated with any commits that you create:

    $ git config --global user.name "Eric Ma"
    $ git config --global user.email "eric.ma@digidems.com"

## Create your Personal Access Token
> If you’ve set up an SSH or a different Personal Access Token you can skip this step.  

You should create a personal access token to use in place of a password with the command line or with the API. Personal access tokens (PATs) are an alternative to using passwords for authentication to GitHub. As a security precaution, GitHub automatically removes personal access tokens that haven't been used in a year.  

Create your token. On the upper-right corner of your Github page go to Settings

On the left-hand sidebar find Developer Settings > Personal Access Tokens

Generate and name your token.

Select the scopes, or permissions, you'd like to grant this token. To use your token to access repositories from the command line, select repo.

Click Generate token.

Click the clipboard to copy the token to your clipboard. For security reasons, after you navigate off the page, you will not be able to see the token again.

Open 1Password and under Github click Edit. You can see your GitHub password by holding down the alt key. Do not change your current password. Under Section > new field click the pull down and add a Password. In the new password field paste and save your Personal Access Token. You can label the new section ‘PAT’.

The next time git prompts you for a password from the Command Line, open 1Password and copy and paste your Personal Access Token from your notes.

    $ git clone https://github.com/username/repo.git
    Username: your_username  
    Password: your_token  
Personal access tokens can only be used for HTTPS Git operations. If your repository uses an SSH remote URL, you will need to switch the remote from SSH to HTTPS.  
## (Optional) Install the git-credential-osxkeychain helper
Bitbucket supports pushing and pulling your Git repositories over both SSH and HTTPS. To work with a private repository over HTTPS, you must supply a username and password each time you push or pull. The git-credential-osxkeychain helper allows you to cache your username and password in the OSX keychain, so you don't have to retype it each time.  

Check your terminal to see if git-credential-osxkeychain is already installed

$ git credential-osxkeychain
usage: git credential-osxkeychain <get|store|erase>

If you receive a usage statement, skip to step 4. If the helper is not installed, go to step 2


Use curl to download git-credential-osxkeychain (or download it via your browser) and move it to /usr/local/bin:

    $ curl -O http://github-media-downloads.s3.amazonaws.com/osx/git-credential-osxkeychain
    $ sudo mv git-credential-osxkeychain /usr/local/bin/


Make the file an executable:

    $ chmod u+x /usr/local/bin/git-credential-osxkeychain


Configure git to use the osxkeychain credential helper.

    $ git config --global credential.helper osxkeychain


The next time Git prompts you for a username and password, it will cache them in your keychain for future use. Use your Personal Access Token in place of a password.
## Turn on 2-Factor Authentication
Two-factor will be required for joining an organization.

In the upper-right corner of any page, click your profile photo, then click Settings.

In the user settings sidebar, click User Security
Under "Two-factor authentication", click Enable two-factor authentication.

On the Two-factor authentication page, click Set up using an app.

Save your recovery codes in the notes section of 1Password

On the Two-factor authentication page, do one of the following:

Scan the QR code with your mobile device's app, either 1Password or Authy. After scanning, the app displays a six-digit code that you can enter on GitHub.

If you can't scan the QR code, click enter this text code to see a code you can copy and manually enter on GitHub instead.

Enter the 6-digit code from you Authenticator and click Enable.

#### Install Git on Windows  
To be added.  
#### Install Git on Linux  
To be added.  

# Getting Started with Git in Bash
## Introduction
Git commands can be run in the bash shell. Bash
### Objectives
You will be able to:
- Describe the difference between a forked and a cloned repository
- Use git add, git commit, and git push to make changes to a repository
- Compare local and remote repositories

### Some terminology and concepts
As you can see from the objectives above, we're going to dive in and use several Git commands in this lesson.

The first thing we'll look at is a git clone from a bash shell like terminal or git bash in order to copy the material from the web to our local computer.

From there, Git will allow us to continue to track and incorporate changes that we make to our work.

git status allows us to see if we have made any changes.

If we have made changes that we would like to save to our version control history, we can then use git add to add the changed files to the version history and git commit to finalize the process. Finally, we can then use git push to push our changes to the web so that we or collaborators can access them from anywhere.

Now that you have a brief overview of what we're about to dive into, let's go through the process step by step.

Open up a Bash Shell and Create a Projects Folder / Subfolder

To use Git, we're going back to the bash shell (mac: terminal, windows: git bash) once again! To start:

- Create a folder on your computer for your course materials and navigate into it (preferably using mkdir and cd)

- Then create a subfolder titled "Bash_and_Git" (or whatever you find to be an appropriate title) and navigate into that

- Return to your web browser and navigate to the lesson you want to download
- Click the GitHub icon

## Fork a repo

On the top right corner there is a button called fork. This lets you copy a snapshot of the repository and download it to your drive.

    git clone
Now that you have your own copy (by forking), we're going to download this copy to your local computer using git clone.

Copy the URL

Mac: Press cmd+L to highlight the url bar and cmd+c to copy the url

Windows: Press Ctrl+L to highlight the url bar and Ctrl+c to copy the url

Return to your bash shell

Type: git clone and paste your repo url (cmd + v or Ctrl+V)

** Voila! **

The repository and all of its contents will be downloaded locally to your computer!

You should be able to see the new folder by listing the files in the current directory with ls.

You can then navigate into the git directory with cd directory_name.

Now that you have a local copy, we can further investigate some more Git commands for version control. Note that for these to work you must be in the git folder (the one you just cloned above). Make sure to navigate into the folder using the cd command.

    git status  

Once you have a Git repository downloaded locally, Git will keep track of every change you make to the code in that folder. You can ask Git what the differences or changes you've made since the last commit by typing git status into your terminal.

It's really helpful to constantly get the status from Git to see what changes you need to stage, add, commit, or push.

    git add
Adding changes with the git add command is a way to stage any changes and get them ready to be a permanent record in your Git log via a commit. The workflow worth memorizing right now is to simply add all your changes via git add ..

    git commit
A commit is a permanent moment in time in your Git history. A commit creates a new version of your code. To commit, memorize this command. git commit -am "Your commit message". You are using the git commit command with the flags -am, which tell Git to commit all the changes and to include a commit message. You supply the commit message in "" directly in the command, "Your commit message".

    git push    
Pushing is the process of taking your local code and commits and syncing them, or uploading them, to GitHub. You're updating the GitHub remote (remotes are just fancy names for copies of the repository), generally your fork, represented by a remote named origin, by pushing your code to the remote. The Git command to do this is simply git push. When you git push from within a Git repository, it will take all the commits that you have locally and push them to the online remote.

### Additional Resources
[Git Cheatsheet](https://www.git-tower.com/blog/git-cheat-sheet/)  
[Git Best Practices](https://www.git-tower.com/learn/git/ebook/en/command-line/appendix/best-practices)  
[Understanding the GitHub Flow](https://guides.github.com/introduction/flow)  
[Hello World GitHub](https://guides.github.com/activities/hello-world)  
[Forking on GitHub](https://learngitbranching.js.org/)
[Git - The Simple Guide](http://rogerdudler.github.io/git-guide/)  
[Git Immersion](http://gitimmersion.com/)  
[Try Git](http://try.github.com/)
