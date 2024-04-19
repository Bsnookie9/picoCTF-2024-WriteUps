# Overview
- Tags: `picoCTF 2024` `General Skills` `browser_webshell_solvable` `git`
- `50 points`

# Description
I accidentally wrote the flag down. Good thing I deleted it!

# Hints
* Version control can help you recover files if you change or lose them!
* Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control)
* You can 'checkout' commits to see the files inside them

# Solution
Use the `wget` command to download the zip file: `wget https://artifacts.picoctf.net/c_titan/138/challenge.zip`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/ece4a28c-bc1e-46e7-b484-dfa96cf3e110)</kbd>

Next unzip the file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/af80729d-0aae-4920-8040-82bbe82a629c)</kbd>

Doing a quick `ls` we can see a new directory `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/2bc4b333-7a15-424d-aec6-51385d464b4d)</kbd>

Let's `cd` into `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/cb2f3bf4-4e62-433f-95e0-a671fdebae63)</kbd>

Do another `ls` and see that there is a `message.txt` file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/51b1cca2-9409-4475-92be-0a589f83a37b)</kbd>

Referencing the hints, they mention version control. We can use the `git log` command to find changes made to the file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/70b51f10-867e-4271-9fd9-f883458912ec)</kbd>

From here we can see two commits, with the previous commit being the flag creation. The hints also mention using the `checkout`   
command. This command goes "back in time" to that save point of the commit. Copy the commit id and use this command:  
`git checkout b562f0b425907789d11d2fe2793e67592dc6be93`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/5c21af4c-9a54-49c5-820d-52408bbf3bdb)</kbd>

This commit is now the HEAD of the branch. Now let's try a simple `cat` command to view the file and maybe the flag...

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/cd1a1fa1-4819-4049-b159-3bda2c8ebf4d)</kbd>

Flag: `picoCTF{s@n1t1z3_c785c319}`
