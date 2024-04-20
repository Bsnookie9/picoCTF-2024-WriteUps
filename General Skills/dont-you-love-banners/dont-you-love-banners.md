# Overview
- Tags: `picoCTF 2024` `General Skills` `shell` `browser_webshell_solvable`
- `300 points`

# Description
Can you abuse the banner?

The server has been leaking some crucial information on `tethys.picoctf.net 53279`. 

Use the leaked information to get to the server. 

To connect to the running application use `nc tethys.picoctf.net 53701`.   

From the above information abuse the machine and find the flag in the /root directory.

# Hints
* Do you know about symlinks?
* Maybe some small password cracking or guessing

# Solution
Lets start by using netcat with the first server and port number given: `nc tethys.picoctf.net 53279`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/5e322181-84c2-4942-8999-92f12ee96622)</kbd>

The description mentions that this server was leaking information and as we can see, there is a potential password in plaintext.  
Let's now use the second server and netcat to it: `nc tethys.picoctf.net 53701`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/ec70d658-26ca-43a8-9e01-2bcfd127d918)</kbd>

We are presented with a prompt to enter the password, so let's enter that password we saw before...

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/d0ec5b90-0f13-4133-a8b8-6f0463a0dd67)</kbd>

That worked! Now we have to answer the next question. After researching and knowing off the top of my head, I knew it was DEF CON!

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/25f6fe30-db34-47ed-85f2-7df980980144)</kbd>

Again, correct! It wants the name of the first hacker of phreaking. After researching, I found John Draper...

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/6fb1cdfc-8ca5-4244-964b-9292c3a7cbdd)</kbd>

We are now logged in as player@challenge! I did a quick `ls` to see what files existed and saw two files. I then used `cat` on both of the files

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/47f3150a-4583-4f86-b66c-c3f31d669bb0)</kbd>

We know need to see what hidden files might exist by using the `-la` flag with shows a long list of all files

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/1b3d326a-8cb5-4da1-8d47-3d88ccf5223a)</kbd>

Nothing popping out here so let's dig deeper by looking in the root directory

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/271a89ac-e5f6-4dd5-9bab-3b6be3a49e99)</kbd>

Ok we are getting somewhere! We can see there is a flag.txt file and a script.py file. Unfortunately we don't have access to read the flag file.  
Let's try looking at the script file and see what we can find.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/34fcd1c1-ba5b-4201-bf25-afdbe94cd778)</kbd>

We can see this is what we interacted with when we first netcat into the server, with all the questions and accepted answers.  
There is an important part to this script in the beginning...

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/575a2717-c831-4560-9086-9397f97397b0)</kbd>

The hints for the challenge mentions symlinks. Symlinks are essentially reference pointers for files and directories. Think of the symlinks   
as a shortcut to the file...for example...link1 -> /root/flag.txt. We need to create a symlink between a file and the flag.txt file in the root directory.

Let's use that important piece in the beginning of the script where when we first connect to the server, it opens the banner.  
We can create a symlink between the banner and the /root/flag.txt. First we need to remove the banner, `rm banner`.   
Use this command after: `ln -s /root/flag.txt banner`. This now tells the script to point to the banner which then points to the flag.txt file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/d16b3271-5d3b-4607-9a41-4221e32e4209)</kbd>

Now type `CTRL+C` to exit the server. Reconnect to the server using the previous netcat command.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/76cf9c5b-502e-4938-83b5-44758a4dc53a)</kbd>

There is your flag!

Flag: `picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_ed6f9c71}`
