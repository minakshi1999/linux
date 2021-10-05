## Git commands

```sh
$ git init
$ git status
git add file_name                 # add specific file
git add -A                      #all files in staging area
git restore <file>              #to discard changes in working directory
git rm --cached <file>          #to unstage
git commit                         # open in code editor
git commit -m "statement"        #not deal with code editor
git commmit -a -m "statement"    #to make commit direct by skipping staging area 
git checkout file_name           #for recover accidently modified file 
git checkout -f                      # to restore all file at a time
git diff                          #compare working tree with staging area
git diff --stage                    # compare staging area with last commit 
git log                             #to see commit
git log -p                          #to see commit with all differences
git log -p -<number_of_commit>      #to see commit with specific differences
```