<font size="4em"><strong>Git Version Control</strong></font>

#### Git is a version control system to provision, test, and deploy code. The following resources includes frequently used commands, as a central location on Git.

#### Git Commands

```bash
When a # is used, this indicates a comment
When a <> is used, this indicates the location for a file, tag, hash, etc.
```

###### Configure preferred name and e-mail for Authorship 
```bash
git config --global user.name "David Yakobovitch"
git config --global user.email "david@gmail.com"
```

###### Configure CR LF message display  
```bash
git config --global core.autocrlf input
git config --global core.autocrlf false 
```

###### Set your preferred text editor
```bash
git config --global core.editor "emacs"
```

###### View configuration settings
```bash
git config --list
```

###### View help settings
```bash
git config --help
```

###### Clone a repository from Github
```bash
git clone [_url_here] [directory_name_here] [local_file_path_here]
```

###### View the repository connected to from the remote
```bash
git remote -v
```

###### Initalize a local git on host machine
```bash
git init [directory_name]
git init # inside the directory
```

###### Create a new directory or file
```bash
mkdir [directory_name] #create directories
touch [file_name.extension] #create empty files
echo "text goes here" > file.txt #creates new file with text values
```

###### Stage changes to the active directory
```bash
git add . # all changes to be logged
git add [file.txt] # logs a file change
git add [file-1.text] [file-2.txt] # logs file changes for specific files
```

###### Show changes status in the active directory
```bash
git status
```

###### Show changes before and after staging as colored-words
```bash
git diff # before git add 
git diff --staged # after git add
```

###### Commit changes to the git log
```bash
git commit -m "message goes here"
git commit --message "message goes here"
git commit --author="Vlad Dracula <vlad@tran.sylvan.ia>" # chan
git commit --amend -m "comment" #Amends most recent commit for small update, shorter than a reset w/ commit
```

###### Change author for a specific commit when pair coding
```bash
git commit --author="David Yakobovitch <david@gmail.com>"
```

###### View completed commits
```bash
git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
git log --pretty=oneline --max-count=2
git log --pretty=oneline --since='15 minutes ago'
git log --pretty=oneline --until='15 minutes ago'
git log --pretty=oneline --all
git log --all --pretty=format:'%h %cd %s (%an)' --since='7 days ago'
git log
```

###### View files excluded by .gitignore
```bash
[text_editor_name] .gitignore
nano .gitgnore
```

###### Tags: A replacement for Hash strings
```bash
git tag v1 #Adds a tag to a commit
git tag <hash> #Adds a tag to a commit named with its hash 
git tag #View tags
git tag -d tagname #Deletes the tag name
```

###### Checkout: Recover previous verisons
```bash
git checkout v1 # Checkout the branch to a specific commit with tag
git checkout v2~1 # Checkouts 1 previous version with tag
git checkout v2^1 # Checkouts 1 previous version with tag
git checkout filename #Checkouts a specific filename
```

###### Reset
```bash
git reset HEAD <filename> #Undoes changes to the file from recent commit
git reset --hard <tag or hash> #Undoes commit back to the previous version
git fetch origin # Drops all your local changes and fetches latest history from server 
```

###### Revert
```bash
git revert HEAD #Reverts changes after committing if accidently committed
```

###### History: View all commits
```bash
# First, be sure to set in ~/.gitconfig an [alias] for hist
# [alias]
# hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
git hist master --all # Show all commit history
git hist --all # Show all history, even when a hard reset is performed, as all history is preserved
# Note: HEAD is the currently checked out commit.
```

###### Exit Nano or Vi or Vim without saving changes
```bash
q!
Shift :q
```

###### Exit & Save Nano or Vi
```bash
Escape
Shift + :
wq
Enter
```

###### Keystrokes to Exit & Save in Nano or Vi
```bash
Ctrl + X
Y
Enter
```

#### Unix Commands

###### Show all hidden files and folders in active directory
```bash
ls -A
ls -lha # Human readable format
```

### Edit the Commit Message
git commit --amend                  # start $EDITOR to edit the message
git commit --amend -m "New message" # set the new message directly


###### Display the most recent commit
```bash
git show #displays the most recent commit on the HEAD
```

###### Display the most recent commit
```bash
git show #displays the most recent commit on the HEAD
```

###### Display the commit in a pretty-print format
```bash
git cat-file -p <commit-ID> #can be run on the tree (points to blobs), blob (sub-directory of files) or commit (points to tree) 
```

###### Re-load shell with updates to profile or config
```bash
source ~./profile
source ~/.gitconfig 
```

###### Display wordcount of an object (requires ruby installation)
```bash
cat .git/objects/ce/<commit> | inflate | wc -c
```


###### Explore Hex characters
```bash
cat .git/objects/ce/<commit> | inflate | hexdump -C
```

###### Gitk
```bash
gitk # Visual interactive of git repository
```


git status
git log --patch cats.txt #Shows log and diff together
4. git push origin master
git remote add origin url #becomes master 

git push -u origin master #Sends to web 

git log --patch filename.txt
git log -1
git log --oneline #shows as one line per commit 
git log --format=full

# Revision changes 
1. git diff HEAD or 8a61d07 mars.txt #show the most recent change(s)
git diff HEAD~1 mars.txt
2. git show HEAD~2 mars.txt #view version to roll back
ctrl + shift + c #gitbash copy for PC 
ctrl + v #pastes for gitbash 
3. git checkout HEAD~1 or f22b25e mars.txt # roll back one line
git reset HEAD mars.txt #removes staged files
git checkout -f master mars.txt #Checks out one previous commit on Github

unset SSH_ASKPASS #asks for password 
#For Proxys
git config --global http.proxy http://user:password@proxy.url
git config --global https.proxy http://user:password@proxy.url

# Merge conflicts between branches
git checkout feature 
git rebase -i master

git checkout feature
git merge master 
git merge master feature 

git revert 
git checkout 

git push --force

git merge-base feature master 

git stash # code available for later
git stash list # see the changes 
git stash apply #applies stash 
git stash apply stash@{1}
git checkout . # reset all uncomitted code
git stash branch 'debugging-branch' # saves stashes in new branch 
git stash drop stash@{2} #drops one stash at a time 
git stash clear # removes all stashes 

git reset --soft HEAD~1 # soft reset against messy code, but still exists so you can fix and re-commit 
git reset --hard HEAD~1 #permanently erases previous commit

git bisect start #launches git bisect utility 
git bisect bad [commitID] #indicate where a problem exists

git checkout [commitID] # to examine when in git bisect where the problem no longer occured

git bisect good [commitID] #git searches for where issue occured and resolves 
git bisect bad [no commit ID needed]  # if still bad 

git bisect good #once it's good 
git show #reveal the commit and where issue occured 

git bisect reset #reset branch to normal working state after 

git rebase -i HEAD~2 # be presented with last 3 commits --root # for local
pick [commitID] # a screen will appear and you can change all before pick to say squash to merge them
squash [commitID] # squash specific id into the pick 
git push 
git push --force #forces the push
Git rebase --abort #cancels the rebase 

git checkout #to explore changes to consider to commits 

git add -A  #git knows to remove it 
git commit --amend -v #to edit commit message 
git rebase --onto HEAD [commitID] master 

git rebase --continue 
git rebase --skip 

git rebase --interactive 
# if you didn't specify any tracking information for this branch 
# you will have to add upstream and remote branch information: 
git rebase --interactive origin branch

### Additional Git Options
git reset HEAD~2        # undo last two commits, keep changes
git reset --hard HEAD~2 # undo last two commits, discard changes  

git checkout -- Gemfile # reset specified path 

git reset filename          # or git remove --cached filename
echo filename >> .gitingore # add it to .gitignore to avoid re-adding it

git add forgotten_file 
git commit --amend

### Reverting Pushed Commits
git revert c761f5c              # reverts the commit with the specified id
git revert HEAD^                # reverts the second to last commit
git revert develop~4..develop~2 # reverts a whole range of commits
 
### undo the last commit, but don't create a revert commit 
git revert -n HEAD

### Avoid Repeated Merge conflicts
git config --global rerere.enabled true

### Gitbash Shortcuts
<li>Ctrl-a		Move to the start of the line.</li>
<li>Ctrl-e		Move to the end of the line.</li>
<li>Ctrl-b		Move back one character.</li>
<li>Alt-b		Move back one word.</li>
<li>Ctrl-f		Move forward one character.</li>
<li>Alt-f		Move forward one word.</li>
<li>Ctrl-] x	Where x is any character, moves the cursor forward to the next occurance of x.</li>
<li>Alt-Ctrl-] x	Where x is any character, moves the cursor backwards to the previous occurance of x.</li>
<li>Ctrl-u		Delete from the cursor to the beginning of the line.</li>
<li>Ctrl-k		Delete from the cursor to the end of the line.</li>
<li>Ctrl-w		Delete from the cursor to the start of the word.</li>
<li>Esc-Del		Delete previous word (may not work, instead try Esc followed by Backspace)</li>
<li>Ctrl-y		Pastes text from the clipboard.</li>
<li>Ctrl-l		Clear the screen leaving the current line at the top of the screen.</li>
<li>Ctrl-x Ctrl-u	Undo the last changes. <li>Ctrl-_ does the same</li>
<li>Alt-r		Undo all changes to the line.</li>
<li>Alt-Ctrl-e	Expand command line.</li>
<li>Ctrl-r		Incremental reverse search of history.</li>
<li>Alt-p		Non-incremental reverse search of history.</li>
<li>!!		Execute last command in history</li>
<li>!abc		Execute last command in history beginning with abc</li>
<li>!abc:p		Print last command in history beginning with abc</li>
<li>!n		Execute nth command in history</li>
<li>!$		Last argument of last command</li>
<li>!^		First argument of last command</li>
<li>^abc^xyz	Replace first occurance of abc with xyz in last command and execute it</li>

### Aliases:

The following aliases could be set in your .bash_aliases file to save keystrokes when processing git commands.

# ----------------------
# Git Aliases
# ----------------------
```
Aliases for .profile or [alias] for .gitconfig
alias gaa='git add .'
alias gc='git commit'
alias ga='git add'
alias gaaa='git add --all'
alias gau='git add --update'
alias gb='git branch'
alias gbd='git branch --delete '
alias gcm='git commit --message'
alias gcf='git commit --fixup'
alias gco='git checkout'
alias gcob='git checkout -b'
alias gcom='git checkout master'
alias gcos='git checkout staging'
alias gcod='git checkout develop'
alias gd='git diff'
alias gda='git diff HEAD'
alias gi='git init'
alias glg='git log --graph --oneline --decorate --all'
alias gld='git log --pretty=format:"%h %ad %s" --date=short --all'
alias gm='git merge --no-ff'
alias gma='git merge --abort'
alias gmc='git merge --continue'
alias gp='git pull'
alias gpr='git pull --rebase'
alias gr='git rebase'
alias gs='git status'
alias gss='git status --short'
alias gst='git stash'
alias gsta='git stash apply'
alias gstd='git stash drop'
alias gstl='git stash list'
alias gstp='git stash pop'
alias gsts='git stash save'
```

##### FAQs:
<ul>
<li><a href="https://alanbarber.com/post/how-to-customize-the-git-for-windows-bash-shell-prompt/">Customize Git Bash for Windows</a></li>
<li><a href="http://kurtdowswell.com/software-development/git-bash-aliases/">Set Aliases Gitbash Windows</a></li>
</li>
<li><a href="https://jonsuh.com/blog/git-command-line-shortcuts/">Additional Aliases</a></li>
<li><a href="https://stackoverflow.com/questions/2553786/how-do-i-alias-commands-in-git">Customize Alias in Mac</a></li>
<li><a href="https://help.github.com/en/articles/changing-a-remotes-url">Change SSH to HTTPS for Git</a></li>
<li><a hrf="https://stackoverflow.com/questions/32268986/git-how-to-remove-proxy/32269086">Reset HTTPS Proxy</a></li>
</ul>

### References:
- https://www.toptal.com/git/tips-and-practices
- https://www.atlassian.com/git/tutorials/what-is-version-control
- https://gist.github.com/citizen428/16fb925fcca59ddfb652c7cb22809018
- http://gitimmersion.com/
- [Git Manual Online](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/)
- [Git User Manual](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html)
- [Blog: The Thing About Git](https://tomayko.com/blog/2008/the-thing-about-git)
- [The Simple Git Guide](http://rogerdudler.github.io/git-guide/)
- [Pro Git Book](https://book.git-scm.com/book/en/v2)
- [Github.com Help](https://help.github.com/en)
- [Think Like a Git](http://think-like-a-git.net/)
- [Fork - Merge Visualizer for Windows/Mac](https://fork.dev/windows)

How do I set up tree on windows?
https://superuser.com/questions/531592/how-do-i-add-the-tree-command-to-git-bash-on-windows

How do I rename my Windows computer for Gitbash?
https://kb.iu.edu/d/ajnx

How do I customize Git bash display for Windows?
https://alanbarber.com/post/how-to-customize-the-git-for-windows-bash-shell-prompt/

How do I change default Git location launch for Jupyter and Git bash on Windows?
http://practicalseries.com/1002-vcs/03-03-install.html

How to set Conda commands to run from git bash on Windows 10?
https://stackoverflow.com/questions/44597662/conda-command-is-not-recognized-on-windows-10?rq=1
