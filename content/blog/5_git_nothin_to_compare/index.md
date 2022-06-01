---
title: Nothing to compare, branches are entirely different commit histories.
date: "2022-05-18T22:40:32.169Z"
description: "Solutions for git 'Nothing to compare' message."
---
<div style="text-align: justify">

If you have ever encountered this message while trying to create a pull request to the main branch of GitHub remote repository, the solution below I found on [StackOverflow](https://stackoverflow.com/a/66527784/5970321) and have worked for me:

```bash
git checkout master
git branch main master -f
git checkout main
git push origin main -f
```
<div style="text-align: right">



###### []'s 
