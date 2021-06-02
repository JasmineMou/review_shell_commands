#### Resources
- [x] coursera ["Command Line in Linux"](https://www.coursera.org/learn/command-line-linux/supplement/MhGNK/project-based-course-overview)
- [x] [interviewbit](https://www.interviewbit.com/courses/shell/)
- [x] [leetcode](https://leetcode.com/problemset/shell/)

- [ ] [hackerrank](https://www.hackerrank.com/domains/shell)



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


### InterviewBit
1. `cut`: select sections of text from each line of files.

Get columns 1 to 5
```
cat data.csv | cut -c 1-5
```

Set delimiter and get 1st field
```
cat data.csv | cut -d "," -f 1
```


2. `grep`

Match all words starting with 'Ind'
```
cat /usr/share/dict/words | grep "Ind.*"
```

Match all words ending with 'age'
```
cat /usr/share/dict/words | grep ".*age$"
```

Match all pattern which starts with q and doesn’t follow by u
```
cat /usr/share/dict/words | grep "q." | grep -v "qu"
```

Get information about all ethernet interfaces using `-A` (after) flag
```
ifconfig | grep "en[0-9]" -A 4
```

Recursively search for a keyword and also get filename using `-H` (filename), `-R` (recursive), `-i` (case-insensitive) flag 
```
grep -HRi "json" *
```

https://man7.org/linux/man-pages/man1/grep.1.html


3. piping
A pipe is a form of redirection that is used in Linux and other Unix-like operating systems to send the output of one program to another program for further processing.

Print unique second digits from 1 ~ 30
```
for i in {1..30}; do echo $i; done | cut -c 2 | sort | uniq
```

- Print 1 to 30
```
for i in {1..30}; do echo $i; done 
```
- print the second digits of the given inputs
```
cut -c 2 
```
https://www.geeksforgeeks.org/cut-command-linux-examples/
- sort the given input
```
sort 
```
- filter only unique digits
```
uniq
```


4. `sort`, `uniq`

Sorting by the second field ( Flag -k used to select a field for sorting)
```
cat words.txt | sort -k 2
```

Filter out repeated lines in a file
```
cat nums.txt | uniq
```

Select unique lines along with their count using -c (count) flag {count, line}
```
cat nums.txt | uniq -c
```


5. `head`, `tail`, `tr`

`head` and `tail` are used to print n top or bottom lines respectively.

Get lines from 345 o 360
```
cat /usr/share/dict/words | head -360 | tail -15
```

`tr` Replacing or removing specific characters from the input.

Reverse the case
```
cat data.csv | tr '[a-z][A-Z]' '[A-Z][a-z]'
```

Replace each digit with x
```
cat data.csv | tr '[0-9]' 'x'
```

Remove consecutive duplicate alphanumerics using -s (squash) flag
```
cat data.csv | tr -s '[0-9A-Za-z]'
```

Remove all digits using -d (delete) flag
```
cat data.csv | tr -d '[0-9]'
```


6. conditional statements

If-else statement
```
num=5
if [ $num -lt 0 ]; then
	echo "number is negative";
elif [ $num -lt 10]; then
	echo "number is less than 10";
else
	echo "number is equal or greater than 10";
fi
```


7. loops

for loop
```
for i in {5..10};
do 
	echo $i;
done
```

while loop
```
i=1
while [ $i -le 20]
do 
	echo "$i"
	i=$(($i+1))
done
```


8. regex

The main uses for Regular Expressions (REs) are text searches and string manipulation. An RE matches a single character or a set of characters -- a string or a part of a string.

regex metacharacters
- `.`: match any signle character except the new line character (\n)
- `*`: match 0+ occurence of the immediate preceding character
- `<`: match the beginning of a word
- `>`: match the ending of a word
- `^`: match the beginning of a line
- `$`: match the ending of a line
- `{m}`: match the exact regex 'm'
- `{m,}`: match 1+ regx 'm'
- `{m,n}`: match the preceding regex 'm' to 'n' times

regex metaclasses
- `[:alnum:]` or `[a-zA-Z0-9]`: alphanumeric characters
- `[:digit:]` or `[0-9]`: digits
- `[:punct:]`: punctuations 

regex to match all words ending with 'ing'
```
<.*ing\>
```

regex to match all words containing 'quu' or 'quuu' and such
```
qu{2,}
```

match all lines starting with non-vowel and end with a vowel using grep
```
cat lite.txt | grep "^[^aeiou].*[aeiou]$"
```


9. `sed`, `awk`

`sed` is a powerful text stream editor which can do insertion, deletion, search, and replace


Replace consecutive multiple 'a' with a single 'a'
https://www.cyberciti.biz/faq/how-to-use-sed-to-find-and-replace-text-in-files-in-linux-unix-shell/
```
sed 's/a\{2,\}/a/g' cats.txt
```
or 
```
cat interviewbit/cats.txt | tr -s 'a'
```

Display but delete lines 1 through 2:
https://stackoverflow.com/q/25678863/2687773
```
sed '1,2d' filename
```

`awk` searches files for text containing a pattern and performs a specific action on that line/text
https://opensource.com/article/20/9/awk-ebook


Calculate total number of the students
```
awk -F, 'BEGIN {printf "name \t sub1 \t sub2 \t total\n"} {printf "%s \t %s \t %s \t %s\n", $1, $2, $3, $2+$3}' marks.txt
```

Syntax for tr. option and stringValue2 are optional for tr command. You can use -c, -s and -d option with tr command to do different types of tasks.
https://linuxhint.com/bash_tr_command/
```
tr [option] stringValue1 [stringValue2]
```


10. functions

Define a bash function
```
greet() {
	echo Hello $1
}
```
to execute 
```
> greet WORLD!
```
output
```
hello WORLD!
```

#### Quiz

1. Valid phone numbers
Given a text file 'valid_numbers.txt' containing list of phone numbers (one per line), write bash script to print all valid numbers, which are in one of these formats:
- (xxx)xxx-xxxx
- xxx-xxx-xxxx
You may also assume each line in the text file must not contain leading or trailing white spaces.


Solution

'input' saved as 'valid_numbers.txt'

```
cat input | grep '^[0-9]\{3\}\-[0-9]\{3\}\-[0-9]\{4\}$\|^([0-9]\{3\}) [0-9]\{3\}\-[0-9]\{4\}$'
``` 

Parsing
- to match (xxx)-xxx-xxxx
```
cat input | grep '^([0-9]\{3\}) [0-9]\{3\}\-[0-9]\{4\}$'
```

- to match xxx-xxx-xxxx
```
cat input | grep '^[0-9]\{3\}\-[0-9]\{3\}\-[0-9]\{4\}$'
```

- to match both pattern A and pattern B
```
grep 'A\|B'
```


2. Lines in a given range

Solution

'input' saved as 'lines_in_a_given_range.txt'.

```
read -r firstline<input
L=$(echo $firstline | cut -d ' ' -f 1)
R=$(echo $firstline | cut -d ' ' -f 2)
head -n $R input | tail -n -$(($R-$L+1))
```


3. Remove punctuations

Solution

'input' saved as 'remove_puncs.txt'

```
cat input | tr -d [:punct:]
```


4. Transform CSV

Solution

'input' saved as 'transform.csv'

```
awk -F, '{printf "%s,%s,%s,%s,%s,+%s-%s\n", $1, $2, $3, $4, $6, $5, $7}' input
```


5. Swap forward and backward slash

Solution

'input' saved as 'swap_slash.txt'

note: use `\` in front of a symbol

```
sed 's+\/+\#+g; s+\\+\/+g; s+\#+\\+g' input
```
or 
```
cat input | tr '/\\' '\\/'
```


6. ? Sort by frequency ?


Solution

'input' saved as 'sort_freq.txt'


```
cat input | tr -s ' ' '\n' | sort | uniq -c | sort | awk -F' ' '$1==last {printf " %s",$2; next} NR>1 {print "";} {last=$1; printf "%s",$0;} END{print "";}' | sed "s/^[ \t]*//"
```


7. ? Valid email address ?

Solution

'input' saved as 'valid_emails.txt'


```
cat input 
| grep -xv "^[A-Za-z][-_\.\+A-Za-z0-9]*[@][-A-Za-z0-9]*[\.][A-Za-z]*" 
| grep -xv "^[A-Za-z][-_\.\+A-Za-z0-9]*[@][-A-Za-z0-9]*[\.][A-Za-z]*[\.][A-Za-z]*"
```


8. Convert integer to roman number

Solution

'input' saved as 'int2roman.txt'

```
A=(Z I II III IV V VI VII VIII IX)
B=(Z X XX XXX XL L LX LXX LXXX XC)
C=(Z C CC CCC CD D DC DCC DCCC CM)
D=(Z M MM MMM MMMM MMMMM MMMMMM MMMMMMM MMMMMMMM MMMMMMMMM)

while read num
do
  	if [ $num -ge 1000 ]
  	then
  	    th=`expr $num / 1000`
  	    echo -n "${D[$th]}"
  	fi
  	
  	num=`expr $num % 1000`
  	
  	if [ $num -ge 100 ]
  	then
  	    h=`expr $num / 100`
  	    echo -n "${C[$h]}"
  	fi

  	num=`expr $num % 100`

  	if [ $num -ge 10 ]
  	then
  		t=`expr $num / 10`
  		echo -n "${B[$t]}"
  	fi

  	num=`expr $num % 10`
  	if [ $num -ge 1 ]
  	then
  		echo -n "${A[$num]}"
  	fi
  	echo
done < input
```



### Leetcode Bash

192. Word Frequency
https://leetcode.com/problems/word-frequency/submissions/

Solution
```
cat words.txt | tr ' '  '\n' | sort | sed '/^$/d' | uniq -c | sort -r | awk -F ' ' '{printf "%s %s\n", $2, $1}' 
```

To remove empty line
``` 
sed '/^$/d'
```


193. Valid Phone Numbers
https://leetcode.com/problems/valid-phone-numbers/

Solution
```
grep '^[0-9]\{3\}\-[0-9]\{3\}\-[0-9]\{4\}$\|^([0-9]\{3\}) [0-9]\{3\}\-[0-9]\{4\}$' file.txt
```


194. Transpose File
https://leetcode.com/problems/transpose-file/

Solution
```
awk '{
for (i=1; i<=NF; ++i) {
    if (NR==1) s[i]=$i;
    else s[i] = s[i] " " $i;
}}
END {
for (i=1; i<=NF; ++i) {
    print s[i];
}} ' file.txt
```


195. Tenth Line
https://leetcode.com/problems/tenth-line
- `NR`: number of records
- `NF`: number of fields

Solution
```
awk 'NR==10' file.txt
```



### Hackerrank








