  # Bandit - Over The Wire
>[!WARNING]
>This is a tutorial for the CTF Bandit, by OverTheWire. If you have not yet completed yourself, go try it out.
>This file contains spoilers and solutions for the game

## What is Bandit?
<div id='id-section1'/>

Bandit is a CTF game aimed for complete beginners in the hacking scenario. The purpose of the game is to teach you the basics of CLI(command line interface) hacking aswell as other important concepts of cybersecurity.
The game gets progressively harder and it is composed of 33 Levels at the time of this writing.

Check for more info in the official website: https://overthewire.org and https://overthewire.org/wargames/bandit/

## Bandit 0
<div id='id-section2'/> 

The username for this level is **Bandit0** and the password is **Bandit0**.
After logging in the server, type `ls` to list the directory. After that, you can use the command `cat` to read the file.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/c355c4d3-be48-45a9-b339-75338a64f9f7" width="600" height="500">
</p>  

## Bandit 1
<div id='id-section3'/>
  
Log in to the server with **bandit1** username and the specified password.
Using `ls` to list the directory a "-" is shown. To open this file, use `cat ./-` 

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/e903c0cc-fe62-4971-9d82-22c4f64e99e0" width="600" height="500">
</p>  
  
## Bandit 2
<div id='id-section4'/>

After logging in into the server with the username and password, list the directory using `ls`. A file named "spaces in this filename" will be shown.
To open files with spaces in bash, you need to use "\" for each space. In this case: `cat spaces\ in\ this\ filename`.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/ef84543a-932b-4d55-b0f5-7d0fd7614a4d" width="600" height="500">
</p>

## Bandit 3
<div id='id-section5'/> 

Log in with the **bandit3** username and password. Use `ls` to list the directories. a folder "inhere"(listed in blue) will be shown. If you try listing again with `ls` nothing is shown.
This is because the file is named ".hidden", and will be automatically ignored when using `ls`. Instead try `ls -a` to list all files and `cat .hidden` to show the password.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/26532bc1-0099-4b17-9a03-4a531f3c6438" width="600" height="500">
</p>

## Bandit 4
<div id='id-section6'/>

Log in with the **bandit4** username and password and follow the same previous steps. Use `cd inhere` to enter the folder. List the directory using `ls -a`. We can see that there are numerous files inside and we are looking for the only human readable file, this is, a text file. To this effeciently, use the command `file` + `./*`. This will show all the files in the directory aswell as the type.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/dfa0c8c7-9f2e-4ebe-815a-74d010c540ac" width="600" height="500">
</p>

## Bandit 5
<div id='id-section7'/>
  
After logged in, enter the "inhere" folder and list the directory. The file we are looking for is: 
- human-readable
- 1033 bytes in size
- not executable
You defenitely can and should search the file with all the details provided. However, using `find -size 1033c` does the trick. "Find" is used for navigating files. 1033 is the size and "c" for bytes.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/4ce20226-78ac-44b0-b8b9-70684a99b140" width="600" height="500">
</p>

## Bandit 6
<div id='id-section8'/>

Log in with the username and password for **bandit6**. In this level we are looking for a specific file:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

There are many approaches to solve this. In this example, you can use the `find` command + `-type f -user bandit7 -group bandit6 -size 33c 2>/dev/null`. This will show **files* that are: 1. Owned by user "bandit7", 2. Owned by group "bandit7", 3. Of 33 bytes in size and 4. append all the "permission denied" messages

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/1230dc04-246f-45ee-8927-b1fb931a4871" width="600" height="500">
</p>

## Bandit 7
<div id='id-section9'/>

First, use the `ls` command to list the files. We can see a "data.txt" file and we are searching for the text next to the word "millionth". You can use grep to complete this task with `grep millionth data.txt`, or you could simply open the data.txt with Vim and `Ctrl + F` the word millionth.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/fa61988b-5d30-4920-af3a-19a66c4f5e9d" width="600" height100">
</p>

## Bandit 8
<div id='id-section10'/>

When entering this level, you are searching for a string that occurs only once in the data.txt file. To solve this, you can use `uniq` to filter based on identical lines. You can also use `-u` flag to only show lines that appear once in the file. With a simple sort, you get the password for the next level. `sort data.txt | uniq -u`

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/354136bb-1c0f-4576-9026-705757506cb9" width="600" height="500">
</p>

## Bandit 9
<div id='id-section11'/>

Now, you are looking for a password, which is located in the "data.txt" file. It is human-readable and preceded by several "=". There are many ways to solve this, one i find incredibly easy however might not work everytime:
- You are looking several "=" (This means more than two but not many)
- It is human readable
- You already know that passwords commonly have about 30 characters

Armed with that information, you cant use `grep "==="` and look for 3 equal symbols (since we dont know the actual number of symbols) + `data.txt --text`, pointing to the file and requesting text only.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/3af14223-77e9-4de9-a9cc-b1a2708e56f2" width="600" height="500">
</p>

## Bandit 10
<div id='id-section12'/>

You are greeted with a data.txt file that is encoded in base64. To solve this you can simply decode it with `base64 -d data.txt`.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/087b7672-b018-4684-82f1-94c706c150bc" width="600" height="350">
</p>

## Bandit 11
<div id='id-section13'/>

In this level you are looking at a Rot13 translation for the data.txt file. To get the information you need, you can use `cat data.txt` concatenated with `tr '[a-z][A-Z]' '[n-za-m][N-ZA-M]'`. The last part of the code swaps 13 positions in the alphabet.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/fe27ee23-a3b5-4843-b6eb-58a532b815ff" width="600" height="150">
</p>

## Bandit 12
<div id='id-section13'/>

In this level, you are looking for a password in a hexdump file that has been repeatedly compressed. In this level we will use many commands to decompress the file provided. First, we must create a folder where the decompression will take place. You can create you folder on /tmp/YourFolderNameHere. 
- Lets begin by creating the folder: `mkdir /tmp/homer`.
- Now copy the "data.txt" file to your folder: `cp data.txt /tmp/homer`.
- At last, change you directory to the folder you have just created: `cd /tmp/homer`

Now, if you take a look inside the file you just copied its not readable since it is a hexdump. To reverse this process use `xxd -r data.txt newdata`. Checking out the newly generated file by `file newdata`, you can see that "newdata" is now a gzip file. Rename the file to "newdata.gz" and use gzip to decompress with `gzip -d newdata.gz`.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/2a35950e-e28f-4945-be26-a46397584b4f" width="600" height="200">
</p>
  
Now when using the command `file newdata`, you are looking at a bzip file. To decompress it, first rename the file with bz2 extension `mv newdata newdata.bz2`, then `bzip2 -d newdata.bz2`

This whole process will repeat until we have a final, readable file with the password. Using `file` we can see that we have a *tar*.
- Rename the file `mv newdata newdata.tar`
- Decompress the file `tar -xf newdata.tar`
- A new file has appeared: data5.bin. Run `file data5.bin`. A POSIX tar archive is shown. Rename it with `mv data5.bin data5.tar`. Now use  `tar -xf data5.tar`.
- A new file has appeared: data6.bin. Run `file data6.bin`. A bzip2 file is shown. Rename it with `mv data6.bin data6.bz2`. Now use `bzip2 -d data6.bz2`.
- The old data6 is now a .tar file. Run `mv data6 data6.tar` and then `tar -xf data6.tar`.
- A new file has appeared: data8.bin. Run `file data8.bin`. A gzip file is shown. Rename it with `mv data8.bin data8.gz`. Now use `gzip -d data8.gz`.
- Finally you have the final data8 file which is ASCII Text. Run `cat data8` and there is your password.

## Bandit 13
<div id='id-section14'/>

The password for this level is located in `/etc/bandit_pass/bandit14` and can only be read by user **bandit14**. You will not have a ASCII text password however, but rather a SSH key.
Lets use the SSH key to login to the server. First, use the command `ssh bandit14@localhost -i sshkey.private -p 2220` (This must be done inside user bandit13). Type **yes** for the connection request and then `cat /etc/bandit_pass/bandit14`

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/f3a50c53-1297-47c4-8727-4e4346b9e178" width="600" height="200">
</p>

## Bandit 14
<div id='id-section15'/>

To resolve bandit14, you must submit the password of the current level, to localhost on port 30000. 
- To do this, use the command echo with the password: `echo fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq`.
- Now use nc localhost 30000.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/b36a79b1-2c9e-4ecf-8d3d-2f419efa2568" width="600" height="150">
</p>

## Bandit 15
<div id='id-section16'/>

The password for this level is obtained by submitting the password of the current level to port 30001 on localhost using SSL encryption. To solve this, first copy the password for the current level to the clipboard. After entering the level, use the command `openssl s_client -connect localhost:30001`. When the connection is stablished, you should see "read R BLOCK". Just paste the password with `Ctrl + Shift + V` and hit enter.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/e7c42035-3e30-4ed4-9ea0-655d055bea47" width="600" height="500">

## Bandit 16
<div id='id-section17'/>

In this level, we are looking for open ports that speak SSL. First, lets begin by using `nmap localhost -p 31000-32000` to list open ports on local host.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/7c711d04-7511-4294-bcb5-db1ab8cadb39" width="600" height="250">
</p>

We can see that there are 05 open ports. If you are in the correct port, replying with the password of the current level should return a RSA Key to the next level. If you are at the wrong port, either no option to reply will appear, or the port will simply give back the password you sent.
1. Trying to connect to 31046 with `openssl s_client -connect localhost:31046` does not allow for replies.
2. Trying to connect to 31518 with `openssl s_client -connect localhost:31518` will send back the password you replied.
3. Trying to connect to 31691 with `openssl s_client -connect localhost:31691` does not allow for replies.
4. Trying to connect to 31790 with `openssl s_client -connect localhost:31790` accepts the password and returns the RSA Key.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/59e01e84-7f9b-4521-8ed3-9b70f0940337" width="400" height="600">
</p>

Copy the text starting in `---BEGIN RSA PRIVATE KEY---` til the end `---END RSA PRIVATE KEY---` (If you copy only the middle part this will not work). Now we are going to paste the RSA Key in a file. To create this file we must navigate to /tmp/ and we must create a directory. Use `cd /tmp`. Inside /tmp, create a directory and inside it create a file with *.key* extension. In my case i created *bandit17pass.key*. Now paste the RSA key into the file using `nano bandit17pass.key`

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/18c78d5c-ed4d-4b34-bd05-3a302dbc941c" width="600" height="120">
</p>

After pasting the RSA Key into the file and saving it, change the permissions of the file with `chmod 400 bandit17pass.key` and log in with `ssh -i bandit17pass.key bandit17@bandit.labs.overthewire.org -p 2220`.

## Bandit 17
<div id='id-section18'/>

When entering this level, we are presented with two files: *passwords.old* and *passwords.new*. To see the difference between both files you can use `diff passwords.new passwords.old`. Or the way i use it: `diff -y -W 70 passwords.new passwords.old`

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/eca96f68-25b7-45a2-9d09-e26c4007ce88" width="650" height="500">>
</p>

As shown above, the password for the next level is `hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`

## Bandit 18
<div id='id-section18'/>

If you try to login like you would normally, a bye-bye message is shown and the connection is dropped. The thing is, when using SSH, you can also execute commands such as `ls` or `cat`. 
1. Lets try to login via ssh and list the directories available with ` ssh -t bandit18@bandit.labs.overthewire.org -p 2220 ls`.
2. Now opening the file with cat ` ssh -t bandit18@bandit.labs.overthewire.org -p 2220 cat readme` we can retrieve the password

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/e7e0bf1d-0e20-407a-9794-713389ed28c5" width="650" height="500">
</p>

## Bandit 19
<div id='id-section18'/>

In the home directory there is a *bandit20-do* file. When reading the permissions for this file with `ls -la` we can see that it is possible to execute commands as bandit20, even though you are logged as bandit19.  
To do this you can simply execute this file before that action you want to perform as bandit20. For example, if i tried to open the password located in `/etc/bandit_pass/bandit20`, i would receive a *Permission Denied* message.  
However if i try to run `cat /etc/bandit_pass/bandit20` executing the file before hand, technically you are trying to access the password as bandit20, thus allowing the password to be shown: `/bandit20-do cat /etc/bandit_pass/bandit20`

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/8dada258-a3e8-4a53-bbb2-4b2aea8e47b3" width="700" height="250">
</p>


## Bandit 20
<div id='id-section18'/>

The goal for this level is to create a network daemon with netcat, that will receive the current level password(bandit20), and reply with the next level password(bandit21), and to accomplish this we must use the *suconnect* file in the home directory.
We can start with `echo -n 'VxCazJaVykI6W36BkBU0mJTCM8rR95XT'`. This will input to the nc server the password for the current level. Then we can use `nc -l -p 7455 &`. (-l for listening / -p for port / & for background running).  

All that is left to do, is connecting with suconnect file to the port we have created (you can create your own port number).

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/cf67720f-184b-42ca-9fe5-5da37e304eb1" width="700" height="200">
</p>

## Bandit 21
<div id='id-section18'/>

There is a program that is running regurlary with cron, located in `/etc/cron.d/`. If we find out that the program is running, we may be able to get a hold of the next's level password. Lets navigate to the folder with `cd /etc/cron.d/`. There is a bandit22 file. Reading the file with `cat cronjob_bandit22`, we can tell that there is a shell script running 24/7.  
Lets read what is inside this shell script with `cat /usr/bin/cronjob_bandit22.sh`. This script is giving the user RWX permissions for a file located in `/tmp` named *t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv*.
If we cat the file above, we have access to bandit22's password.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/163f675c-5199-442e-9117-5a2295407f7f" width="700" height="300">
</p>

## Bandit 22
<div id='id-section18'/>

This level starts the same as the previous. Lets navigate to the script and see whats going on in the background with `cat /usr/bin/cronjob_bandit22.sh`. According to the script: 
1. Grabs the username from the command `echo I am user $myname`
2. Send to md5sum and hashes the string with the password
3. Outputs the password inside the file located in /tmp/

If we run the shell script as intented for the bandit23 user, the password is outputed in the file.
`echo I am user bandit23 | md5sum | cut -d ' ' -f 1`


<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/7bfa1128-e75b-43a0-8b5c-02830026ec6c" width="650" height="430">
</p>

## Bandit 23
<div id='id-section18'/>

Again, this level starts just as the previous one. Lets take a look in the script folder and see whats going on.

~~~
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
~~~
The script that is been run via cron executes everything in the folder `/var/spool/$myname/foo` and then deletes it. The *if* statement checks if the script is being run by bandit23.  
All we have to do, is to create a script to fetch us the password, since any script running in the folder `var/spool/$myname/foo` will be executed.
Lets begin by creating a folder in /tmp/ and creating our script to fetch the password.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/1e19135f-f86c-4285-9f72-4a530ac2ad03" width="600" height="500">
</p>


## Bandit 24
<div id='id-section18'/>

In this level we are looking for a 4 digits PIN code. To go through all the combinations, we are going to use Brute Force.
We'll have to create a script for this. Lets begin by creating a folder in /tmp/: `mkdir /tmp/testing123 && cd /tmp/testing123`.  
Now, lets create a script `nano bruteforce.sh`. Inside the script lets add:
~~~~
#!/bin/bash 
for i in {0000..9999}
do 
        echo "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i"
        sleep 0.02
done
~~~~
It is crucial to add `sleep 0.02`. If you dont do that, you'll overflow netcat, and after a few tries, nc will either timeout, or stop working.
Lets change the permissions with `chmod 777 bruteforce.sh`.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/321a0239-3b87-469e-a14c-99e15ba55f3f" width="600" height="500">
</p>

Run the script with `./bruteforce.sh | nc localhost 30002`. The last line should show the correct password for the next level.

<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/8a4f5d64-df4e-48c2-bc04-50ff27756e8f" width="600" height="500">
</p>

## Bandit 25
<div id='id-section18'/>

After logged into the server, `ls` will show a *bandit26.sshkey*. Lets try using it as we did in [Bandit13](https://overthewire.org/wargames/bandit/bandit13.html). Use the command `ssh bandit26@localhost -i bandit26.sshkey`.  

Trying to connect however will disconnect you from the local host, too bad.
The challenge states that the shell being used by bandit26 is not shell. To find out which one is being used, run `cat /etc/passwd | grep bandit26`

~~~
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$
~~~
<p align="center">
<img src="https://github.com/sena-00/bandit/assets/156020094/05f1d4b1-a33a-4e10-99a6-3f10aa887ef8 width="600" height="500">
</p>


This tells us that instead of /bin/bash, a "/bin/showtext" is being used. Find out whats going on with `cat /usr/bin/showtext`.
~~~
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/shexport TERM=linuxmore ~/text.txt
exit 0
bandit25@bandit:~$
~~~

## Bandit 26
<div id='id-section18'/>







