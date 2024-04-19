# Overview
- Tags: `picoCTF 2024` `Forensics` `browser_webshell_solvable`
- `300 points`

# Description
Here's a file that was recovered from a 32-bits system that organized the bytes a weird way. We're not even sure what type of file it is.  
Download it [here](https://artifacts.picoctf.net/c_titan/112/challengefile) and see what you can get out of it.

# Solution
This challenge I struggled with a lot with comprehending big and little endian. I had to use this [write-up](https://medium.com/@0xVirtu4l/picoctf-2024-endianness-v2-challenge-solve-f9c93d6b8fa6)

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/c151d364-ced4-488e-9557-77b365f5fdaa)</kbd>

Flag: `picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_f72c4bf7}`
