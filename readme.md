#### Resources
- [ ] coursera ["Command Line in Linux"](https://www.coursera.org/learn/command-line-linux/supplement/MhGNK/project-based-course-overview)
- [ ] [hackerrank](https://www.hackerrank.com/domains/shell)
- [ ] [leetcode](https://leetcode.com/problemset/shell/)
- [ ] [interviewbit](https://www.interviewbit.com/courses/shell/)


### Coursera "Command Line in Linux"
Outline
- List files and directories using `ls`    
- Use the `cd` command to change directories
- Use `touch`, `copy`, `mkdir`, and `rm` to create and remove files and directories    


Summary

#### Display the home directory from a terminal
- `pwd`: display the current locations
- `echo`: print whatever follows 
- `$`: contents of shell environment variable
- `echo $SHELL`, `echo $HOME`: print the shell/home env
- `env`: return a whole list of environment vars
- `clear`: clear out terminal

#### List files and directories
- `ls`: list files and directories
- `ls -l`: an option to get details (permissions, etc) of files and directories
- `ls -l Desktop/`: use directory name argument to list 'Desktop''s files and directories
- `ls -d Desktop/`: display name only about the directory itself not its contents
- `ls -ld Desktop/`: display information only about the directory itself 
- `ls -al Desktop/`: list details of all files and directories
`.XX` are hidden files

#### Change directories
- `cd`: change path to HOME
- `cd Desktop/`: change path to a directory
- `cd $HOME`: go back to the home directory
- `cd .`: stay in the same directory. one dot means the current directory
- `cd ..`: go back one layer up. two dots means one directory back from the current location 

#### Make and Remove Files and Directories
- `mkdir tmp`: make a directory 'tmp'
- `chmod 700 tmp`: change permissions of tmp to grant rwx access only to user
-- roles: [user, group, world]
-- permission for each role: 'rwx' as read/write/execute 
-- permission code single: 
111 (binary) == 7 (decimal) == 'rwx'
000 (binary) == 0 (decimal) == '---'
101 (binary) == 5 (decimal) == 'r-x'
-- permission codes combo: 
700 == 7 (decimal) for user + 0 (decimal) for group + 0 (decimal) for world == 'rwx------'
755 == 7 (decimal) for user + 5 (decimal) for group + 5 (decimal) for world == 'rwxr-xr-x'
- `touch test`: create an empty directory 'test'
- `cp A B`: copy a directory A to B
- `cp ../Desktop/Vocabulary_list.csv .`: copy the file 'Vocabulary_list.csv' from aunt directory 'Desktop' to the current location
- `rm test`: remove a directory 'test'
- `rm tmp/*`: remove all the contents from directory 'tmp'
- `rmdir tmp`: remove directory when 'tmp' is already empty
- `rm -rf R`: remove recursively and force it

#### Search for Files and Search for patterns
- `grep PATTEN file`: return lines containing 'PATTEN' from 'file'
- `grep the Vocabulary_list.csv`: find lines with 'the' from 'Vocabulary_list.csv'
- `grep -V the Vocabulary_list.csv`: list all the words without the pattern 'the' from 'Vocabulary_list.csv'
- `grep -r boisterous *`: search recursively for 'boisterous' in any directories
- `grep 'Manager|Developer' employee.txt | grep -v Sales`: find 'Manager' and 'Developer' and exclude 'Sales' 
https://www.thegeekstuff.com/2011/10/grep-or-and-not-operators/#:~:text=Using%20grep%20%2Dv%20you%20can,lines%20except%20the%20given%20pattern.&text=For%20example%2C%20display%20all%20the,contains%20the%20keyword%20%E2%80%9CSales%E2%80%9D.
- `find . -name Vocabulary_list.csv`: find file with name 'Vocabulary_list.csv' from current directory
- `find / -name cat`: '/' means root
`find / -name cat 2>/dev/null`: redirect all the error msg to '/dev/null'
- `cat`: create single/multiple files, view contents, concatenate files, and redirect outputs to terminal or files





















