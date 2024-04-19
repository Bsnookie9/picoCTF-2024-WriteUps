# Overview
- Tags: `picoCTF 2024` `General Skills` `browser_webshell_solvable` `git`
- `75 points`

# Description
Someone's commits seems to be preventing the program from working. Who is it?  
You can download the challenge files here:
* [challenge.zip](https://artifacts.picoctf.net/c_titan/156/challenge.zip)

# Hints
* In collaborative projects, many users can make many changes. How can you see the changes within one file?
* Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
* You can use `python3 <file>.py` to try running the code, though you won't need to for this challenge.

# Solution
Use the `wget` command to download the zip file: `wget https://artifacts.picoctf.net/c_titan/156/challenge.zip`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/320d2616-ef4b-4279-840e-59405f43954d)</kbd>

Next unzip the file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/b316fc51-8d86-43d0-94c5-be1d7b9e909f)</kbd>

Doing a quick `ls` we can see a new directory `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/2bc4b333-7a15-424d-aec6-51385d464b4d)</kbd>

Let's `cd` into `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/cb2f3bf4-4e62-433f-95e0-a671fdebae63)</kbd>

Do another `ls` and see that there is a `message.py` file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/4162d5a9-dce5-4d52-855d-522793d77bea)</kbd>

We need to find the author of the commit that is causing the program error. We'll use the `git log` command.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/bd85dcd5-c1e6-40c1-ba35-6cff44bb3711)</kbd>

The flag is in the author of the most recent commit.

Flag: `picoCTF{@sk_th3_1nt3rn_d2d29f22}`
