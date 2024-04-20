# Overview
- Tags: `picoCTF 2024` `General Skills` `browser_webshell_solvable` `git`
- `75 points`

# Description
Someone's commits seems to be preventing the program from working. Who is it?  
You can download the challenge files here:
* [challenge.zip](https://artifacts.picoctf.net/c_titan/156/challenge.zip)

# Hints
* `git branch -a` will let you see available branches
* How can file 'diffs' be brought to the main branch? Don't forget to `git config`!
* Merge conflicts can be tricky! Try a text editor like nano, emacs, or vim.

# Solution
Use the `wget` command to download the zip file:   
`wget https://artifacts.picoctf.net/c_titan/179/challenge.zip`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/74fdd4a3-0e98-428b-b68e-4da68b423617)</kbd>

Next unzip the file

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/1e1c8d8d-0c71-42a0-a4f1-4224c55e99d0)</kbd>

Doing a quick `ls` we can see a new directory `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/2bc4b333-7a15-424d-aec6-51385d464b4d)</kbd>

Let's `cd` into `drop-in`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/cb2f3bf4-4e62-433f-95e0-a671fdebae63)</kbd>

Do another `ls` and see that there is a `flag.py` file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/d9c7c524-47cf-4c6e-859b-e117a43419c2)</kbd>

Let's do a quick `cat` to see what the .py file contains

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/db45ab9c-0fd9-43a1-90fa-52e02308181d)</kbd>

From this we can infer that the rest of the flag exists somewhere else. To see the other exisiting branches,   
use the `git branch -a` command. The -a option tells us that we are currently on the main branch.   
The other branches must be where the flag is.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/fc0c8a9d-89d2-4192-9249-f67b06dd01ca)</kbd>

To move branches, use the `git checkout` command. 

> [!NOTE]
> To find the current branch, use the `git status` command

Try this command: `git checkout feature/part-3` then `cat flag.py`.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/18c90422-42c5-4a09-8c50-fc021ba0b029)</kbd>

From this we can see that the flag must be split into the three different branches and needs merged.  
We want to checkout branch "feature/part-2" since we want to merge feature/part-3 to feature/part-2   
and so forth all the way until main.

After switching branches, we need to use the `git merge` command, followed by feature/part-3.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/81be159a-9948-47f4-9aab-d1a41ab32406)</kbd>

We've now experienced our first merge conflict. To fix this, open the flag.py file in an editor, such as vim. 

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/c595094c-5779-468a-9307-14438e58682f)</kbd>

The start of the conflict is marked with `<<<<<<< HEAD`, and the end of the conflict is marked with `>>>>>>> <branch name>`. Somewhere in the middle will be a `=======` which marks the division between the lines in each branch.

To edit using vim, press `i` to insert, then use the arrow keys to move around and fix the conflicts. The result should look something like this:

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/7192a68b-c106-4973-ba54-769e6a6297f1)</kbd>

To save type `:w`, then type `:q` to exit the editor

Now we meed to add the newly edited file back into the branch and commit the edit. However, since our username is different than that of the original author, we must use `git config`.   
To find this information, let's run a `git log` on the file.

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/e10f05ed-52ee-4194-9769-8137186432c1)</kbd>

We can see that the author is `picoCTF` with the email address `ops@picoctf.com`

We need to change the global user.email and user.name. To do this use the following commands:  
`git config --global user.email "ops@picoctf.com`  
`git config --global user.name "picoCTF`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/4528a7fe-e61b-4c05-a7ca-4450c5dc5ca6)</kbd>

Now run the following commands: `git add flag.py` and `git commit -m "picoCTF"`

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/6652f45e-7552-483b-8177-d504c511db11)</kbd>

> [!IMPORTANT]
> Repeat the steps above this line until you get to the main branch!

Making the last commit into the main branch should look like this:

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/ae793d0d-d10e-4719-b496-cf566a1a9ee7)</kbd>

Since we have successfully merged all the commits together to the main branch, the .py file should print the flag!

<kbd>![image](https://github.com/Bsnookie9/picoCTF-2024-WriteUps/assets/106827110/3b2123ee-0b6b-4c58-912a-1e55159244c8)</kbd>

Flag: `picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_798f9981}`
