## 05:50 
### local : on local system
- working directory : where code is written editted etc
    - making changes
- stage : once written and edited, its staged
    - my changes are ready for next step
- local git
    - middle area between local and remote repo
- commit 
    - locking the current code version with a commit id 
    - its permanent
- repository 
    - where all the versions and the change history are stored
    - git creates sytem files to manage versions and tracks history and changes

### remote : usually github, gitlab or bitbucket
- for collaboration and remote access anywhere of the locally saved code


### commands
1. git init : initalize git for the folder
    - for tracking any changes in this folder
    - creates .git hidden folder in the folder with its system files for tracking
2. git clone : copy remopte git repo to local
    - git clone <remote repo url>
    - -b : specify which branch to be cloned
3. git status :  to see what changes have been made since the last pull or last commit
4. git add : to move to staging area
    - git add <folder path>
    - git add --all
    - git add -A
        - to track all the changes made so far in the whole project
        - --all is -A in short
    - git add .
        - only track changes made in the particular folder
    - git add *
        - only adds new or modified files and not deleted ones
    - git add <file path>
        - only stages the file mentioned
    - git add *.txt
        - stages all txt file in the folder (nto sub folder)
5. git reset : to un-stage all changes
    - git reset HEAD~
        - undo the previous commit and bring back the previous version, in local
6. git commit : from stage area to the remote
    - git commit -m "commit message here"
        - while sending version to the remote, specify the changes in short description
7. git remove : delete a file and stage it at the same time, insetad of delete and then git add .
    - git rm <file path>
    - git reset : now will only bring back the file but not really (only changes will be undone) #doubt
    - git reset --hard : will now bring in the remoevd file too
    - uncommited changes cant be removed, lets say a file thatw as earlier commited and now modified needs to be deleted, rm wont work (needs to be removed forcefully)
        - git rm -f <modified but uncommited file path>
    - git rm --cached <file path>
        - removed from staging but not form system
    - git rm -r <folder path>
        - to remove fodler and all its subfolders and files recurssively
    - git rm <folder path>
        - only the folders content, not the sub folders, will nto work if its not empty
8. git log : view all commits and messages history with commit ids
    - git long --oneline
        - summary for each commit
    - to escape from log window press : "q"
9. branching : seperate palce to make changes away from the main one
    - main is the main branch, not to be used for experimenting (used to be called master)
    - development branch is where things are made broken and tested and if good, moved to main
    - merge : after branches make changes and are approved for main, it will merge it to main 
    - git branch 
        - shows list of all branches in the repo
        - * shows which branch we are in
    - git branch <new branch name>
        - creates a new branch with clone of the current branch
    - git checkout <branch name>
        - to move from one branch to another
    - once checkedout, only files from the branch will be visible
10. Merge : passing on the changes of one branch to another
    - git merge main -m "merging main into develpment"
        - updates of both the branches are combined into developement
    - conflicts : while merging if there are changes that contradict or are not compatible, this will occur
        - git will flag and you will have to resolve the conflict manually by choosing which changes to keep
            - current or incoming
    - git merge <name of the branch>
        - bring in all the changes from one branch to another
        - will not work incase of conflict
11. checkout : apart from changing branches it can also be used for
    - travelling back in time to another version in the same branch
    - using git log --onliner a comit id of all commits in the history can be obtained
    - git checkout <commit id>
        - to go back in time to a previous version
    - git checkout main
        - to go back to the latest version
12. compare : one commit to another
    - git diff <commit id 1> <commit id 2>
        - from the perspective of commit id 1, can be reversed
13. Push : to move all changes commited in lcoal to remote
    - git push origin <branch name>
        - origin means remote repo
    - to change the rbanch and then push
        - git checkout <branch name>
        - git push origin <branch name>
14. Fetch : to reflect all changes in remote in local, but not actually merging them
    - when something change in github file , someone changes using github ui or commits from  thier system
    - the chnages will not be reflected on our local so for that
    - git fetch 
        - to make the fetched items final : git merge
15. Pull : to actually get all the changes from remote to local, fetching + merge
    - git pull : git fetch + git merge
16. git restore : to undo all the changes since the last commmit 
    - git restore <file path>
    - git restore <folder path>
    - git restore . 
        - for all changes in the folder
    - git restore --staged <folder path>
        - for restoring all stage chanegs in the folder
17. git stash : to not cimmit the changes made in a branch and still move to a different branch
    - withotu committing checkout will nto happen
    - so  to do that first git stash
    - git checkout <another branch>
    - git checkout <previous branch>
    - it will not show the uncommitted work yet
    - git stash pop
        - will rmeove from the stash list and make it back to the desired stage (latest stashed commit)
    - git stash apply
        - will not remove from the list and still bring back the desired stage (latest stashed commit)
    - stash is like a list and can have multiple things stashed
    - git stash list
        - shows all stashed away items in the list with stash id
        - which an be used to apply or pop them specifically
        - git stash pop stash@{0}
        - git stash apply stash@{0}
    - git stash drop
        - to remove the latest stash id 
18. git revert : used to create a new commit which is copy of the previous commit
    - i.e. commit 1 , commit 2
        - after revert there will be commit 3 which will be commit 1
    - doesn delete anything, just creates a new commit with old stuff
    - git revert <commit id>
        - will ask for a message , either write or :wq
    - revert vs reset 
        - revert doesn delete but just creates copy of a desired stage point in time
        - reset goes back to a point in time fo dersired state and deletes any changes after that
19. git rebase 
    - situation : working a branch with changes and mean while main is change by someone
    - to include those changesthere are several ways
        - 1. merge it (creates extra commit and looks messy)
    - rebase is cleaner
        - all main chanegs will be applied to feature branch and the changes in feature branch will still be there
    - to bring latest update from main to feature while working on feature
    - git checkout feature
    - git rebase main
        - finds the most recent common commit between the feaure and main branch
        - then after that point any changes in feature branch is set aside
        - and commits form main branch is added to feature brach
        - then the changes in feature branch is added back 
    - not recommend for public or large group repo setting
        - inform the admin before doing that
        - it rewrites commit id and hsitory
    - #doubt will there be conflicts here?
20. Pull request PR
    - a request to merge changes from your branch to the main one
    - ask for review and then merge to main
    - 

