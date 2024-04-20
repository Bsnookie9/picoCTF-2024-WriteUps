# Overview
- Tags: `picoCTF 2024` `General Skills` `browser_webshell_solvable`
- `200 points`

# Description
Know of little and big endian?  
[Source](https://artifacts.picoctf.net/c_titan/78/flag.c)  
`nc titan.picoctf.net 65339`

# Hints
* You might want to check the ASCII table to first find the hexadecimal representation of characters before finding the endianness.
* Read more about how endianness [here](https://levelup.gitconnected.com/little-endian-and-big-endian-74ab6441b2a7).

# Solution
First enter the netcat command given: `nc titan.picoctf.net 65339` into the webshell

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/09f10c53-565e-47aa-ab77-82bde5cf4e49)</kbd>

Now we need to find the big and little endian of the given word, in this case my word is `vjewx`. Use CyberChef to convert the text to hex.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/3138325e-3e12-4269-8365-c99f84bf3d68)</kbd>

This is the big endian representation. Now take that big endian and use a [converter](https://www.save-editor.com/tools/wse_hex.html#littleendian) to get the little endian representation.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/43f39519-f77b-467e-bcaf-def624036c44)</kbd>

Now take those two representations and enter them in the webshell

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/27f3beae-f8ed-44ca-a4ba-e5e01b0107c5)</kbd>

You've got the flag!

Flag: `picoCTF{3ndi4n_sw4p_su33ess_cfe38ef0}`
