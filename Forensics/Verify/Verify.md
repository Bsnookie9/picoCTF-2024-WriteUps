# Overview
- Tags: `picoCTF 2024` `Forensics` `grep` `browser_webshell_solvable` `checksum`
- `50 points`

# Description
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?  
You can download the challenge files here:
* [challenge.zip](https://artifacts.picoctf.net/c_rhea/20/challenge.zip)
  
The same files are accessible via SSH here:
`ssh -p 663920 ctf-player@atlas.picoctf.net`  
Using the password `f3b61b38`. Accept the fingerprint with yes, and ls once connected to begin.  
Remember, in a shell, passwords are hidden!
* Checksum: fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
* To decrypt the file once you've verified the hash, run `./decrypt.sh files/<file>`.


# Hints
* Checksums let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file.
* You can create a SHA checksum of a file with `sha256sum <file>` or all files in a directory with `sha256sum <directory>/*`.
* Remember you can pipe the output of one command to another with `|`. Try practicing with the 'First Grep' challenge if you're stuck!

# Solution
Enter the ssh command `ssh -p 663920 ctf-player@atlas.picoctf.net` then accept the fingerprint by entering `yes`

Enter the password `f3b61b38` then `ls` to see what files or directories exist in the current directory.

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/cc12b07f-e0db-4ee8-81fa-27e850ddd2e1)

You can see that three things exist: a checksum text file, a decryption script, and a directory called `files`.

Enter the following command to see the checksum: `cat checksum.txt`.

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/abdbdc76-2ab6-45af-960c-f406cdaef6ed)

Now you need to find the file with the corresponding checksum. 

    Note: Change directories to /files, you can see all the encrypted files.

From here you need to do a SHA256 checksum of all the files in the files directory. Use the `sha256sum` command.

There are two ways to get the output:
1. First complete the SHA256 checksum, output to a text file, and grep the checksum from the text file using these commands:  
`sha256sum files/* > output.txt` followed by `grep "<checksum>" output.txt`
   
2. Do it all in one command: `sha256sum files/* | grep "fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7"`

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/487edf59-c65d-4075-83de-cafedbc33010)

Both give the same output: `fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7  files/87590c24`.  
The file with the matching checksum is `87590c24`.

Then use the decrypt script to decrypt the file and to get the flag: `./decrypt.sh files/87590c24`

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/f1078dc3-70b2-42d9-abab-f9150d835786)

Flag: `picoCTF{trust_but_verify_87590c24}`
