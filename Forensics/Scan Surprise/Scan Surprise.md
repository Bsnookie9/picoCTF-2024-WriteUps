# Overview
- Tags: `picoCTF 2024` `Forensics` `shell` `browser_webshell_solvable` `qr_code`
- `50 points`

# Description
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?  
You can download the challenge files here:
* challenge.zip
  
The same files are accessible via SSH here:
`ssh -p 62141 ctf-player@atlas.picoctf.net`  
Using the password `f3b61b38`. Accept the fingerprint with yes, and ls once connected to begin.  
Remember, in a shell, passwords are hidden!

# Hints
* QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
* Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
* If you don't have access to a phone, you can also use zbar-tools to convert an image to text

# Solution

Enter the command `ssh -p 62141 ctf-player@atlas.picoctf.net`

Then accept the fingerprint with `yes` and then `ls`

From here there is a QR code image that pops up. 

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/6739eed4-6b8b-4fde-928d-14c1a2bee768)</kbd>

Use a mobile phone to scan the code or you can use any qr code scanning application that you prefer. After scanning the QR code you will get another pop-up containing the flag!

<kbd>![flag](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/845f377e-90fb-465d-8f81-afd971b5b969)</kbd>

Flag: `picoCTF{p33k_@_b00_d4ca652e}`
