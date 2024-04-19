# Overview
- Tags: `picoCTF 2024` `Forensics` `browser_webshell_solvable` `apk`
- `200 points`

# Description
Can you handle APKs?  
Download the android apk [here](https://artifacts.picoctf.net/c_titan/141/mobpsycho.apk).

# Hints
* Did you know you can unzip APK files?
* Now you have the whole host of shell tools for searching these files.

# Solution
Using the picoCTF webshell, use the `wget` command to download the APK file:   
`wget https://artifacts.picoctf.net/c_titan/141/mobpsycho.apk`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/2cda5a07-5530-4fc0-b885-e59b33ba47fe)</kbd>

Next unzip the APK file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/ad533bd0-61f5-4024-a3c6-64427b677960)</kbd>

I always like to do a `ls` to see what files/directories exist after unzipping files

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/9d0dfb66-2f6a-4482-a407-653d9ce5ffc0)</kbd>

To save some time, let's use the find command to look for the flag. Typically these challenges label the flag with a .txt

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/8975e68c-6489-4926-a002-a719379a82ea)</kbd>

The results show the flag.txt file is in the res/color directory. Let's use the `cat` command the output the flag.txt

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/b1588580-9f30-4aff-849c-39cb6448cc28)</kbd>

This output looks like it is encoded using HEX. Toss this string of text into cyberchef and decode it using HEX

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/db217056-3aa4-42e5-a7c2-a52217d163ac)</kbd> (cyberchef)

There's your flag!

Flag: `picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_b112ae57}`
