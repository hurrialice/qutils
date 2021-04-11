# quick notes on Git

1. get recent changes from another branch
  - https://stackoverflow.com/questions/37709298/how-to-get-changes-from-another-branch (2nd preferred)

2. submodule
  - `git submodule update --init --recursive`
  - `git submodule -b <branch> add <repo url>` for specific branch
  - `git checkout <branch>` to attach HEAD to submodules
  - `git submodule update --remote`
  - [completely remove a submodule](https://gist.github.com/myusuf3/7f645819ded92bda6677)
