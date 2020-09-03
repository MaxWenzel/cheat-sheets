# cheat-sheets
Cheatsheets for developers

## Git

Checkout new branch:
```bash
git fetch
git pull
git branch -a | grep <branchName>
git checkout --track remoteBranchName
```

Delete all local branches where the remote branches are also deleted:
```bash
git branch -vv | grep ': gone]'|  grep -v "\*" | awk '{ print $1; }' | xargs -r git branch -d
```

 Delete remote delted branches from local cache
 ```bash
 git fetch --prune
```



## IntelliJ

Shortcut | Action
------------ | -------------
Ctrl+Alt+L | Reformat code: Reformat the whole file or the selected fragment according to the current code style settings.
Ctrl+Shift+Enter | Complete current statement: Insert any necessary trailing symbols and put the caret where you can start typing the next statement.
Ctrl+Alt+V | Introduce Variable
Ctrl+E | View recent files
Alt+F7 | Find usages
Alt+1 | Focus the Project tool window
Ctrl+Shift+V | Clipboard History
Ctrl+E | Last Changes 
Ctrl+Shift+Enter | Complete Statement
Ctrl+J | Live Template
Alt+Enter | Language Injection
Alt+Shift+Up | Move line up
Alt+Shift+Down | Move line down
Ctrl+W | Mark code

## Windows

Kill process listening on port:
```bash
$ netstat -aon | findstr :<port>
$ Taskkill /PID <pid> /F
```

Shortcut | Action
------------ | -------------
Win+L | Lock screen
Win+D | show Desktop
Win+E | start Explorer
Win+R | Run command


## Shell
