# Nov22-2021-test
Creating new repository for trial. Write down notes for learning github and git

Very good resource: https://www.youtube.com/watch?v=RGOj5yH7evk

Github guide: https://docs.github.com/en/get-started/quickstart/hello-world


## Initialize git tracking of a newly created or existing repository (to generate .git)
Ref: https://www.atlassian.com/git/tutorials/setting-up-a-repository

---> cd /path/to/your/existing/code \
---> git init

Or  

---> git init <path_to_directory>  

Terminal output: \
" \
hint: Using 'master' as the name for the initial branch. This default branch name \
hint: is subject to change. To configure the initial branch name to use in all \
hint: of your new repositories, which will suppress this warning, call: <br />
hint: <br />
hint: 	git config --global init.defaultBranch <new_branch_name>  
hint: <br />
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and  
hint: 'development'. The just-created branch can be renamed via this command:  
hint:  
hint: 	git branch -m <branch_name_desired_to_remove>  
Initialized empty Git repository in /Users/chiachun.liang/Desktop/Nov24-2021-test/.git/  
" 

## Downloading a remote repository on github and making updates back and forth
Use ssh. Before you clone any repository to your local computer, you need to set up ssh key. Each device should have 1 ssh key pair (public + private). Some ppl use multiple keys on same device, but even with multiple keys, it's always going to be the same public key, so maybe having multiple keys are not necessary. (Good ref to install ssh key: https://www.youtube.com/watch?v=2dA1dfkS79o) \
---> git clone <repository_ssh_link>  

Once we clone a repository from github, we have configured it (it's automatically setup tracking). If there are changes to the existing files, just need to add, commit and push to the github repository (if desire) \
---> git add filename_you_made_edits (even though this is not a new file I created, looks like I still need to add it first)
---> git commit -m "add any title of commit here (this will be the title line)" -m "add any extended description here" \
---> git push \ (if haven't setup upstream branch yet, i.e, may have multiple branches on github and you do not tell which branch to push to, need to set up upstream branch: git push --set-upstream origin branch_I_wish_to_push_to. The branch I wish to push here is named "main") \
* If a new file is created within the same repository, definitely need to git add the file (tell git to start tracking that file) and then do git commit \
---> git add file_name \
---> git commit -m "add commit message here" \
---> git push 
* Note, we can also use "git add ." for anything new files or changes made in the same repository. 
* Use "git status" whenever you feels like it to check out the current updates on your local repository (like what files are edited, what files are newly created, etc)

If there are some new updates from the remote branch (that's say, you change something on the repository in github), the way to update your local branch will be:\
---> git pull 
* Note, not specifying any branch is allowed only when you already set up a tracked remote branch (if there are multiple tracked remote branches, need to specify) 
* Good ref: https://www.freecodecamp.org/news/git-pull-explained/ 

That's it.

* *Tip: Do not try to rename my branch, it'll create chaos! I changed my local repository name to development and when I tried to push to github, it didn't work. After trying a suggestion from the output of terminal, it created a new branch on github name exactly "development". This problem was solved by deleting whole repository on my local computer (use rm -rf) and re-clone it from my github. I also double-checked my upstream branch is main (git push --set-upstream origin main 

# Git branching
Ways to check out branches you have:
1. git status
2. git branch
* Note that the * sign in front of a branch is the current branch you are on

Creating new branch: \
---> git checkout -b new_branch_name \
Once we have multiple branches, we can switch among branches:\
---> git checkout branch_you_wish_to_switch \
If I wish to push this newly created branch to github (which, github doesn't have it), I create an empty branch on github name exactly same name, upload/push my local development branch to that new empty branch, and then create a pull request, and then merge with my main branch if desire

Comparing 2 branches or a file within 2 branches before merging: \
Go into 1 branch first (ex: main) and type on terminal: \
---> git diff branch_name_you_wish_to_compare \
Or we can do \
---> git diff branch1..branch2 \
If comparing a file between 2 branches or just comparing commits between 2 branches, see this: https://devconnected.com/how-to-compare-two-git-branches/. Other ref: https://stackoverflow.com/questions/9834689/how-can-i-see-the-differences-between-two-branches

## Merging branches locally
---> git merge
---> git diff
41:27

Delete a branch: \
---> git branch -b branch_you_wish_to_delete
TESTING
TESTING2
