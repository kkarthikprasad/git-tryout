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

Here the  master branch can be ahead or behind a feature branch. If the master branch is behind and all the commits of the master branch is already present in the feature then there is no need of rebasing and rebasing will shout the feature branch is uptodate with master branch, in case the master branch has any other commits which are missing by the feature branch then the commits will be added to the feature branch and master will remain same. If the master branch is ahead of the feature branch then the feature branch will apply all the commits from the master branch and comes head to head with the master branch , if the new commits are present in the feature branch which are made before rebasing then these will be kept with the branch in additional to the commits of the master (i.e., the commits of the master will be added to the feature branch and the new commits that were made to the feature branch will be kept in feature branch.).


In case of conflicts the rebasing will stop and ask for you to resolve the conflicts and then you can continue the rebasing process.

    git rebase --continue

12.Cherry picking -- It will allow you to particularly apply one commit from one branch to another ( why only one commit ?? -- That is how you should group the changes to a commit and then make the commit as a individual change like a fix or a patch or a feature . The rebasing or merging will take all the commits to the branch and that is not what is required here only one commit , a fix , a single file change or file added can be taken from one branch to another)
From the branch in where you want the cherry pick to , run the cherry pic command

    git cherry-pick <COMMIT_FROM_OTHER_BRANCH>
    
    
If the branch from which the commit was taken is merged to the branch to which the commit was applied then the Git will not apply the same commit again (GIT is smart enough to know that commit was alredy taken from that branch) 

13.Adding the remote branches from the local branches

    git push origin new-branch (This will push the whole branch commits to the remote repository , it will create the new branch if it is not present in remote repository).
    
14.Deleting remote branches is corky.

    git push origin localbranch:remote-branch ( This will create another branch as remote-branch from the local branch localbranch)
    
    git push origin :fe1branch ( This will DELETE  the branch fe1branch in the remote repository and the local branch is not mentioned here)
    

    
    




