# Lab Report 1 - Remote Access and FileSystem

## Installing VS Code

1. Head to the VS Code [website](https://code.visualstudio.com/) and follow the instructions to install it onto your computer. The website supports all major operating systems such as MacOS and Windows.
&nbsp;  
&nbsp;   
![Image](https://raw.githubusercontent.com/kevinlu021/cse15l-lab-reports/main/Lab%201/Images/Screenshot%202023-04-08%20at%206.38.35%20PM.png)
2. After installation, open up VSCode. The color scheme and layout may vary due to different settings, but the new window should look something like this:
&nbsp;  
&nbsp; 
![Image](https://raw.githubusercontent.com/kevinlu021/cse15l-lab-reports/main/Lab%201/Images/Screenshot%202023-04-08%20at%206.51.33%20PM.png)

## Remotely Connecting

1. Look up your course-specific account for CSE15L [here](https://sdacs.ucsd.edu/~icc/index.php), and copy the username to your clipboard.
2. Open up your terminal by typing ``shift + ` + control`` in VSCode or opening up `Terminal` in your Launchpad.
3. Type in `ssh <username>@ieng6.ucsd.edu`.
4. Enter in your password when prompted. The terminal hides whatever you type, so just hit `Enter` on your keyboard when finished.
The final result will look something like this: 
&nbsp;  
&nbsp;  
![Image](https://raw.githubusercontent.com/kevinlu021/cse15l-lab-reports/main/Lab%201/Images/Screenshot%202023-04-08%20at%209.30.36%20PM.png)

## Trying Some Commands

Here are some commands you can try on your remote server:
* `cd` - Navigate between different directories or folders on your file system
* `cd ~`-  Takes you to the home directory of the current user.
* `pwd` -  Display the current working directory or folder that the user is located in within the computer's file system.
* `ls -lat` - List the contents of the current directory. Includes hidden files and directories (starting with a dot). 
* `ls <directory>`, where `<directory>` is `/home/linux/ieng6/cs15lsp23/cs15lsp23abc`, where the `abc` is one of the other user - Will list the contents of that user's directory.
* `cp`- Make a copy of a file or directory.
* `cat` - Display the contents of a file on the terminal

Outputs of these sample commands can be seen here:
&nbsp;  
&nbsp;  
![Image](https://raw.githubusercontent.com/kevinlu021/cse15l-lab-reports/main/Lab%201/Images/Screenshot%202023-04-08%20at%209.44.36%20PM.png)
&nbsp;  
&nbsp;  
We start off by changing to the home directory from the home directory, so effectively nothing happens. Then, we print the working directory that we are in, which shows the absolute path of the home directory. After typing in `ls -lat` we see a list of hidden files that include the name, date and time of creation, and the read write execute permissions for each of the individual files. However, `ls` shows a list of the public files and directories. We can use `ls` on a directory we aren't currently in by adding the directory afterwards. In this case we chose the linux folder. We can also copy files and folders in directories into other directories with the `cp` command. If we want to see the specific contents of a single file, we can use the `cat` command as shown.
