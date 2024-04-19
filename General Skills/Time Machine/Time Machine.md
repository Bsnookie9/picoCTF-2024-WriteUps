# Overview
- Tags: `picoCTF 2024` `General Skills` `browser_webshell_solvable` `git`
- `50 points`

# Description
What was I last working on? I remember writing a note to help me remember...  
You can download the challenge files here:
* `challenge.zip`

# Hints
* The `cat` command will let you read a file, but that won't help you here!
* Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
* When committing a file with git, a message can (and should) be included.

# Solution
Use the `wget` command to download the zip file: `wget https://artifacts.picoctf.net/c_titan/163/challenge.zip`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/6b0f5c3e-0ad1-4ecf-820e-b3cf81e81fb9)</kbd>

Next unzip the file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/fd2e22ec-6e43-4c22-9080-75dece6d2307)</kbd>

Doing a quick `ls` we can see a new directory `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/2bc4b333-7a15-424d-aec6-51385d464b4d)</kbd>

Let's `cd` into `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/cb2f3bf4-4e62-433f-95e0-a671fdebae63)</kbd>

Do another `ls` and see that there is a `message.txt` file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/51b1cca2-9409-4475-92be-0a589f83a37b)</kbd>

Referencing the hints, they mention not using cat but looking for messages in previous commits.   
This can be do with version control using the `git log` command.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/7f85b9e8-95b4-4d08-a407-8f66d61f9294)</kbd>


Flag: `picoCTF{t1m3m@ch1n3_88c35e3b}`
