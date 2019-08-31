# Git  tryouts

### Commands to have on finger tips when working with Git

1.To discard the changes made to a tracked file before staging it for the new commit.


	git checkout file.txt
	
2.To unstage the file and keep the changes made to the file.


	git reset HEAD fil1.txt

3.To uncommit the commit that was done but keeping the changes of the commit in the stage ( hence you add more changes to the files ). The commit to which you reset to , all the other commts after the that commit and their changes will be editable and all the commits changes can be squashed together along with new changes.


     git reset --soft HEAD~1
     
4. To uncommit the commit made and discard whatever changes done to the files in that commit.


    git reset --hard HEAD~1
    
5.To clear the unstaged files from the git ( For examples target folder and config and log files)


    git clean -n  ==> will give you "what would you do ?"
    git clean -f ==> will force to remove the files from git (But will be there in the folder)
    
6.To tag the commit. This is tag will always point to the same commit always no matter what.


    git tag mytag
    or
    git tag -a mytag ( This will provide you to give the message for the tag)
	
To sign the tag use -s switch and to verify that use the -v switch

    git tag -s mysignedtag (Asks for the passphrase to be signed).
    git tag -v mysignedtag (To verify the signed tag).
    
To push the tags (which doesn't happen with just git push)

    git push --tags
To create a branch from a tag 

    git branch <new-branch> <tag-name>

7.Configuring the logs with aliases

    git log --graph --oneline --all --decorate ( This will give the commit in a nice decorated concise format)
    git config --global alias.lga "log --graph --oneline --all --decorate" (To make and alias lga)
    git lga (to use the alias created , the alias can be found in the .git/gitconfig file)
    
8.Once the branch has been deleted the changes or the commits can still be recoered and make those commits into a new branch

    git reflog ( Gives all the references to which the HEAD has pointed to).
    git branch <new-name-for-deleted-branch-commit> COMMIT-SHA (This will create the new-branch with the same commit of the deleted branch)
    
**Note: These HEAD references which are dangling commits will be maintained by GIT for 30 days only.**

9.Stashing the changes.

    git stash (Stashes the changes)
    git stash list (to list the stashes)
    git stash apply (to apply the changes , but the stash will be there in the stash list)
    git stash pop ( the stash will be applied but will be removed from the stash list)
    git stash branch <branch-nanme> ( to make the stashed changes into a new branch)
    
10.Difference between the staging aread and the repository. The changes are added to the staging area and it gives the diff with respect to the repository (HEAD)

    git diff --cached
    
11.Rebasing -- Its all about applying the commits of one branch to another branch. The commits that have been done to one branch and you want those commits in your branch (In other words one branch is ahead of another branch and you want the lagging branch to catch up with the branch with new commits) 
Assume you are in one of the feature branch and it is behind the master and you want the commits of the master so the feature branch can move ahead of the master branch and you can continue to do the work of feature branch or you can merge the branch to master itself.

    git rebase master ( This will add the commits from master to the current active branch.)
In case of conflicts the rebasing will stop and ask for you to resolve the conflicts and then you can continue the rebasing process.

    git rebase --continue




