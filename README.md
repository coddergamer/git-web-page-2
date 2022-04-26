# git-web-page-2
## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```


##### Config
git config --global user.name “[firstname lastname]”
git config --global user.email “[valid-email]”
git config --global color.ui auto

##### SETUP & INIT
git init
git clone [url]

##### STAGE & SNAPSHOT
    git status
    show modified files in working directory, staged for your next commit

    git add [file]
    add a file as it looks now to your next commit (stage)

    git reset [file]
    unstage a file while retaining the changes in working directory

    git diff
    diff of what is changed but not staged

    git diff --staged
    diff of what is staged but not yet committed

    git commit -m “[descriptive message]”
    commit your staged content as a new commit snapshot


##### BRANCH & MERGE

    git branch
    list your branches. a * will appear next to the currently active branch
    
    git branch [branch-name]
    create a new branch at the current commit
    
    git checkout
    switch to another branch and check it out into your working directory
   
    git merge [branch]
    merge the specified branch’s history into the current one
    
    git log
    show all commits in the current branch’s history


##### INSPECT & COMPARE

    git log
    show the commit history for the currently active branch
    
    git log branchB..branchA
    show the commits on branchA that are not on branchB
    
    git log --follow [file]
    show the commits that changed file, even across renames
    
    git diff branchB...branchA
    show the diff of what is in branchA that is not in branchB
    
    git show [SHA]
    show any object in Git in human-readable format

##### TRACKING PATH CHANGES

    git rm [file]
    delete the file from project and stage the removal for commit
    
    git mv [existing-path] [new-path]
    change an existing file path and stage the move
    
    git log --stat -M
    show all commit logs with indication of any paths that moved



##### SHARE & UPDATE

    git remote add [alias] [url]
    add a git URL as an alias

    git fetch [alias]
    fetch down all the branches from that Git remote
    
    git merge [alias]/[branch]
    merge a remote branch into your current branch to bring it up to date
    
    git push [alias] [branch]
    Transmit local branch commits to the remote repository branch
    
    git pull
    fetch and merge any commits from the tracking remote branch

##### REWRITE HISTORY

    git rebase [branch]
    apply any commits of current branch ahead of specified one
    
    git reset --hard [commit]
    clear staging area, rewrite working tree from specified commit
    
##### TEMPORARY COMMITS

    git stash
    Save modified and staged changes
    
    git stash list
    list stack-order of stashed file changes
    
    git stash pop
    write working from top of stash stack
    
    git stash drop
    discard the changes from top of stash stack


##### IGNORING PATTERNS

    Preventing unintentional staging or commiting of files
    git config --global core.excludesfile [file]
    system wide ignore pattern for all local repositories

## Features

- Import a HTML file and watch it magically convert to Markdown
- Drag and drop images (requires your Dropbox account be linked)
- Import and save files from GitHub, Dropbox, Google Drive and One Drive
- Drag and drop markdown and HTML files into Dillinger
- Export documents as Markdown, HTML and PDF

Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ git config --global user.name "[aniket]"  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ git config --global user.email "[aniketp@sjcem.edu.in]"  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ touch file.txt  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ touch file1.txt  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ ls file.txt  file1.txt  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ git status fatal: not a git repository (or any of the parent directories): .git  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands $ git init Initialized empty Git repository in D:/BE IT/DevOps lab/Git commands/.git/ ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands (master) $ git status On branch master  No commits yet  Untracked files:   (use "git add <file>..." to include in what will be committed)         file.txt         file1.txt  nothing added to commit but untracked files present (use "git add" to track)  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands (master) $ git add file.txt  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands (master) $ git status On branch master  No commits yet  Changes to be committed:   (use "git rm --cached <file>..." to unstage)         new file:   file.txt  Untracked files:   (use "git add <file>..." to include in what will be committed)         file1.txt   ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands (master) $ git add .  ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands (master) $ git status On branch master  No commits yet  Changes to be committed:   (use "git rm --cached <file>..." to unstage)         new file:   file.txt         new file:   file1.txt   ADMIN@LAPTOP-0MCTR32M MINGW64 /d/BE IT/DevOps lab/Git commands (master) $ git commit -m "First Commit" [master (root-commit) a35b9f2] First Commit 
ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  status On  branch  master nothing  to  commit,  working  tree  clean ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  echo  "This  is  file  1"  >>  file1.txt ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  add  . warning:  LF  will  be  replaced  by  CRLF  in  file1.txt. The  file  will  have  its  original  line  endings  in  your  working  directory ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  status On  branch  master Changes  to  be  committed: (use  "git  restore  --staged  <file>..."  to  unstage) modified:    file1.txt ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  commit  -m  "After  Chnages" [master  a5b69f8]  After  Chnages 1  file  changed,  1  insertion(+) ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  remote  add  origin  https://github.com/Aniket0501/Test1.git ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  remote origin ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  push  -u origin  master remote:  Permission  to  Aniket0501/Test1.git  denied  to  Aniket0501. fatal:  unable  to  access  'https://github.com/Aniket0501/Test1.git/':  The  requested  URL returned  error:  403 ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  push  -u  origin  master remote:  Permission  to  Aniket0501/Test1.git  denied  to  Aniket0501. fatal:  unable  to  access  'https://github.com/Aniket0501/Test1.git/':  The  requested  URL returned  error:  403 ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  push  -u  origin  master Enumerating  objects:  6,  done. Counting  objects:  100%  (6/6),  done. Delta  compression  using  up  to  4  threads Compressing  objects:  100%  (4/4),  done. Writing  objects:  100%  (6/6),  470  bytes  |  39.00  KiB/s,  done. Total  6  (delta  0),  reused  0  (delta  0),  pack-reused  0 To  https://github.com/Aniket0501/Test1.git *  [new  branch]       master  ->  master branch  'master'  set  up  to  track  'origin/master'. ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $ echo  "File  Updated"  >>file.txt ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $ ls file.txt   file1.txt ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  status On  branch  master Your  branch  is  up  to  date  with  'origin/master'. 
ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  add  file.txt warning:  LF  will  be  replaced  by  CRLF  in  file.txt. The  file  will  have  its  original  line  endings  in  your  working  directory ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  commit  -m  "Afetr  second  changes" [master  a3d2424]  Afetr  second  changes 1  file  changed,  1  insertion(+) ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  log commit  a3d2424a4539500415f57313d882409c396fbc7f  (HEAD  ->  master) Author:  [aniket]  <[aniketp@sjcem.edu.in]> Date:    Mon  Apr  25  23:45:47  2022  +0530 Afetr  second  changes commit  a5b69f8a1ff5361efa7d51853f07b92bf74ec498  (origin/master) Author:  [aniket]  <[aniketp@sjcem.edu.in]> Date:    Mon  Apr  25  23:32:41  2022  +0530 After  Chnages commit  a35b9f2d42c147663ecf399841ccf3378097b254 Author:  [aniket]  <[aniketp@sjcem.edu.in]> Date:    Mon  Apr  25  23:31:49  2022  +0530 First  Commit ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  push  -u  origin  master Enumerating  objects:  5,  done. Counting  objects:  100%  (5/5),  done. Delta  compression  using  up  to  4  threads Compressing  objects:  100%  (2/2),  done. Writing  objects:  100%  (3/3),  287  bytes  |  143.00  KiB/s,  done. Total  3  (delta  0),  reused  0  (delta  0),  pack-reused  0 To  https://github.com/Aniket0501/Test1.git a5b69f8..a3d2424   master  ->  master branch  'master'  set  up  to  track  'origin/master'. ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  branch  feature ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  checkout  feature Switched  to  branch  'feature' ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $ ls file.txt   file1.txt ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $  git  status On  branch  feature nothing  to  commit,  working  tree  clean ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $  echo  "updating"  >>file1.txt ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $  git  status On  branch  feature 
ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $  git  add  . warning:  LF  will  be  replaced  by  CRLF  in  file1.txt. The  file  will  have  its  original  line  endings  in  your  working  directory ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $  git  commit  -m  "final  commit" [feature  dcc91ea]  final  commit 1  file  changed,  1  insertion(+) ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (feature) $  git  checkout  master Switched  to  branch  'master' Your  branch  is  up  to  date  with  'origin/master'. ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  merge  feature Updating  a3d2424..dcc91ea Fast-forward file1.txt  |  1  + 1  file  changed,  1  insertion(+) ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  push  -u  origin  master Enumerating  objects:  5,  done. Counting  objects:  100%  (5/5),  done. Delta  compression  using  up  to  4  threads Compressing  objects:  100%  (2/2),  done. Writing  objects:  100%  (3/3),  291  bytes  |  145.00  KiB/s,  done. Total  3  (delta  0),  reused  0  (delta  0),  pack-reused  0 To  https://github.com/Aniket0501/Test1.git a3d2424..dcc91ea   master  ->  master branch  'master'  set  up  to  track  'origin/master'. ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  push  -u  origin  feature Enumerating  objects:  12,  done. Counting  objects:  100%  (12/12),  done. Delta  compression  using  up  to  4  threads Compressing  objects:  100%  (8/8),  done. Writing  objects:  100%  (12/12),  984  bytes  |  246.00  KiB/s,  done. Total  12  (delta  0),  reused  0  (delta  0),  pack-reused  0 remote: remote:  Create  a  pull  request  for  'feature'  on  GitHub  by  visiting: remote:       https://github.com/Aniket0501/Test1/pull/new/feature remote: To  https://github.com/Aniket0501/Test1.git *  [new  branch]       feature  ->  feature branch  'feature'  set  up  to  track  'origin/feature'. ADMIN@LAPTOP-0MCTR32M  MINGW64  /d/BE  IT/DevOps  lab/Git  commands  (master) $  git  pull  --rebase remote:  Enumerating  objects:  5,  done. remote:  Counting  objects:  100%  (5/5),  done. remote:  Compressing  objects:  100%  (2/2),  done. remote:  Total  3  (delta  0),  reused  0  (delta  0),  pack-reused  0 Unpacking  objects:  100%  (3/3),  680  bytes  |  3.00  KiB/s,  done. From  https://github.com/Aniket0501/Test1 dcc91ea..127a73b   master       Updating  dcc91ea..127a73b Fast-forward file1.txt  |  1  + 1  file  changed,  1  insertion(+) 
