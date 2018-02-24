---
draft  : true
title  : New to GitHub
author : Harrie Bickle (TW)
issue  : https://github.com/project-cx/pbx-group-security/issues/245
notes:
  - draft0
---

## GitHub's quirks

Oh, GitHub, isn't that what the developers use? Yes, indeed GitHub drives many open source projects allowing disparate individuals 
to come together as an effective group. So here you are, the new press officer, proof-reader or hot-beverages assistant saying: 
"but I don't need GitHub to make a cuppa tea". Welcome to the party because, in fact, you do; everything is managed within GitHub 
here at Photobox security, including hosting the very pages that this site is constructed from.

There are some seriously good reasons to use GitHub. It has a project board, issue board and allows you to assign
items to specific individuals to control workflow. It provides built-in version control and most recent version 
of a document will never be on someone elses PC.  

Coming in as a newbie to GitHub is an interesting challenge. There is a lot to learn and there are probably basic assumptions
that you hold that will need to be identified and reworked. Learning GitHub has been a bit like coming to terms with dealing with my
racist mother-in-law: there is very little that I can do to change the underlying architecture, and there are simply some topics 
that are best to stay away from until I have improved my skills. 

The only way to learn is by doing. There are a number of options to choose from just in _how_ you communicate with GitHub. The easiest 
first step is to use the [web interface](www.github.com). Login and find a repository (repo) to work on. 

## Challenge 1: Edit a file

Your first challenge is to alter a file through the GitHub web interface. 

Log in/create an account and make sure that Photobox has given you access to a repo. If not, contact the team.
Choose the repo, for example, <need a public site to edit with no restrictions>.
Let's choose a file to edit. The _Readme_ is a good place to start. 

Hover over the pen symbol at the top right and you will see the message: "edit this file". Yes, let's.
Add some text to the file, then navigate to the bottom of the page where you have an active dialogue box: "Commit changes". 
The default description for this change is: "update Readme". It is good practice to provide something less generic. 
I am going to say "Test update". 

There is also an opportunity to leave comments. If the changes are complex or require analyses by another person, then 
assist by providing data here. For now, we can move on.
To submit the change to the file (and the name/comments for that change) we have two options: either we commit directly to the 
master branch OR we create a new branch for this commit. 

Select to make a new branch. Github will auto assign a name for this branch. Notice that this name contains the word patch.
Select the: "Propose change" button and this takes you through to the same dialogue box, giving you the last chance to communicate 
the reasons for this change. Select the "create pull request" button.

GitHub will run through some basic checks to ensure that you will not break something or cause conflicts with this change. 
If the tests pass, you can collapse your Pull Request (PR), by choosing the button "Merge Pull Request". 
You then also have to "Confirm Merge".

<all the above with images>

Congratulations you have just made your first successful edit.

Let's analyse what you have done using a google spreadsheet as an example. 
What we did can be compared to opening the spreadsheet, adding a number to a cell and closing the spreadsheet back down. 
In GitHub terms, you took a copy of the spreadsheet, edited that copy, suggested that that edit be included in the original 
(known as the master), and replaced the spreadsheet with your copy that contains the change. 

Just as google drive lets you look at the history of a document and revert to older versions, so will GitHub. 
Just as google drive lets you see who made what changes to documents, so will GitHub.

You have one last task, which is a house-cleaning exercise, which is:

Delete branch. The GitHub message will say "Pull request successfully merged and closed", this means that the 
version we made with the name ***patch is redundant because the changes it represents are now part of the main or master branch. 
This means you can throw it away, its job is done, with our google doc analogy this means getting rid of the duplicate spreadsheet.

Phew, are you ready for that cup of tea yet? So you may already have a suspicion that this is not how everybody is using GitHub, 
and it is not. There are three big differences between what we just did and the typical GitHub flow. One is that we used the 
web interface, most people will use a desktop version [GitHub Desktop](https://desktop.github.com/). Two is that we had editor rights on this repository, 
this is pretty atypical. It is very unlikely to be you that accepts the pull request to merge the proposed change to the master branch. 
Three we created a temporary branch on the fly, called a patch, to make one change to one file, typically people work from a 
branch (or a fork) whilst making edits and merge those back with the master.

Before we start dangling off branches whist holding foks, it is a good idea to come to terms with the Pull Request cycle that you
have just done. Try a few more edits on a repo that you can play with.



Resources

https://about.gitlab.com/2014/09/29/gitlab-flow/

https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

https://datasift.github.io/gitflow/IntroducingGitFlow.html

https://guides.github.com/introduction/flow/index.html
