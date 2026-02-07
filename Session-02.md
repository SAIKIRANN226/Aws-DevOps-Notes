### Basic Linux commands
- ls ---> List sub directories.
- cd ---> Change directory.
- cd .. ---> To change the current working directory to its parent directory.
- / ---> Root directory.
- "-" ---> File; w ---> Write; r ---> Read; x ---> Execute
- ls -l ---> Lengthy format in alphabetical order.
- ls -lr ---> Lengthy format in reverse alphabetical order.
- ls --help ---> Will provide all the commands regarding ls, however we dont use all.
- ls -lt ---> Lengthy format based on latest timing.
- ls -ltr ---> Lengthy format based on oldest timing.
- ls -la ---> Lists all folders and files including hidden.
- touch ---> Creates only empty file.
- mkdir ---> Creates only empty folder. Blue colour is folder and white colour is file.

### CRUD (CREATE, READ, UPDATE, DELETE)
So in entire software (or) you take any technology the background will be CRUD. Example facebook login (or) signup (or) update etc. What ever you do CRUD will happen in the background.

### Updating file with content
- cat > file-name and then start entering content (Replaces the content)
- cat >> file-name will appends new content. To save this ---> Press enter and ctrl+D
- To read file ---> cat <file-name>

### Remove file and folder
- rm <file-name> ---> Deletes the file
- rmdir <folder-name> ---> Deletes the empty folder
- rm -r <folder-name> ---> Deletes folder and files init ("r" means recursive, go inside and delete everything)

### Copy command
- cp <source_where_the_file_is> <destination>
- Usage is "cp sample /Videos"
- cp -r ---> recursive and Usage is "cp -r sample /Videos"

### Move command
With in the same folder if you use mv command, it works as rename also. So mv command can also be used for renaming and Usage is "mv sample /Videos"

### grep command
- grep <word-to-find> <file-name>
Linux is a case sensitive. Linux will treat DevOps and DEVOPS as different. So to make this case insensitive (i) use "grep -i <word-to-find> <file-name>"

### Piping symbol
| ---> One command output will become the input to the another command

### wget vs curl commands
- wget is nothing but "get from web"
- wget ---> Used to download the file like example chrome .exe file
- curl ---> Downloads the content directly on the terminal without downloading file, we use this more. For
  example take your any session URL from git and try make sure use only RAW URL of the session. Usage is
  "curl <RAW_URL_of_the_session>"

### cut command
- https://github.com/saikiran-notes/blob/master/session.txt
- To cut this we use "delimiter" here ":" and "/" are the delimiters, we get fragments in delimiter
- Command ---> cut -d / -f1
- Usage ---> "echo https://github.com/saikiran-notes/blob/master/session.txt | cut -d /f1"

### awk command
- Command ---> awk -F / '{print $1F}' 
- To get last fragment just use awk -F / '{print $NF}'
- awk will divide the data based on columns so we use the above command.

### Head and tail commands
- head <file-name> ---> First 10 lines
- tail <file-name> ---> Last 10 lines
- To get specific ---> head -n 1 <file-name>  == first line, similarly tail also.

### VIM (visually improved editor)
- vim <file-name> then press "i" to enter the content or change the content
- To save that ===> :wq(write and quit)
- To not save ===> :q!
- To quit the file ===> :q
- To set numbers ===> :set nu
- To unset numbers ===> :set nonu
- Clear last search highlight ===> :noh
- You cannot go directly from "colon/command" mode to "insert" mode, you need to go to the "esc"mode first

### Searching in the file in server
- :/<word-to-search> ---> Search from the top
- :?<word-to-search> ---> Search from the bottom
- in ESC mode ---> shift+G ==> go to bottom, gg ==> will take to top
- "n" ---> pressing n n n ... will show what is next

We use Ctrl+F ---> To find (or) search (or) replace in windows, but to replace in linux 
":s/<word-to-find>/<word-to-replace>" replaces the word where your cursor is. This will replace only 
first occurance in the line. To replaces all use "/g", if you want any particular line then 
":2s" s=substitute. Example:- ":%s/sbin/SBIN/g" ===> %s means all occurances

- Where ever your curosor is just press "yy" it will copy
- Just press "p" to paste
- Just press "u" to undo
- Just press "10p" it will copy 10 times

### Points to remember
- curl downloads content directly on the terminal.
- grep -i <word-to-find> <file-name>
- :/<word-to-find> ---> In server from the top
- :/? <word-to-find> ---> In server from the bottom
