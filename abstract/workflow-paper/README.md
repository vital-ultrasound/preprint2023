# Workflow for ci and local built of TeX files

## Create repository and essential files and branches
**00.** Create repository    
**01.** clone it locally   
```
git clone git@github.com:free-cortex/framework.git
cd framework
git init
```

**03.** Create a pdfs branch for the pdf files [(see more)](https://www.freecodecamp.org/forum/t/push-a-new-local-branch-to-a-remote-git-repository-and-track-it-too/13222).
```
git checkout -b pdfs
rm -rf * README.md .github .gitignore *swp ~.git .idea 
git add -A
git commit -m 'clean pdfs branch'
git push origin pdfs
 ```

**02.** create .gitignore  
Download and edit `.gitignore`
```
# Ignored paths and directories
## pycharm project path
.idea

## vim temporal files
**/*.swp

## temporal TeX files
**/*.aux
**/*.fdb_latexmk
**/*.fls
**/*.log
**/*.nav
**/slides/main.pdf
**/*.snm
**/*.synctex.gz
**/*.toc
**/*.vrb
**/slides/_minted-main/*.*
```



## Create Github Actions
**01** Create a deploy key with `ssh-keygen -m PEM -t rsa -b 4096 -C "your_email@example.com"` [:link:](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
[:link:](https://jdblischak.github.io/2014-09-18-chicago/novice/git/05-sshkeys.html)

**02.** Add a new secret variable called `DEPLOY_KEY` in
`https://github.com/$PROJECT_NAME/$REPO_NAME/settings/secrets/actions` where `DEPLOY_KEY` is taken from `id_rsa` using    
```
xclip -selection clipboard < ~/.ssh/id_rsa
```
which looks like:  
```
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```
* Don't forget to "Adding your SSH key to the ssh-agent" and be authentified [:link:](https://docs.github.com/en/enterprise/2.13/user/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)
```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
ssh -T git@github.com 
```

## Create Github workflow
**03.** Create github action workflow
`.github/workflow/*.yml` and then create main.yml 
```
mkdir -p .github/workflows
cd .github/workflows && wget https://raw.githubusercontent.com/free-cortex/framework/main/.github/workflows/template.yml
mv template.yml $DESIRED_NAME.yml
```
* Setting up variables for pdf documents and keys in .github/workflows/main.yml. 
See this [template.yml](../.github/workflows/template.yml) as example.
Edit `template.yml` by changing branches and repository name.

**04.** Commit genesis in the main branch using `CI-CV` for CV (or no capital flags for CI build) in the commit 
```
git add . 
git commit -m "genesis commit CI-CV"
git branch -M main
git remote add origin git@github.com:free-cortex/framework.git
git push -u origin main
```



## Create a new LaTeX doc

**00.** Raise a new issue

**01.** checkout and pull main
```
git checkout main
git pull
```

**02.** create a new branch
```
git checkout -b $ISSUENUMBER-$BRANCHNAME
```

**03.** Create github action workflow
`.github/workflow/*.yml` and then create main.yml 
```
mkdir -p .github/workflows
cd .github/workflows && wget https://raw.githubusercontent.com/free-cortex/framework/main/.github/workflows/template.yml
mv template.yml $DESIRED_NAME.yml
```
* Setting up variables for pdf documents and keys in `.github/workflows/*.yml`. 
For instance, 
```
name: Compiling-TeX-$BRANCHNAME
on:
  push:
    branches:
      - main
      - 05-$BRANCHNAME
jobs:
  build:
    if: "contains(github.event.head_commit.message, 'CI-$BRANCHNAME')"
```
See this [template.yml](../.github/workflows/template.yml) as example.


**04.** commit genesis and add path/files and push them
```
git add -A
git commit -m ':fire: genesis of $BRANCHNAME [skip branches]'
git push origin $ISSUENUMBER-$BRANCHNAME
```

* Edit README for new actions and readme icons
```
## Slides
[![GitHub Actions Status](https://github.com/free-cortex/framework/workflows/Compiling-TeX-Slides/badge.svg)](https://github.com/free-cortex/framework/actions) [![ieee-poster](https://img.shields.io/badge/read-slides-blue.svg)](https://github.com/free-cortex/framework/blob/pdfs/slides.pdf)
```

**05.** Create pull request
```
Title: [WIP] Drafting $BRANCHNAME
Content: Resolves #$ISSUENUMBER
If CI is successful, tex file will be built [here](https://github.com/free-cortex/framework/blob/pdfs/$PDFFILE.pdf)
```

**06.** keep making commit until the issue is sorted out
```
git add -A
git commit -m ':fire: genesis of $BRANCHNAME'
git push origin $ISSUENUMBER-$BRANCHNAME
```
You can add capital CI and the type of document for its CI build or nothing 
See workflows [`*.yml`](../.github/workflows/) 



## Local build in Ubuntu 18.04 x64
### Installation of dependencies
```
mkdir -p $HOME/Downloads/latex && cd $HOME/Downloads/latex
wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
tar -xf install-tl-unx.tar.gz
rm install-tl-unx.tar.gz
cd $HOME
echo '# Setting PATH of the TeX Live binaries'
echo 'export PATH=/usr/local/texlive/2020/bin/x86_64-linux/:$PATH'
```

### Local build
In your terminal:
```
cd ~/unt-manuscript-2021/journal-of-imaging-2021/manuscript-tex
make clean && make && make view
make clean
```

## Local build in Windows 10 Enterprise Version 1803
### Generating a new SSH key and adding it to the ssh-agent
Use [`Git Bash` to set up SSH keys](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

### Installation of dependencies
01. Download [install-tl-windows.exe for Windows (18mb)](https://tug.org/texlive/acquire-netinstall.html)
02. Install TexLive at TEXDIR C:/texlive/2020; 
    * (run it anyway)
    * Disk space 7293 MB 
    * Tex Live Installer might take few minutes (90mins ish) as ~4056 packages are installed.
03. "When installation is complete, you will have to restart Windows, 
    and then you can run the TEX programs from a command prompt."
    [:link:](https://accelconf.web.cern.ch/Workshop99/Proceedings/Goossens.pdf)
04. Install Cygwin (Get that Linux feeling - on Windows)  
    04.01 Download and run [setup-x86_64.exe](https://cygwin.com/install.html)  
        Install it from the internet  
    04.02 Running installation  
        * Location: C:\cygwin64  
        * Use System Proxy Settings  
        * Choose a mirror   
        * Make sure to select the latest installers of: make, vim, evince.   
   04.03 Add these lines your .bashrc (vim .bashrc)  
        * alias cdc='cd /cygdrive/c'  
        * ll = 'ls -la'  
        * export C=/cygdrive/c  
   04.04 Close and open Cygwin  
   04.05 Accessing your files   
        cd /cygdrive/c/Users/$USERNAME/UNT/gift-surg/unt-manuscript-2021/journal-of-imaging-2021/manuscript-tex
05. Install make in GitBASH
    > Keep in mind you can easy add make, but it doesn't come packaged with all the standard UNIX build toolchain--so you will have to ensure those are installed and on your PATH, or you will encounter endless error messages.    
    [ref](https://gist.github.com/evanwill/0207876c3243bbb6863e65ec5dc3f058)
    
    05.01 Go to https://sourceforge.net/projects/ezwinports/     
    05.02 Download make-4.1-2-without-guile-w32-bin.zip (get the version without guile).  
    05.03 Extract zip.  
    05.04 Copy the contents to your Git\mingw64\ merging the folders, but do NOT overwrite/replace any existing files   

### Local build using GitBash
01. Open Gitbash and go to 
    cd `~/.../unt-manuscript-2021/journals/ieee-tbe-2021/manuscript-tex`
02. clean project, make project and open pdf
```bibtex
make clean && make && explorer main.pdf
```
04. commit changes
* add `CITBE` anywhere in your commit message for ci tex build


### Local build using Cygwin64 
01. Open Cygwin64
02. Go to with `cd /cygdrive/c/Users/$USERNAME/UNT/$MAIN_REPO/$REPONAME/$JOURNAL/manuscript-tex`
03. Built, clean and view
    * `make` 
    * cygstart.exe main.pdf #to view pdf
    * `make clean`
04. commit changes 
    * add `CITEX` anywhere in the commit message, when you do not build tex files with github action. 
    
## Multiple users working in the same branch 
### In pycharm
01. Checkout branch `origin/#NumberOfIssue-#BranchName`  
02. Click on the blue arrow (Ctrt+T) and choose `merge in coming changes into the current branch`  
    * 02.01 If one accidentally forgot to pull latest commits creating error when pushing files, one can do `git reset --hard HEAD~1`.
    For this case, be sure to copy your progress in a different file and put it back once you update the latest commits. 
03. Make your changes and commit with a message adding CITEX.  
:warning: User would try to avoid working on the same file as it might create conflicts (recommended to have a chat).
   
### Figures workflow using vector images
To create figures using vector files with inkscape, the following template is used 
where vectors path has svg files, `drawing-vNN.svg` where NN is the number of version, 
reference for other images and versions for png or pdf outputs. See one example of
 the path organisation:
```
.
├── Makefile
├── README.md
├── references
│   └── README.md
├── vectors
│   └── drawing-v00.svg
│   └── drawing-v01.svg
└── versions
    ├── drawing-v00.png
    ├── drawing-v01.png
    └── README.md
```
When creating a new version, modify `/vectors/drawing-v00.svg` 
and use the latest version for instance, a copy of v02 to create for instance v03.

#### GNU/Linux users:
Type the following in the terminal
```
make
mv versions/drawing.png versions/drawing-vNN.png #todo: add this in the makefile
```

#### Windows users:
open /svgpath/drawing.svg with inkscape using the explorer to make modifications (use `explorer .` in Cygwin)
Then go to the menu `File>Export PNG image...` export the figure. 
In such window select path and filename to be, for instance, `/versions/drawing-v03.png` and click Export as.

### References  
To avoid any conflicts when two persons are working in the same file such as references.
`references_blurs.bib` contains any potential references that can then be moved to 
a particular section references such as `references_introduction.bib`. 
It is recommended to have a plan and continuous communication in the first stages 
of drafting the papers.

### Building a PDF files from previous versions of the paper
One way to avoid keeping PDF files version in the repository (as this mainly build a pdf of the current tex and images)
is to go to a particular commit to then build the PDF of such commit. For example,
```
$ git checkout $CURRENT_BRANCH #(e.g. manuscript-for-ipcai2021) # change to manuscript branch
$ git log --oneline # show history of commit hashes 
    da1949a (HEAD -> manuscript-for-ipcai2021) Merge branch 'manuscript-for-ipcai2021' of https://github.com/gift-surg/us-needle-tracking-verification into manuscript-for-ipcai2021
    .
    .
    .
    aa81cbe update gitignore to ignore TexStudio files
    a07dca0 adds workflow for figures [skip mdpi2021] (see further discussion at #51)
$ git checkout a07dca0 # change to that version
$ cd .../manuscript-exe/ && make clean && make && evince main.pdf  # build your pdf output (instead of evince, `cygstart.exe main.pdf #to view pdf in windows`)
$ git checkout da1949a #HEAD -> manuscript-for-ipcai2021) # going back to the latest commit 
```

### Save local changes and pull repo using stash, pop, pull
``` 
$ git log --oneline
    38246bc (HEAD -> manuscript-for-ipcai2021, origin/manuscript-for-ipcai2021) refactors methods and materials sections and adds legacy figure for signal processing pipeline
    ed519ca adds figure v00 for coordinate systems
    8279905 cosmetic changes to title, author list, and acknowledgements

$ git stash list #This will list down all your stashes.
$ git stash save "my-save"
$ git pull
$ git log --oneline
    51a8ede (HEAD -> manuscript-for-ipcai2021, origin/manuscript-for-ipcai2021) Fix image size.
    b2fb176 Change phrasing and add guidelines for sig proc part.

$ git stash list #This will list down all your stashes.
$ git stash pop stash@{n} #To apply a stash and remove it from the stash stack, type:

Where n is the index of the stashed change.
```

### Rebase branch 
See the following comments to-rebase-local-branch-onto-remote-master using the terminal [ref](https://stackoverflow.com/questions/7929369/)
```
git checkout main
git pull origin main
git checkout RB
git rebase main
git push --force origin RB
```

## References
* [VIDEO: How to Install TeX Live and TeXstudio in Windows](https://www.youtube.com/watch?v=rUz5kRYP9w4)
* [How to Install LaTeX on windows 10](https://www.youtube.com/watch?v=cmVNPtW3RuQ)
* [tex-live-on-cygwin-a-few-tricks/](https://darrengoossens.wordpress.com/2014/07/16/tex-live-on-cygwin-a-few-tricks/)
* [how-to-name-and-retrieve-a-stash-by-name-in-git](https://stackoverflow.com/questions/11269256/)