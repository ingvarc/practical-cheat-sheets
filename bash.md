Bash cheat sheet
================

## The basics
```bash
env                 # displays all environment variables

echo $SHELL         # displays the shell you're using
echo $BASH_VERSION  # displays bash version

bash                # if you want to use bash (type exit to go back to your previously opened shell)
whereis bash        # finds out where bash is on your system
which bash          # finds out which program is executed as 'bash' (default: /bin/bash, can change across environments)

clear               # clears content on window (hide displayed lines)
!!                  # repeats the last command
exit                # logs out of current session
```

## Bash Variables
```bash
BASH_ENV   # startup file path  
INPUTRC    # readline start default
CDPATH     # 'cd' searchpath    
LANG       # locale default
COLUMNS    # width of display   
LC_*       # locale categories
FCEDIT     # default fc editor  
LINES      # height of display
HISTFILE   # history list path
HISTSIZE   # max hist entries  
MAIL       # mail pathname
MAILCHECK  # how often, in seconds
MAILPATH   # :-separated list for mail
HOME       # user default dir   
IFS        # field separators 
PATH       # :-separated list for cmds
```

## Shortcuts
```bash
CTRL + A   # move to beginning of line
CTRL + B   # moves backward one character
CTRL + C   # halts the current command (first try)
CTRL + \   # halts the current command (second try)
CTRL + D   # deletes one character backward or logs out of current session, similar to exit
CTRL + E   # moves to end of line
CTRL + F   # moves forward one character
CTRL + G   # aborts the current editing command and ring the terminal bell
CTRL + J   # same as RETURN
CTRL + K   # deletes (kill) forward to end of line
CTRL + L   # clears screen and redisplay the line
CTRL + M   # same as RETURN
CTRL + N   # next line in command history
CTRL + P   # previous line in command history
CTRL + R   # searches backward
CTRL + S   # searches forward
CTRL + T   # transposes two characters
CTRL + U   # kills backward from point to the beginning of line
CTRL + V   # makes the next character typed verbatim
CTRL + W   # kills the word behind the cursor
CTRL + X   # lists the possible filename completefions of the current word
CTRL + Y   # retrieves (yank) last item killed
CTRL + Z   # stops the current command, resume with fg in the foreground or bg in the background
Ctrl + ?   # erase last character
```

## File commands
```bash
ls                            # lists your files
ls -l                         # lists your files in 'long format', which contains the exact size of the file, who owns the file and who has the right to look at it, and when it was last modified
ls -a                         # lists all files, including hidden files
ln -s <filename> <link>       # creates symbolic link to file
touch <filename>              # creates or updates your file
cat > <filename>              # places standard input into file
more <filename>               # shows the first part of a file (move with space and type q to quit)
head <filename>               # outputs the first 10 lines of file
tail <filename>               # outputs the last 10 lines of file (useful with -f option)
emacs <filename>              # lets you create and edit a file
mv <filename1> <filename2>    # moves a file
cp <filename1> <filename2>    # copies a file
rm <filename>                 # removes a file
diff <filename1> <filename2>  # compares files, and shows where they differ
wc <filename>                 # tells you how many lines, words and characters there are in a file
chmod -options <filename>     # lets you change the read, write, and execute permissions on your files
gzip <filename>               # compresses files
gunzip <filename>             # uncompresses files compressed by gzip
gzcat <filename>              # lets you look at gzipped file without actually having to gunzip it
lpr <filename>                # print the file
lpq                           # check out the printer queue
lprm <jobnumber>              # remove something from the printer queue
genscript                     # converts plain text files into postscript for printing and gives you some options for formatting
dvips <filename>              # print .dvi files (i.e. files produced by LaTeX)
grep <pattern> <filenames>    # looks for the string in the files
grep -r <pattern> <dir>       # search recursively for pattern in directory
```

## Special characters
```bash
~  # home directory                    #  # comment                             
$  # variable expression               &  # background job                     
;  # shell command separator           /  # pathname directory separator      
\  # quote (escape) next character     |  # pipe                              
*  # string wildcard                   ?  # single-character wildcard         
(  # start subshell                    )  # end subshell                      
[  # start character-set wildcard      ]  # end character-set wildcard        
{  # start command block               }  # end command block                 
'  # strong quote (prevents subs)      "  # weak quote (allows subs)           
<  # input redirect                    >  # output redirect                   
!  # logical NOT                       || # logical OR                         
&& # logical AND                       \  # Return  continue on next line
.  # (dot builtin: execute)            :  # (null builtin: returns true)
<< # here document                     >> # append output
```

## File attribute operators
```bash
-e   # file exists    
-d   # file exists and is a directory 
-f   # file exists and is a normal file
-s   # file exists and is not empty
-r   # user has read permission for the file  
-w   # user has write permission for the file
-x   # user has execution permission for a normal file or user has search permission for a directory
-O   # user owns the file
-G   # user's group id has access to the file
-nt  # newer than (modification date of file)
-ot  # older than (modification date of file)
```

## Arithmetic assignment
````bash
let x=1+4          # value of $x is 5
     ='1 + 4'      # 5
     ='(2+3) * 5'  # 25
     ='2 + 3 * 5'  # 17
     ='17 / 3'     # 5
     ='17 % 3'     # 2         
                            bitwise:
     ='1<<4'       # 16         00001  ->   10000
     ='48>>3'      # 6         110000  ->  000110
     ='17 & 3'     # 1      10001 & 11 ->   00001  
     ='17 | 3'     # 19     10001 | 11 ->   10011
     ='17 ^ 3'     # 18     10001 ^ 11 -> 10010
````

## I/O redirection
```bash
cmd1 | cmd2  # use stdout of cmd1 as stdin for cmd2
     > file  # save stdout to file
     < file  # use file as stdin
    >> file  # append stdout to file (create file if nonexistent)
    >| file  # force stdout to file (even if noclobber is set)
  n >| file  # force stdout to file from descriptor n (even...)
    <> file  # use file as both stdin and stdout (process in place)
  n <> file  # use as both stdin and stdout for file descriptor n
    << label # use here-document (within scripts specifies batch input)
   n > file  # direct file descriptor n to file
   n < file  # take file descriptor n from file
  n >> file  # append descriptor n to file (or create file for n)
  n >&       # duplicate stdout to file descriptor n
  n <&       # duplicate stdin from file descriptor n
  n >& m     # make file descriptor n a copy of the stdout fd
  n <& m     # make file descriptor n a copy of the stdin  fd 
    >& file  # send stdout and stderror to file
    <& -     # close stdin
    >& -     # close stdout
  n <& -     # close input  from file descriptor n
  n >& -     # close output from file descriptor n
```

## String comparison operators
```bash
 (truth = 0)                          
=    # matches                        
!=   #  does not match                 
<    # less than                      
>    # greater than                   
-n   # not null (length > 0)          
-z   #  null (length = 0)  
```       
           
 
## Integer comparison operators
```bash
 (truth = 1)
-lt  # less than
-le  # less than or equal 
-eq  # equal  
-ge  # greater than or equal
-gt  # greater than
-ne  # not equal
```

## Arithmetic operators    
```bash
+    # addition                        
-    # subtraction                     
*    # multiplication                  
/    # division (w/ truncation)        
%    # remainder                       
<<   # bit-shift left                  
>>   # bit-shift right                 
&    # bit-wise and                    
|    # bit-wise or
~    # bit-wise not
!    # bit-wise not
^    # bit-wise exclusive or
```                           
### Arithmetic expression $((   ))
```bash
 echo "Only $(( (365-$(date +%j)) / 7 )) weeks until the New Year"
``` 

## Relational operators
```bash
<    # less than
>    # greater than
<=   # less than or equal to
>=   # greater than or equal to
==   # equal to
!=   # not equal to
&&   # logical and
||   # logical or
```

## Substitution operators
```bash
${#varname}         # returns the length of varname
${varname:-word}    # returns word if varname is undefined 
${varname:=word}    # sets varname to word if varname is undefined
${varname:+word}    # returns word if varname exists and isn't null, otherwise returns null
${varname:?message} # prints varname and message and aborts command if varname is undefined
```

## Frequently used regular expressions
```regexp
'^.*, [A-Z][A-Z] [0-9]{5}-[0-9]{4} '         # city, state zip
'[A-Z][a-z]\{3,9\} [0-9]\{1,2}, [0-9]\{4\}'  # month, day, year
'[0-9]\{3\}-[0-9]\{2\}-[0-9]\{4\}'           # soc-sec-number
'[0-9]\{3\}-[0-9]\{3\}-[0-9]\{4\}'           # telephone number
'\$ [0-9]*\.[0-9]\{2\}'                      # dollars and cents
'^$'                                         # blank line 
'^.*$'                                       # an entire line
' *'                                         # one or more spaces 
```
> for best results, invoke bash with the --posix option

## Variables always available within a script
```bash
$0    # script name                   
$1    # first passed parameter 
$2    # second passed parameter
$n    # nth passed parameter
$*    # all parameters but $0         
$#    # number of tokens in $*        
$?    # exit status of a command
$$    # process id
$@    # quoted passed parameters ("$1","$2",...) and all keyword params
```

## SSH
```bash
ssh user@host            # connects to host as user
ssh -p <port> user@host  # connects to host on specified port as user
ssh-copy-id user@host    # adds your ssh key to host for user to enable a keyed or passwordless login
```

## System info
```bash
whoami                 # returns your username
passwd                 # lets you change your password
quota -v               # shows what your disk quota is
date                   # shows the current date and time
cal                    # shows the month's calendar
uptime                 # shows current uptime
w                      # displays whois online
finger <user>          # displays information about user
uname -a               # shows kernel information
man <command>          # shows the manual for specified command
df                     # shows disk usage
du <filename>          # shows the disk usage of the files and directories in filename (du -s give only a total)
last <yourUsername>    # lists your last logins
ps -u yourusername     # lists your processes
kill <PID>             # kills (ends) the processes with the ID you gave
killall <processname>  # kill all processes with the name
top                    # displays your currently active processes
bg                     # lists stopped or background jobs ; resume a stopped job in the background
fg                     # brings the most recent job in the foreground
fg <job>               # brings job to the foreground
```

## Network commands
```bash
ping <host>     # pings host and outputs results
whois <domain>  # gets whois information for domain
dig <domain>    # gets DNS information for domain
dig -x <host>   # reverses lookup host
wget <file>     # downloads file
```