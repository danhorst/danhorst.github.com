---
filename: 2012-05-14-stage-all-deleted-files-in-a-git-repository.md
layout:   article
category: Note
tags:     [git]
title:    Stage All Deleted Files In A Git Repository
---

    git ls-files -d | xargs git rm

If you delete a file in a git repository without using `git rm FILENAME` it can be a bit of a pain.
The deleted files are not staged for a commit and you can no longer use tab completion for the filename as it is no longer there.
This [post on how to use xargs][1] led me to an elegant solution.

`git ls-files` lists all the files tracked by the git repository.
(The `-d` flag limits the list to deleted files.)
`xargs` takes each line in the list and uses it as the argument for the command it preceeds.
In this case, `git rm FILENAME` is run for every deleted file identified by `git ls-files -d`.

[1]: http://bitops.io/blog/1336893229/xargs
