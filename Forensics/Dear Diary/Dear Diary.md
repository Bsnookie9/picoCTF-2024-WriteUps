# Overview
- Tags: `picoCTF 2024` `Forensics` `disk` `browser_webshell_solvable`
- `400 points`

# Description
If you can find the flag on this disk image, we can close the case for good!
Download the disk image [here](https://artifacts.picoctf.net/c_titan/63/disk.flag.img.gz).

# Hints
* If you're observing binary data raw in the terminal you may be misled about the contents of a block.

# Solution
I started this challenge using Autopsy, getting through the setup of the case and using default settings, I was able to finally to start the analysis.

I clicked `Analyze` and then `Keyword Search` to search for ".txt" using the ASCII option.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/f3beca58-bfed-4a49-bd4c-a8a773d852b5)</kbd>

This then resulted in a bunch of occurrences. Clicking the `ASCII` option on each unit, you'll notice that the flag is in pieces starting at unit 7. 

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/47329904-8e42-41fe-a3c6-d7d28537c3c8)</kbd>

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/a5e6d4bc-8f41-4495-8717-7403bf5d6eeb)</kbd>

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/b7de12ef-465c-4b3a-90ae-0876ca425840)</kbd>

Put them together and you got your flag!

Flag:`picoCTF{1_533_n4m35_80d24b30}`
