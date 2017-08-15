# Version Control Hints
This is not a step-by-step guide. Instead it's a collection of screenshots which will help you complete the DevOpsHack challenges.
This is on purpose: We want you to explore and play with the different options of VSTS.

## Create a new Git repository in your Team Project ##
![Create a new Git repository in your Team Project](/VersionControl/images/VSTSProjectCode.PNG)

## Clone our sample repository found [here](https://github.com/DanielMeixner/DevOpsHackSample) to your machine ##
![Clone our sample repository found here to your machine](/VersionControl/images/GitCloneURL1.PNG)
![Clone our sample repository found here to your machine](/VersionControl/images/GitCloneURL.PNG)
## Push the code to your new repo in your Team Project ##
![Push the code to your new repo in your Team Project](/VersionControl/images/VSTSEmptyRepo.PNG)

Navigate to the folder containing your git repo 

`git add remote origin YourVSTSRepoURL`

`git push -u origin --all`

----

## Modify your repo to require a pull request to merge code into your master branch ##
![Modify your repo to require a pull request to merge code into your master branch](/VersionControl/images/VSTSProjectBranch.PNG)

## Modify your repo to require a Work Item linked to a pull request ##
![Modify your repo to require a Work Item linked to a pull request](/VersionControl/images/VSTSBranchPolicie.PNG)

## Configure your repo to require at least one of your colleagues as approver ##
![Configure your repo to require at least one of your colleagues as approver](/VersionControl/images/VSTSBranchPolicie1.PNG)

##  Modify code locally then proceeding to create a pull request ##
![Create a branch and check it out](/VersionControl/images/VSTSProjectCodeFiles.PNG)

![Modify code locally ](/VersionControl/images/ChangeCodeHereMaybe.PNG)

![Commit your change to your new branch then proceed to create a pull request into master](/VersionControl/images/VSTSCodePullRequest.PNG)