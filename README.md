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
---> git add filename_you_made_edits (even though this is not a new file I created, looks like I still need to add it first) \
---> git commit -m "add any title of commit here (this will be the title line)" -m "add any extended description here" \
---> git push \ (if haven't setup upstream branch yet, i.e, may have multiple branches on github and you do not tell which branch to push to, need to set up upstream branch: git push --set-upstream origin branch_I_wish_to_push_to. The branch I wish to push here is named "main") \
* For an already tracked file, we can actually just use: git commit -am "add message". -am stands for add and commit \
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
* If I wish to push this newly created branch to github (which, github doesn't have it), I create an empty branch on github name exactly same name, upload/push my local development branch to that new empty branch, and then create a pull request, and then merge with my main branch if desire
* If I created a new empty branch on my local computer (or in the video the author created a completely new reposit), and if I wish to update my new branch with the main branch (upstream bbranch) on github, I need to set upstream branch first to this new local branch (in my case: git branch --set-upstream-to=origin/main test_branch), and then I can use git pull.

Comparing 2 branches or a file within 2 branches before merging: \
Go into 1 branch first (ex: main) and type on terminal: \
---> git diff branch_name_you_wish_to_compare \
Or we can do \
---> git diff branch1..branch2 \
If comparing a file between 2 branches or just comparing commits between 2 branches, see this: https://devconnected.com/how-to-compare-two-git-branches/. Other ref: https://stackoverflow.com/questions/9834689/how-can-i-see-the-differences-between-two-branches

## Merging branches locally
---> git diff \
---> git merge master(the main branch which got the updates from github and you want to merge into your local test branch)\
We do git merge when working on your local test branch. You will want to constantly update the main branch on your local computer (bc other ppl who are working on the same project may have some updates to the github) and then merge into your test branch that you are making changes. When conflicts happen when merging, the best way to solve this is open your code editor, look at the code and decide what to keep (should get a good code editor).

Delete a branch: \
---> git branch -b branch_you_wish_to_delete
TESTING
TESTING2
Something

Undoing a "git add" or "git commit": \
If you just git add something and you want to undo it, use \
---> git reset \
This will undo the previous git add you just made. If you already committed it, use: \
---> git reset HEAD~1 \
This is take out/unstage the lastest commit, changes made in your file are still there, but not "git add" and "git commit". If you want undo several commits, then need to go into log file, look at the unique id that each commit has, and use that id to reset \
---> git log \ 
---> git reset 70241fb892e25f307ba1f67c40d95343bdc54025(example id) \
* If you want to completely wipe out the changes you've made in files, use: git reset --hard 70241fb892e25f307ba1f67c40d95343bdc54025(example id)

# Forking
Forking is a way that you can customize a public repository/project that you took from other ppl's account. This allows you to make full control of the repository/project. If you want to give feedback to the account that you forked the repository from, create a pull request.

# Git workflow (super important after learning all git commands!!)
If making some changes on a test branch, always push to a test branch on github (always name the same), create a pull request to merge into main branch. From there, on the main branch on your local computer, the changes can be pulled from main branch in github. I get terminal showing conflicts sometimes. This part I need to learn more.
