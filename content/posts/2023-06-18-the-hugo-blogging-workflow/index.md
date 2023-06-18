---
title: "2023 06 18 the Hugo Blogging Workflow"
date: 2023-06-18T06:40:57+02:00
draft: false
tags: 
- hugo 
- howto
- blog 
---

I cannot remember anything. Therefore a brief overview of the blogging workflow with hugo. 

<!--more-->

## Update the repo 
Make sure you are working with the latest changes in your repo. 
```
git pull 
```

## Make a branch 
You can use branches for planing future blog posts without messing up your **main** branch. I won't go too deep into the **git religion** by now. But think of it as a container for a task. 

### Create a branch in advance without working on it right now
```
git branch <name-of-branch>
```

### List all already existing branches 
```
git branch --list
```
or just 
```
git branch 
```

### Switch to a already created branch
```
git checkout <name-of-branch>
```

### Delete branch 
In case there are no commits and changes in this branch 
```
git branch -d <name-of-branch>
```

In case there are commits and changes in this branch and you want to get rid of it anyways 
```
git branch -D <name-of-branch>
```

### Rename the current branch to something else 
```
git branch -m <new-name-of-branch>
```

Note that you have to check out to the branch first that you want to rename 

### Create a branch and immeditatly work with that branch
a.k.a. make a branch and check out to that branch in one step 
```
git checkout -b <name-of-branch>
```
## Create your blog post 
```
hugo new posts/<year-month-day-name-of-post>/index.md 
code content/posts/<year-month-day-name-of-post>/index.md 
```

## Make your changes and save the file 


## Stage your changes 
```
git add . 
```
or 
```
git add <name-of-file>.md/jpg/png/whatever 
```

## Commit your changes 
```
git commit -m "Declarative Message Of What The Changes Are Which You Are About To Commit."
```

## Merge your changes when you are finished 
Merging in git is also a topic on its own. Let's try to keep it simple with two different examples. 

### Merge your changes while main has not changed at all 
The common one is, that we have the single point of truth in main (this is the way). Then, we prepare a new blog post in a separate branch and merge it to main as soon as we have finished the blog post
```
# Create a branch for the new post and directly switch to that branch 
git checkout -b new-blog-post-about-ants main

# Create your files, add content and save everything 
hugo new posts/2023-06-18-new-blog-post-about-ants/index.md 
code content/posts/2023-06-18-new-blog-post-about-ants/index.md 

# Add the files to the branch and commit 
git add . (or git add <filename>) 
git commit -m "Message for your commit"

# Make some additional changes until finished and repeat step from above 
git add .
git commit -m "Blog post finished" 

# Merge the new blog post to main 
git checkout main (we need to switch to the target branch - in this case main)
git merge new-blog-post-about-ants 

# Delete the now obsolete branch 
git branch - new-blog-post-about-ants 
```

This is a common procedure in git and perfect for the blogging-in-hugo experience. 

### Merg your changes while main has also changed in the meanwhile 
Sometimes you are working on several different branches simultaniously. The result is, that main might have got changes from other merges while you still have branches open which do not have the new changes from main. 

It's actually some kind of a timing issue. In this case the Merge-Process looks a little bit different. 

```
# Make a new branch for your post 
git checkout -b another-awesome-blogpost main 

# Create, edit and save the files for your new post 
hugo new posts/<yyyy-mm-dd-another-awesome-blogpost>/index.md 
code content/posts/<yyyy-mm-dd-another-awesome-blogpost>/index.md 

# Add the files to git and commit 
git add .
git commit -m "New post created in draft mode"

# Make more changes and finally repeat the steps from above 
git add .
git commit - "Finished the new awesome blog post" 

# Switch to our merge target branch -> main 
git checkout main 

# Now sometimes you might need make changes in main or you have merged other branches which were open as well. In this case make sure all changes are committed before trying to merge anything else. 

# Check the status of main 
git status (should show that no changes are pending) 

# If everything is ok, merge as usual with 
git merge another-awesome-blogpost 

# Clean up 
git branch -d another-awesome-blogpost 
```

That's it. Now you're new post should be available on your hugo based blog. 

So long... 



