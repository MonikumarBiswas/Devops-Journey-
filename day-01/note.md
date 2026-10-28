Day - 1 : 

Commands: 
1. mkdir 
2. touch 
3. nano 
4. cat 
5. cp , mv 
6. rm -r ( remove ) 
7. head , tail , 
8. tail -f filename ( show active log) 
9. less 
10 . ls , ls-R , ls-a , ls-la , ls-lh etc 

Day 1: Basic File and Text Commands
Goal: create, view, copy, move, and delete files and folders from the terminal, and read files in different ways.
Creating things
mkdir: make a directory
mkdir projects
mkdir -p projects/devops/notes    # -p creates parent folders as needed

touch: create an empty file (or update its timestamp)
touch notes.txt
touch a.txt b.txt c.txt

nano: simple terminal text editor
nano notes.txt

Save with Ctrl+O then Enter. Exit with Ctrl+X.
Viewing files
cat: print a whole file
cat notes.txt

Good for short files. For long files, use less.
head and tail: start and end of a file
head notes.txt          # first 10 lines
head -n 5 notes.txt     # first 5 lines
tail notes.txt          # last 10 lines
tail -n 20 notes.txt    # last 20 lines

tail -f: follow a file as it grows
tail -f /var/log/syslog

Shows new lines live as they are written. This is how you watch an active log. Stop with Ctrl+C. (Some systems use /var/log/messages or journalctl -f instead of syslog.)
less: scroll through a long file
less /var/log/syslog

Key	Action
Space / f	next page
b	previous page
/word	search forward
n	next match
q	quit

Copying, moving, deleting
cp: copy
cp notes.txt notes_backup.txt
cp -r projects projects_backup      # -r is needed for folders

mv: move or rename
mv notes.txt projects/              # move
mv old_name.txt new_name.txt        # rename

rm: delete
rm notes_backup.txt
rm -r projects_backup               # delete a folder and everything in it

There is no recycle bin in the terminal. Deleted means gone. Be especially careful with rm -rf, and always check the path first (ls the folder before you delete it).
Listing files with ls
Command	What it shows
ls	files in the current folder
ls -a	includes hidden files (names starting with .)
ls -l	long format: permissions, owner, size, date
ls -lh	long format with human-readable sizes (KB, MB)
ls -la	long format including hidden files
ls -R	recursive: lists subfolders too

Practice task I did
mkdir -p practice/day1
cd practice/day1
touch a.txt b.txt
echo "hello linux" > a.txt
cp a.txt c.txt
mv b.txt notes.txt
ls -la
cat a.txt
cd ..
rm -r day1
