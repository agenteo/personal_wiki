#Git snippets

## count how many commits on branchX 
```
git checkout branchX
git rev-list --count HEAD ^master
```

## squash 
```
git rebase -i HEAD~4
```

## bisect 
```
$ git bisect start
$ git bisect bad                 # Current version is bad
$ git bisect good v2.6.13-rc2    # v2.6.13-rc2 was the last version
                                 # tested that was good
```

## undo last commit 
```
  git reset --soft HEAD^
```


## show file in a branch 
```
  git show branch:file
```

## show content of a stash 
```
  git stash show -p stash@{0}
```

## find text in committed files (even when text is now deleted) 
```
  git grep <regexp> $(git rev-list --all)
```

## checkout an old version of a file under different name 
```
  git show HEAD^:main.cpp > old_main.cpp
```

## find deleted files 
```
git log --diff-filterD --summary
```

## restore deleted file 
```
git rev-list -n 1 HEAD -- <file_path>
git checkout <deleting_commit>^ -- <file_path>

git checkout $(git rev-list -n 1 HEAD -- "$file")^ -- "$file"
```

## abbreviated sha 
```
git log --abbrev-commit --prettyoneline
```

## patch 
```
git diff --no-prefix > patchfile
```

```
patch -p0 < patchfile
```

## track remote branch 
```
  git checkout -b < new_branch > origin/< new_branch >
  git checkout --track -b your_branch origin/your_branch
```

## grep for revisions in git 
```
git log --grep 17166705
```

## search for removed strings 
Find only commits that added or removed the word paginate
```
  git log -Spaginate
```

## git change commit text 
```
  git rebase --reword
```

## git restore a file 
```
  git checkout abcde file/to/restore
```

## git colors 
```
git config --global color.diff auto
git config --global color.branch auto
git config --global color.interactive auto
git config --global color.status auto
```

## git-svn 
```
git svn init svn://test.redant.com.au/huggies2009/core/trunk
git svn fetch -rHEAD
```


remote branch:
```
git config --add svn-remote.newbranch.url https://svn/path_to_newbranch/
git config --add svn-remote.newbranch.fetch :refs/remotes/newbranch
git svn fetch newbranch [-r<rev>]
git checkout -b local-newbranch -t newbranch
git svn rebase newbranch
```


## initialize a git repository 
```
git init --bare
```


## detailed log 
Only entries before a date, and with the name of the changed file:
```
git log --before"2011-05-06" --name-status
```

## add remote branch 
```
git checkout --track -b your_branch origin/your_branch
```

## add remote 
```
git remote add origin URL:/git/repo.git
```


## remove multiple local branches 
```
git branch | cut -c3- | egrep "^HUG" | xargs git branch -D
taken from: http://efreedom.com/Question/1-3670355/Can-Delete-Multiple-Branches-One-Command-Git
```


## remove remote branch 
```
git push origin :work_on_linux
```

## find a string in git 
```
git ls-tree -r HEAD | grep HelloWorld.pm
```
