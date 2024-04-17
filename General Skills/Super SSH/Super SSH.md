# Overview
- Tags: `picoCTF 2024` `General Skills` `shell` `ssh` `browser_webshell_solvable`
- `25 points`

# Description
Using a Secure Shell (SSH) is going to be pretty important.
Can you ssh as `ctf-player` to `titan.picoctf.net` at port `53403` to get the flag?
You'll also need the password `f3b61b38`. If asked, accept the fingerprint with `yes`.

# Hints
* [https://linux.die.net/man/1/ssh](https://linux.die.net/man/1/ssh)
* You can try logging in 'as' someone with <user>@titan.picoctf.net
* How could you specify the port?
* Remember, passwords are hidden when typed into the shell

# Solution
Enter the following ssh command: `ssh ctf-player@titan.picoctf.net -p53403` Note: the -p flag designates the port number

![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/dad8bea8-f6fe-404e-be05-c4099d34c953)

Flag: `picoCTF{s3cur3_c0nn3ct10n_3e293eea}`
