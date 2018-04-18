Bash cheat sheet
================

## Bash basics
```bash
env                 # displays all environment variables

echo $SHELL         # displays the shell you're using
echo $BASH_VERSION  # displays bash version

bash                # if you want to use bash (type exit to go back to your previously opened shell)
whereis bash        # finds out where bash is on your system
which bash          # finds out which program is executed as 'bash' (default: /bin/bash, can change across environments)

clear               # clears content on window (hide displayed lines)
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