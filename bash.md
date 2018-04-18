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

## Shortcuts
```bash
CTRL + A   # move to beginning of line
CTRL + B   # moves backward one character
CTRL + C   # halts the current command
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