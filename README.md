# cheat-sheets
Cheatsheets for developers

## JVM

Create Heap-dump:

```bash
jps (or ps aux | grep java)
jmap -dump:live,format=b,file=/tmp/dump.hprof pid
```

## Docker

Remove all unused containers, networks, images (both dangling and unreferenced), and optionally, volumes.
```bash
docker system prune -a

docker rmi <imageId>
```

Update and restart image
```bash
docker-compose pull && docker-compose up -d
```

Inspect log files
```bash
docker logs -f -n 10 <serviceName>

sudo docker logs <dockerPID> | less
```

Docker files:
```bash
/var/lib/docker/containers/<container_id>/<container_id>-json.log
```

Misc:
```bash
docker run -it -v $PWD:/data --rm debian
docker exec --it <dockerPID> bash
docker ps
```

## Gradle

Force updating all dependencies
```bash
./gradlew clean build --no-build-cache --refresh-dependencies --info
```

Update Gradle wrapper:
```bash
./gradlew wrapper --gradle-version 7.2
 ./gradlew --version
```

## Spring

Active Hiberate SQL Logging with Parameters:
```yaml
logging:
  level:
    org:
      hibernate:
        SQL:  DEBUG
        type.descriptor.sql.BasicBinder: TRACE
```

## Git

Checkout new branch:
```bash
git fetch
git pull
git branch -a | grep <branchName>
git checkout --track remoteBranchName
```

Undo a commit and redo
```bash
$ git commit -m "Something terribly misguided"             
$ git reset HEAD~  
<< edit files as necessary >>    
$ git add ...                      
$ git commit -c ORIG_HEAD   
```

Delete all local branches where the remote branches are also deleted:
```bash
git branch -vv | grep ': gone]'|  grep -v "\*" | awk '{ print $1; }' | xargs -r git branch -d
```

 Delete remote delted branches from local cache
 ```bash
 git fetch --prune
```

### Import an existing, unversioned code project

```bash
git init
git add --all
git commit -m "Initial Commit"

git remote add origin https://username@your.bitbucket.domain:7999/yourproject/repo.git 
git push -u origin master
```


## Github

- [GitHub Actions](https://github.com/sdras/awesome-actions)

[Github Search](https://github.com/search):
```
in:file extension:EXTENSION filename:FILENAME
```

## Kibana & Elastic

Show all indices:
```bash
GET /_cat/indices?h=h,s,i,id,p,r,dc,dd,ss,creation.date.string
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

## Linux: important directories

- /etc/passwd
- /etc/fstab
- /proc/swaps

## Linux commands

Use zsh-Shell!

### Examples

```bash
# shutdown
sudo shutdown -r now

# show column 13,5
cut -d":" -f 1,3,5 /etc/passwd | column -ts":"^
# same as above
sed -E 's/([^:]*):[^:]*:([^:]*):[^:]*:([^:]*):.*/\1:\2:\3/' /etc/passwd | column -ts":"

cat /etc/passwd | cut -d":" -f1,3,6 | sort -t":" -k1,1
cat /etc/passwd | cut -d":" -f1,3,6 | sort -n -t":" -k2,2

# Euro amount
egrep "^[0-9]+(,[0-9]{1,2}|,-)? EUR$|^EUR [0-9]+(,[0-9]{1,2}|,-)?$"

cut -d : -f 1,3,6 /etc/passwd | egrep -E '[^:]+:[0-9]+[0,2,4,6,8]:.+' |sort -t : -k 2 -n -u
```


### Files

- sort datei.txt | uniq 
- echo Maus | tr M H 
- column
- cut -d: -f1 /etc/passwd 
- sed s/Anton/Berta/g Textdatei 
- vi
- less 
- tail -n 10
- find . -name "*.py" -type f 
- grep -rnw './path/to/search/' -e 'SearchWord'
- egrep --color "([0-9]{4})-\1" 

### Directory and Files

- mkdir
- touch
- mv
- cp
- ls


### Process

- top
- atop
- htop
- free
- ps auxw
- pstree
- jobs
- nohup COMMAND &
- disown <Option> [%Jobnummer] 
- bg
- fg
- echo $$  (show current process)

### Disc
 
 ```bash
 fdisk -l
 mkfs.ntfs /dev/sdb1
 mkdir /mnt/ntfs
 mount /dev/sdb1 /mnt/ntfs
 less /etc/fstab
 ```
 
```bash
# create swap partition with 1GB
sudo dd if=/dev/zero of=/swap.img bs=1024 count=1048576
sudo chmod 600 /swap.img
sudo mkswap /swap.img
sudo swapon /swap.img
cat /proc/swaps
sudo swapoff /swap.img
```
 
 - blkid
 - lsblk
 - df -h 
 - du <options> <location of directory or file>
 
### Usermanagement

- sudo adduser xyz www-data # adds user xyz to group www-data
- sudo addgroup groupName
- chmod a+rwx datei # a:all +: add rightd, -: del rights
- sudo chown -c andreas /media/VERZEICHNIS 
- chgrp -c -R musik /opt/musik/ 
- id

```bash
sudo groupadd students
sudo useradd -m max -G students
sudo mkdir /home/students
sudo chown root:students /home/students
sudo chmod g+w /home/students
```

### Tools
 
 - bc -l (ibase=2;obase=10; 10011)
 - mc
 - tar xzf pa5-script.tgz
 - wget
 - curl
 - diff
 
### Misc

- uname -a
- nice
- clear
- echo

 ###  String Operations
 
 |Befehl |Ausgabe |Erklärung|
|---|---|---|
|a="wort"; | echo ${a^} |Wort 1. Buchstabe in Großbuchstaben wandeln|
|a="wort"; | echo ${a^^} |WORT alle Buchstaben in Großbuchstaben wandeln|
|a="WORT"; | echo ${a,} |wORT 1. Buchstabe in Kleinbuchstaben wandeln|
|a="WORT"; | echo ${a,,} |wort alle Buchstaben in Kleinbuchstaben wandeln|
|a="eins:zwei:drei"; | echo ${a%%:*} |eins alles ab erstem „:“ abschneiden (löschen)|
|a="eins:zwei:drei"; | echo ${a%:*} |eins:zwei alles ab letztem „:“ abschneiden|
|a="eins:zwei:drei"; | echo ${a#*:} |zwei:drei alles bis zu erstem „:“ abschneiden|
|a="eins:zwei:drei"; | echo ${a##*:} |drei alles bis zu letztem „:“ abschneiden|
|a="0123456789"; | echo ${a::4} |0123 Substring; erste 4 Zeichen|
|a="0123456789"; | echo ${a:2:4} |2345 Substring; ab Position 2; 4 Zeichen|
|a="0123456789"; | echo ${a:2} |23456789 Substring; alles ab Position 2|

### Regex

- egrep --color "([0-9]{4})-\1" 
- echo "0211/36262" | grep --color -E '...'

#### Basic Syntax

- `/.../`: Start and end regex delimiters
- `|`: Alternation
- `()`: Grouping


#### Position Matching

- `^`: Start of string or start of line in multi-line mode
- `\A`: Start of string
- `$`: End of string or end of line in multi-line mode
- `\Z`: End of string
- `\b`: Word boundary
- `\B`: Not word boundary
- `\<`: Start of word
- `\>`: End of word


#### Character Classes

- `\s`: Whitespace
- `\S`: Not whitespace
- `\w`: Word
- `\W`: Not word
- `\d`: Digit
- `\D`: Not digit
- `\x`: Hexade­cimal digit
- `\O`: Octal digit


#### Special Characters

- `\n`: Newline
- `\r`: Carriage return
- `\t`: Tab
- `\v`: Vertical tab
- `\f`: Form feed
- `\xxx`: Octal character xxx
- `\xhh`: Hex character hh


#### Groups and Ranges

- `.`: Any character except newline (\n)
- `(a|b)`: a or b
- `(…)`: Group
- `(?:…)`: Passive (non-c­apt­uring) group
- `[abc]`: a, b or c
- `[^abc]`: Not a, b or c
- `[a-z]`: Letters from a to z
- `[A-Z]`: Uppercase letters from A to Z
- `[0-9]`: Digits from 0 to 9


