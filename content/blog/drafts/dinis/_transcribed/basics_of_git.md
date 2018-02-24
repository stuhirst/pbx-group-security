---
draft  : true
title  : What is Git?
author : Dinis Cruz
notes:
 - english and structure needs fixing
---

What is Git?

Git is a version control system. It basically, it's a technology designed to keep copies, keep track of made to files. 

Git is a type of version control system, where all data ...

Git is a distributed version control system. What that means? It means that instead of relying on a server to hold information and fetch the latest version, Git database contains all commits and all changes made in the files. That means, in a way, that every Git database, or Git distribution is a full copy of all the data, in all the files. And this simple change means that activities that usually are very complicated, or very time consuming in other version controls, are very simple and fast in Git. Because, fundamentally, you have all the data at one look. 

And the reason it scales, it’s because, Git is fundamentally a graph. And that means, that when Git calculates the conversion of the file, it just transverses a particular graph note based on its delta. So, the key concepts in Git are, when you start using Git, is the Git pull, the Git push, and the Git stage and the Git commit.

So, when you start a new repository, the first thing you do, you do Git in it, so you have a brand-new Git database and you add the file. So, now you have a file that exists only on your local base, then what you do? You need to do a Git, for example, add dot, because that stages the file to be committed. And that means that you have an intermediate step between the commit of the file, basically, between the moment you add it from version control, from the moment it exists in the file system.

And this already allows a very good variety, and to eventually pick and choose, sometimes, what you want to commit straight away or not. And then, what you do: You do a current called Git commit and put a message, and what it does? It writes that files to the version control. In practice what it does, it calculates the files information and stores in a hash based database. Each log containing the content upload hash of that log, and then, in the Git's database, you basically store the mapping to those logs and the files that exist. And then, Git signs all of that to give you a hash of that commit. And, when you make another change, the same thing, you make changes, you again add a Git commit, and then, what happens is that the commit of the next version of the file is now hashed with the previous one. It means in practice that Git contains a whole chain of authentic with everything you commit. Because everything you commit is basically hashed and mapped to the previous one. And that's basically it.

Even if you just did that, that was already quite good. Because it means that locally, you were already working in a version control workflow. And ideally, we should get to a point that even our operating systems have native Git support. That would be great one day.
So, the next stage, is when you want to distribute and collaborate with others, or you want to store this information in a server, so that it doesn't only exist in your machine. This is where you need to use servers like GitHub. 

So, with GitHub, what you do, is you create a repository, and the repository, basically, is a Git repo is GitHub. So, when you got a repository on GitHub, you got an URL, and that url is now what you are going to add to your Git repo. So, if you add a scalar remote, the remote is a remote Git server, so if you go GitRemoteadd and then the URL, you are going to the GitHub. Then, what happens is you now save for that repo.

So, if it's the first time you do this, you can just push into it. And basically, pushing means that you pushing data from your GitHub to the server. So, you add origin and then the name of the repo. And then now you are going to do a Git push origin master, because that's the branch you are in, and then what happens, is that, that will push, if all goes well, in this case if the other repo had no commits. You then have the data being pushed into the server.

And that's it. And now go to GitHub and you'll see your file. If you are connecting from a new repo, what you do, and when somebody pushes changes to that repo, you want to consume it, you do is call ligated pulls, which basically pools into the database and pushes the file system and if you are starting from scratch, you do the clone, which basically creates a local copy of the repo to your computer. And that's the basics of Git.

