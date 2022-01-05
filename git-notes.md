# quick notes on Git

1. usecases
  -  get recent changes from another branch
     - https://stackoverflow.com/questions/37709298/how-to-get-changes-from-another-branch (2nd preferred)
  - [keep Git history while `mv`-ing them](https://gist.github.com/ajaegers/2a8d8cbf51e49bcb17d5)

2. submodule
  - `git submodule update --init --recursive`
  - `git submodule -b <branch> add <repo url>` for specific branch
  - `git checkout <branch>` to attach HEAD to submodules
  - `git submodule update --remote`
  - [completely remove a submodule](https://gist.github.com/myusuf3/7f645819ded92bda6677)

3. patch add
  - `git add -p <>`

4. [remove all history concerning one file](https://stackoverflow.com/questions/43762338/how-to-remove-file-from-git-history), when you accidentally pushed some sensitive information
