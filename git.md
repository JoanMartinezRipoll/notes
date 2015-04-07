#Views

##Rebase vs merge
Github will ALWAYS create a merge commit once a pull request is merged, so it makes sense to rebase at the branch to be merged, because otherwise we would get to merge commits (the first one, when we merge master into the branch with the feature, and the second one because of github's pr merge commit)

Its interesting to notice that when we do rebase "master" we are merging with our local master. If we wanted to merge with the remote master, we would do a rebase origin/master, but most likely this will be the same thing as the previous unless we do a git fetch.