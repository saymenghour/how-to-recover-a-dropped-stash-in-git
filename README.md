# How to recover a dropped stash in Git?

__1. Find the stash commits:__

```sh
git log --graph --oneline --decorate $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )
```

_This will show you all the commits at the tips of your commit graph which are no longer referenced from any branch or tag – every lost commit, including every stash commit you’ve ever created, will be somewhere in that graph._

__2. Once you know the hash of the commit you want, you can apply it as a stash:__

```sh
git stash apply YOUR_WIP_COMMIT_HASH
```

_Note: The commit message will only be in this form (starting with "WIP on") if you did not supply a message when you did git stash._

__Source:__ View the complete answer at https://stackoverflow.com/a/91795/2510591
