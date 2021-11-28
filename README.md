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
Use ssh. Before you clone any repository to your local computer, you need to set up ssh key. Each device should have 1 ssh key pair (public + private). Some ppl use multiple keys on same device, but even with multiple keys, it's always going to be the same public key, so maybe having multiple keys are not necessary. (Good ref to install ssh keys: https://www.youtube.com/watch?v=2dA1dfkS79o) \
---> git clone <repository_ssh_link>  

Once we clone a repository from github, we have configured it (it's automatically setup tracking). If there are changes to the existing files, just need to commit and push to the github repository (if desire) \
---> git commit -m "add any title of commit here (this will be the title line)" -m "add any extended description here" \
---> git push \ 
If a new file is created within the same repository, need to git add the file (tell git to start tracking that file) and then do git commit \
---> git add file_name \
---> git commit -m "add commit message here" \
---> git push 
* Note, we can also use "git add ." for anything new files or changes made in the same repository. 
* Use "git status" whenever you feels like it to check out the current updates on your local repository (like what files are edited, what files are newly created, etc)



If there are some new updates from the remote branch (that's say, you change something on the repository in github), the way to update your local branch will be:\
---> git pull 
* Note, not specifying any branch is allowed only when you already set up a tracked remote branch (if there are multiple tracked remote branches, need to specify) 
* Good ref: https://www.freecodecamp.org/news/git-pull-explained/ 

  

