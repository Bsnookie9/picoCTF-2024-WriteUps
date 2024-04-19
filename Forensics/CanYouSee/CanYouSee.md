# Overview
- Tags: `picoCTF 2024` `Forensics` `browser_webshell_solvable`
- `100 points`

# Description
How about some hide and seek?  
Download this file [here](https://artifacts.picoctf.net/c_titan/130/unknown.zip).

# Hints
* How can you view the information about the picture?
* If something isn't in the expected form, maybe it deserves attention?

# Solution
Using the picoCTF webshell, use the `wget` command to download the image file:   
`wget https://artifacts.picoctf.net/c_titan/130/unknown.zip`

Then unzip the file: `unzip unknown.zip`

From here use the `exiftool` command to extract the metadata from the image:  
`exiftool ukn_reality.jpg`

Here are the results you'll see

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/e901f113-e677-461c-908b-a3eef2693153)</kbd>

Looking at the metadata, you can see that the attribution URL looks to be a Base64 encoded blob.  
Take this long string and pop it into cyberchef using the Base64 decoder:

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/b2d69ff0-cbfc-43c8-890e-bdfbeddf1596)</kbd>

You found the flag!

Flag: `picoCTF{ME74D47A_HIDD3N_6a9f5ac4}`
