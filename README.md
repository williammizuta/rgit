rgit
====

Script to help wrangle multiple git repositories. Currently, it can show the status of all repositories at a glance, and safely `git pull` all of them.

Setup
====
Clone the repository somewhere on your home folder. Let's suppose it is on ~/bin:

    ~/bin$ git clone git@github.com:rafaeldff/rgit.git rgit
    
Then source it on your .bashrc:

    [[ -e "$HOME/bin/rgit/recursive-git.sh" ]] && . "$HOME/bin/rgit/recursive-git.sh" 
    
That's it.


Usage
====

The script operates on all git repository clones on subdirectories, even indirect, of the current directory. Currently, it sports two commands:

`rgit`: shows the status of the repositories at a glance:

![Sample output](https://gist.github.com/rafaeldff/7158274/raw/ec6ee3681b636b7d323d47f3fa87042ef13d5be4/2013-10-25-144453_954x534_scrot.png)

It shows, for each repository: the current branch, whether the working copy is dirty or clean, whether there are commits to push or pull to/from the upstream branch. This entails a `git fetch` for each repository to get updated information.



`rgit pull`: effectively does a `git pull` for each repository in a safe way. By this I mean that it will not attempt to merge, it only pulls when a clean fast-forward is possible. 

