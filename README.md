# Getting_Started_With_Git
## Introduction
Git is a version control system.GitHub is an online hosting platform that uses Git.
Objectives
You will be able to:
- Describe the difference between a forked and a cloned repository
- Use git clone to clone a repository
- Use git add, git commit, and git push to make changes to a repository
- Compare local and remote repositories
### Some terminology and concepts
The first thing we'll look at is forking, a concept from the GitHub platform.
Forking is the process of making a personal copy on GitHub.
Afterward, we'll then use git clone from a bash shell like terminal or git bash in order to copy the material from the web to our local computer.
From there, Git will allow us to continue to track and incorporate changes that we make to our work.
git status allows us to see if we have made any changes.
If we have made changes that we would like to save to our version control history, we can then use git add to add the changed files to the version history and git commit to finalize the process. Finally, we can then use git push to push our changes to the web so that we or collaborators can access them from anywhere.
Now that you have a brief overview of what we're about to dive into, let's go through the process step by step.
## Open up a Bash Shell and Create a Projects Folder / Subfolder
To use Git, we're going back to the bash shell (mac: terminal, windows: git bash) once again! To start:
- Create a folder on your computer for your course materials and navigate into it (preferably using mkdir and cd)
- Then create a subfolder titled "Bash_and_Git" (or whatever you find to be an appropriate title) and navigate into that
- Return to your web browser and navigate to the lesson you want to download
- Click the GitHub icon
You'll be redirected to the associated github repository like this.

- Click the fork button, as shown above in order to create a copy to your personal account which you can edit and update.
After a moment of this:

You'll be redirected to your new personal copy of the repository:
### git clone
Now that you have your own copy (by forking), we're going to download this copy to your local computer using git clone.
