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

## Create your SSH key
If you’ve set up an SSH or a different Personal Access Token you can skip this step.

https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh  

You should create an SSH key to use in place of a password with the command line or with the API. With SSH keys, you can connect to GitHub without supplying your username or password at each visit.
Check for currently existing SSH keys. If there are keys you don’t recognise or don’t use anymore delete them.


Generate a new SSH key and adding it to the ssh-agent. Open Terminal.
Paste the text below, substituting in your GitHub email address.

$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

This creates a new ssh key, using the provided email as a label.

Generating public/private rsa key pair.
When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

    Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]

At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases". Passphrases are not required. If you do make one store it in your password manager (1Password, Lastpass)

    Enter passphrase (empty for no passphrase): [Type a passphrase]
    Enter same passphrase again: [Type passphrase again]

Adding your SSH key to the ssh-agent. Start the ssh-agent in the background.

    $ eval "$(ssh-agent -s)"
    Agent pid 59566

If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
First, check to see if your ~/.ssh/config file exists in the default location.

    $ open ~/.ssh/config
    The file /Users/you/.ssh/config does not exist.

If the file doesn't exist, create the file.

    $ touch ~/.ssh/config

Open your ~/.ssh/config file, then modify the file, replacing ~/.ssh/id_rsa if you are not using the default location and name for your id_rsa key.

    Host *
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/id_rsa


Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

    $ ssh-add -K ~/.ssh/id_rsa

Adding a new SSH key to your GitHub account. Copy the SSH key to your clipboard.

If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

    $ pbcopy < ~/.ssh/id_rsa.pub
    # Copies the contents of the id_rsa.pub file to your clipboard

Tip: If pbcopy isn't working, you can locate the hidden .ssh folder, open the file in your favorite text editor, and copy it to your clipboard.

In the upper-right corner of any page, click your profile photo, then click Settings > SSH and GPG keys > New SSH key or Add SSH key.

In the title include a descriptive name for your key. Paste your key into the key field.

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
