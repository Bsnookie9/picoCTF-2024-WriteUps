# Overview
- Tags: `picoCTF 2024` `General Skills` `shell` `browser_webshell_solvable` `ls`
- `100 points`

# Description
Want to play a game? As you use more of the shell, you might be interested in how they work!

Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.  

Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics.   
Practicing the fundamentals manually might help you in the future when you have to write your own tools!  

You can download the challenge files here:
* [challenge.zip](https://artifacts.picoctf.net/c_atlas/17/challenge.zip)

# Hints
* Have you ever played hot or cold? Binary search is a bit like that.
* You have a very limited number of guesses. Try larger jumps between numbers!
* The program will randomly choose a new number each time you connect. You can always try again, but you should start your binary search over from the beginning - try around 500. Can you think of why?

# Solution
Let's start by downloading the zip file using `wget`, then we will unzip the file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/581b792a-3c8b-4708-91f0-ca7dcc0ea589)</kbd>

Now we'll do a quick `ls` to view new files/directories.Theres' new directories home, ctf-player, and drop-in and then the guessing game.sh file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/5cd5b461-d95f-4a4f-8bc1-1c2b41fbf708)</kbd>

Let's use an editor to view the file, such as vim

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/2d451274-3adb-446a-a5d5-eb938c2e8da8)</kbd>

We can see that it chooses a random number between 1 and 1000 and the user only gets 10 guess before failing.

> [!WARNING]
> 10 incorrect guesses causes the server to close and choose a new number when you reconnect. CHOOSE WISELY!

Let's enter the ssh command to connect to the server

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/0c266e7f-2633-4320-9756-d3a6e8bf7f43)</kbd>

Let's start guessing! Start with 500 since it's halfway and you can then the program will say higher or lower.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/ed4096f0-bbfb-4279-8d58-26f8307711b4)</kbd>

Ok, so the number is lower than 500. Let's go halfway between 500 and 1...250?

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/beea2f96-a8d9-4747-9e8f-efc5e4d48f7f)</kbd>

Lower than 250 too! I just kept doing the same thing of guessing halfway between the the number range of the high and low number until I got the flag on the last try!

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/79445365-ea41-49f5-b486-27155ff78438)</kbd>

Flag: `picoCTF{g00d_gu355_6dcfb67c}`
