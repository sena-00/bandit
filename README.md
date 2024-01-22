# Bandit - Over The Wire
>[!WARNING]
>This is a tutorial for the CTF Bandit, by OverTheWire. If you have not yet completed yourself, go try it out.
>This file contains spoilers and solutions for the game

## What is Bandit?
<div id='id-section1'/>

Bandit is a CTF game aimed for complete beginners in the hacking scenario. The purpose of the game is to teach you the basics of CLI(command line interface) hacking aswell as other important concepts of cybersecurity.
The game gets progressively harder and it is composed of 33 Levels at the moment of this writing.

Check for more info in the official website: https://overthewire.org and https://overthewire.org/wargames/bandit/

## Bandit 0
<div id='id-section2'/>

The username for this level is **Bandit0** and the password is **Bandit0**.
After logging in the server, type 'ls' to list the directory. After that, you can use the command 'cat' to read the file.

![image](https://github.com/sena-00/bandit/assets/156020094/c355c4d3-be48-45a9-b339-75338a64f9f7)
## Bandit 1
<div id='id-section3'/>
  
Log in to the server with **bandit1** username and the specified password.
Using `ls` to list the directory a "-" is shown. To open this file, use `cat ./-` 

![image](https://github.com/sena-00/bandit/assets/156020094/e903c0cc-fe62-4971-9d82-22c4f64e99e0)

## Bandit 2
<div id='id-section4'/>

After logging in into the server with the username and password, list the directory using `ls`. A file named "spaces in this filename" will be shown.
To open files with spaces in bash, you need to use "\" for each space. In this case: `cat spaces\ in\ this\ filename`.

![image](https://github.com/sena-00/bandit/assets/156020094/ef84543a-932b-4d55-b0f5-7d0fd7614a4d)

## Bandit 3
<div id='id-section5'/>

Log in with the **bandit3** username and password. Use `ls` to list the directories. a folder "inhere"(listed in blue) will be shown. If you try listing again with `ls` nothing is shown.
This is because the file is named ".hidden", and will be automatically ignored when using `ls`. Instead try `ls -a` to list all files and `cat .hidden` to show the password.

![image](https://github.com/sena-00/bandit/assets/156020094/26532bc1-0099-4b17-9a03-4a531f3c6438)

## Bandit 4
<div id='id-section6'/>

Log in with the **bandit4** username and password and follow the same previous steps. Use `cd inhere` to enter the folder. List the directory using `ls -a`. We can see that there are numerous files inside and we are looking for the only human readable file, this is, a text file. To this effeciently, use the command `file` + `./*`. This will show all the files in the directory aswell as the type.

![image](https://github.com/sena-00/bandit/assets/156020094/dfa0c8c7-9f2e-4ebe-815a-74d010c540ac)

## Bandit 5
<div id='id-section7'/>
  
After logged in, enter the "inhere" folder and list the directory. The file we are looking for is: 
- human-readable
- 1033 bytes in size
- not executable
You defenitely can and should search the file with all the details provided. However, using `find -size 1033c` does the trick. "Find" is used for navigating files. 1033 is the size and "c" for bytes.

![image](https://github.com/sena-00/bandit/assets/156020094/4ce20226-78ac-44b0-b8b9-70684a99b140)

## Bandit 6
<div id='id-section8'/>

Log in with the username and password for **bandit6**. In this level we are looking for a specific file:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

There are many approaches to solve this. In this example, you can use the `find` command + `-type f -user bandit7 -group bandit6 -size 33c 2>/dev/null`. This will show **files* that are: 1. Owned by user "bandit7", 2. Owned by group "bandit7", 3. Of 33 bytes in size and 4. append all the "permission denied" messages

![image](https://github.com/sena-00/bandit/assets/156020094/1230dc04-246f-45ee-8927-b1fb931a4871)

## Bandit 7
<div id='id-section9'/>

First, use the `ls` command to list the files. We can see a "data.txt" file and we are searching for the text next to the word "millionth". You can use grep to complete this task with `grep millionth data.txt`, or you could simply open the data.txt with Vim and `Ctrl + F` the word millionth.

![image](https://github.com/sena-00/bandit/assets/156020094/fa61988b-5d30-4920-af3a-19a66c4f5e9d)














