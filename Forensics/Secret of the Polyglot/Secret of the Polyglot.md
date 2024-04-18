# Overview
- Tags: `picoCTF 2024` `Forensics` `file_format` `polyglot`
- `100 points`

# Description
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting   
conflicting information on what type of file it is.They've brought you in as an external expert to examine the file.   
Can you extract all the information from this strange file?  
Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/7/flag2of2-final.pdf).

# Hints
* This problem can be solved by just opening the file in different ways

# Solution
When you download the file, you will see it is a PDF. Opening the file you will find the second half of the flag:

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/18ee5da2-f6ad-4e43-94b8-cd4184994c23)

The hint mentions opening the file in different ways. Thinking about file forensics, changing the file type can reveal hidden items.

I opened the file in notepad and noticed the PNG stamp in the top left-hand corner. 

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/11b53cdb-ae72-4544-adf6-35ee2f4ac265)

Try changing the file extention to PNG. Open the file and you will see the first half of the flag to piece together. 

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/8956891f-1262-4cb9-baa4-c3f5eea3f9cd)

Flag: `picoCTF{f1u3n7_1n_pn9_&_pdf_53b741d6}`
