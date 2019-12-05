# Tips and Tricks in Git

This is the documentation for the Pluralsight course for _Advanced Git Tips and Trips_ .

<br/>

#### Diff

Getting the diff much more in the words scope
    
    git diff --word-diff=color

Using different algorithms for diff

    git diff --patience # It takes more time but figures out which are the lines of code that are grouped together more logically and then groups them.
    git diff --histogram # This algorithm takes much less time than patience algorithm and it is recommended to get the diff as it is much faster.
    
#### Commits

Qualities of a Good commit :
  Maarkup : * **Atomic**  
               * _Self Contained_ - Semantically related changes should not be split across commits.
               * _Coherent_ - All changes in a commit should be semantically related.
            * **Consistent**
               * _No compilation erros_ - A commit should not introduce compilation errors.
               * _No broken tests_ - Commit should not break any existing tests nor add failing ones.
            * **Incremental**
               * _Ordered_ - commits should be ordered deliberately
               * _Explanatory_ - The order should be a trail of the programmer's thought process.
            * **Documented** 
               * _Short summary_ - Commit message should include a short one-sentence summary.
               * _Detailed description_ - Longer description can be added if more details are necessary.
               


          AAAAAAAAAAAAAAAAAAAAAAAA


    


