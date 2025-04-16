---
title: Introduction to Command Line Interface
linkTitle: Learn CLI tools
summary: An introductory course on command line interface
date: '2025-04-01'
type: book
tags:
  - previous
---

{{< figure src="featured.png" >}}

{{< toc hide_on="xl" >}}


## What is Linux?
Linux is an operating system that evolved from a **kernel** created by [Linus Torvalds](https://www.linux.org/threads/what-is-linux.4106/). It evolved from an old UNIX system, but it is important to remember that:
1. Linux **is not** a program
2. Linux **is an interface** between computer/server hardware and the programs that run on it.

People would often say *Linux is just a kernel*, but it turns out that a **kernel** is the focal point of any OS. A kernel is literally what tells the big chip what to do with the programs you are using. To make a relatively appealing example, think of a nice plate of **pappardelle with wild boar ragu** (a typical dish from my home region in Italy). If the **dish** itself is the operating system, the **ingredients** (tomato sauce, meat, persley, etc) are the programs that run on it, and the **pasta** is the kernel. Without **pasta** the dish completely loses its significance, no matter the quantity of programs that run on it. 

**Why you should use Linux today?**

Below I will give you my reasons as to why you should consider using Linux. This is beyond being and exhaustive list of reasons, or an absolute list of reasons.

1. Linux is **FREE** and **OPEN-SOURCE**. You can easily look at its source code, and if you are crazy enough even attempt to mdify it. The open-source characteristic is probably the most beautiful aspect, as over the years, people have contributed to its development. You now have gazillion Linux distributions which you can try and choose from, but most importantly, you have a massive community behind Linux ready to help when you have a problem.
2. **AMAZING** software mamagement through packages. You can update your systems and your applications **WHENEVER** you feel like it (unlike other OSs).
3. Linux is **stable**, very **light**, and **reliable**. This is the reason why it is the first choice as OS in Internet Servers, Cloud systems, and Clusters.
4. Linux is **safe** and **transparent**. Due to its large community-based developments at its back, Linux is probably the safest OS in terms of malwares and attacks. This does not mean that it is immune!

**Why you should not use Linux?**
1. Linux **IS NOT** very user friendly and it can be confusing for non-tech savy people. The learning curve might be steep at first.
2. Linux has small peripheral hardware drivers compared to windows. If you are a hard-core gamer, Linux is probably not your choice (yet ...).
3. If you use Linux regularly you might run into compatibility issues with commonly used programs in corparate offices or companies (MS Word, MS excel, etc).


## Basic UNIX concepts?
It is important, before we dive into the **command line**, to clarify a few important UNIX concepts:
1. **File**: data stored in a standard format that behaves in a certain way depending on its function in the system. In Linux (UNIX in general) everything is a file.
2. **Program**: a file that can be executed (run).
3. **Process**: a program that is being executed.
4. **Ownership**: in UNIX sytems files/programs/processes are owned by a user and a group.
5. **Hierarchical directory structure**: files are organized in **directories** (you would call them folders) that can have a parent or children. Example: in the path /home/user/sim1/run.sh the file named *run.sh* is contained in the directory <mark>sim1</mark> and <mark>user</mark> is its parent directory.

<span style="color:red">Managing your files and processes in an organized way is a crucial step in the correct utilization of the system.</span>

## The SHELL

The **shell** is a program that takes (interpret) commands from the keyboard and gives them to the OS to perform. The shell is a comand line interface (CLI), and it will be the main focus of this short course. The shell provides:
1. Built-in commands.
2. Programming control structures.
3. Environment variables.

Linux supports several shell programs, but the default is usually **BASH** ([Bourne Again SHell](https://www.gnu.org/software/bash/)).

The **Terminal** is a program called a terminal emulator. This is a program that opens a window and lets you interact with the shell. Once again, there are several terminal emulators supported by Linux systems: gnome-terminal, konsole, xterm, nxterm, and eterm.

The **Prompt** is that first line that pops up when you first open a terminal application. It is very informative, and it might look something like this:
```
francesco@rafaela : (~) ->
```
This is the prompt of my own device, and most likely yours will look different, but here is what the prompt is telling us (or me in this case):
- **Username**: francesco
- **System/computer name**: rafaela
- **Current working directory** (~). In Linux the symbol <mark> ~ </mark> is a shorthand for HOME directory.
- **Blinking cursor**: the terminal is always waiting for the user input. It usually displays a blinking cursor.

The basic syntax to give commands to the Shell is the following:
```
command [OPTIONS] argument(s)
```

- **command**: is the keyword that identifies the specific command you are trying to run.
- **[OPTIONS]**: optional, they add more specifics to the command you are running.
- **argument(s)**: are the argument(s) required by the command to run.

## How do I follow this course?
The best thing you can do is open a terminal window and follow along by running every command as we learn them. This course does not require any prerequisite knowledge. To make sure you are using the same terminal application I am using:
1. **Linux users**: there is nothing you should do.
2. **MAC OS users**: run the following command:
```
exec bash -l
```
For a temporary swith to **bash**. If you want to use bash as your permanent shell, you can run:
```
chsh -s /bin/bash
```
3. **Windows users**: you have several options. The most common is probably [Windows Subsystem Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install). You can also install [MobaXterm](https://mobaxterm.mobatek.net/) which is an enhanced terminal for Windows with X11 server, tabbed SSH client, network tools and much more.

## Basic SHELL commands
#### Print Working Directory (PWD)
In Linux the directory you are currently in is called the working directory. When using the shell, it is very easy to get lost and the <mark>pwd</mark> command will be your compass.
```
francesco@rafaela : (Teaching) -> pwd
/Users/francesco/QueensU/Teaching
francesco@rafaela : (Teaching) -> 
```
When we first log into our Linux system, the working directory is set to our home directory (~). This is where we put our files. In most systems, the home directory will be called <mark>/home/username</mark>, but it can be anything according to the wishes of the system administrator.

#### List directory content (LS)
In Linux, to list the content of a directory, we use the command <mark> ls </mark>. The syntax is the following:
```bash
ls [option] [directory]
```
By running the <mark> ls </mark> command as is in the previous example, I get:
```bash
francesco@rafaela : (Teaching) -> ls
00_EXTRAS  02_MREN241 04_MECH330 06_MREN230
01_MECH241 03_MECH398 05_MECH444 07_APSC103
francesco@rafaela : (Teaching) -> 
```
Which tells me that insite the directory named <mark>teaching</mark> there are 8 direcories numbered from 00 to 07 conatining information on all the courses I have taught throughout these years at Queen's University. Take a very good look at the naming convention I use for my files. It is probably not the best (for some) but the most important detail I want your attention on is that **there are NO spaces in the name**.

Common options of the <mark>ls</mark> commands are:
- **ls -l**: list the files in a directory with extended information.
- **ls -a**: list all files, including hidden files (files with names starting with a dot, for example .bashrc).

#### Change directory (CD)
In Linux, to move around directories (change) we use the command change directory or <mark>cd</mark>:
```bash
cd pathToDirectory
```
In the example before, if I want to get inside <mark>01_MECH241</mark> I would type:
```bash
francesco@rafaela : (Teaching) -> ls
00_EXTRAS  02_MREN241 04_MECH330 06_MREN230                                                     
01_MECH241 03_MECH398 05_MECH444 07_APSC103
francesco@rafaela : (Teaching) -> cd 01_MECH241/
francesco@rafaela : (01_MECH241) -> pwd
/Users/francesco/QueensU/Teaching/01_MECH241
francesco@rafaela : (01_MECH241) -> 
```
You would notice that the prompt has changed, and from (Teaching) it is telling me that I am now in (01_MECH241), and if I run <mark>pwd</mark> it would show me the full path. One of the beautiful aspect of using the CLI to move around directories is that I do not have to be in the parent directory to move inside my destination, but I only need to know the **absolute path**. In the example before, I could go in any location (for example Desktop), and go back to <mark>01_MECH241</mark> with one simple command:
```bash
francesco@rafaela : (Desktop) -> cd /Users/francesco/QueensU/Teaching/01_MECH241
francesco@rafaela : (01_MECH241) -> 
```
Using the mouse or trackpad, this would have cost me at least 5 clicks. The notation <mark> . </mark>  refers to the working directory itself, and the notation <mark> .. </mark>  refers to the working directory's parent directory. By yourself try the following commands and analyze the output: 
```bash
cd .
cd ..
cd ../../
```

#### Create a file using TOUCH
In the shell, if you want to create a file (remember what a file is!) you can use the command <mark>touch</mark>. This command creates a file without opening it, and without adding anything in it. The syntax is the following:
```bash
touch file_name
```
If I want to create a .txt file for instance, I would type:
```bash
touch myFile.txt
```
And if I use my preferred text editor ([check out my course on VIM](https://francescoambrogi.github.io/courses/my-vim-course/)) to open it, I would see that the file is indeed empty.

<span style="color:red">Danger !!!</span> The name you choose for your files is VERY important in a UNIX system:
- File names that begin with a period character are hidden. This only means that ls will not list them unless we say ls -a.
- File names in Linux, like Unix, are case-sensitive. The file names "File1" and "file1" refer to different files.
- **Do not** embed spaces in file names. If you want to represent spaces between words in a file name, use underscore characters. You will thank me later.

#### Create a new directory using MKDIR
In the shell, if you want to create a new directory (remember what a directory is!) you can use the command <mark>mkdir</mark>. This command creates a new directory in the specified location with nothing in it. The syntax is the following:
```bash
mkdir fullPathToDirectoryName
```
**TASK**: from my desktop I want to create a new directory in <mark>Teaching</mark> named <mark>08_CLI</mark>. I would type the following:
```bash
francesco@rafaela : (Desktop) -> mkdir ~/QueensU/Teaching/08_CLI
francesco@rafaela : (Desktop) -> ls ~/QueensU/Teaching/
00_EXTRAS  02_MREN241 04_MECH330 06_MREN230                                                     
01_MECH241 03_MECH398 05_MECH444 07_APSC103 08_CLI
francesco@rafaela : (Desktop) -> 
```
Notice that I have **created** the dirctory and **listed** the directory content without leaving the original location. This is another very important aspect of using the CLI.

#### A very important MAN
The <mark>man</mark> command, short for manual, is a powerful tool in the Linux operating system that allows users to access detailed information about various commands, utilities, and system calls. Just like any other shell command the syntax for the man command is:
```bash
man [OPTIONS] command
```

Manual pages pop up in the terminal itself, and can be quite overwhelming. They are, however, a GREAT resource! Here is how to navigate them:
- **Spacebar**: move forward one page.
- **Enter**: move forward one line.
- **B**: move backward one page. 
- **Q**: quit the manual viewer.

## Installing new commands
In Linux is very easy to get lost, especially if one is used to a GUI. The <mark>tree</mark> command is a recursive directory listing program that produces a depth-indented listing of files. With no arguments, the tree lists the files in the current directory. You can install <mark>tree</mark> by running:
```bash
sudo apt install tree
```
The installation command might change based on the Linux distribution you use. The above command can be used in debian based (Ubuntu, Pop OS, etc) Linux distributions. Please refer to the the specific documentation page for more information. 

If I use the <mark>tree</mark> command on my Desktop directory, the output will be the following:
```bash
francesco@rafaela : (Desktop) -> tree
.
└── myFile.txt

1 directory, 1 file
```
In **Desktop** there is only one file named myFile.txt which we have just created.

## Homework
Open a new terminal window and perform the following:
1. Go to your HOME directory.
2. Create a new directory called "intro_shell"
3. Move into the new directory.
4. Create an empty .txt file called "my_first_file.txt"
5. List the content of your new directory.

## Managing files and directories
It will come a day when you will have to do some **bookkeeping** or general **organizing** or your directories, and the following commands will come very handy.

#### The move (MV) command
<mark>mv</mark> is very powerful command and it stands for "move". Think of it as your digital moving van, able to perform the following tasks:
- Rename files.
- Move files from one place to another.
- Tidy up your directories.

The basic syntax for the <mark>mv</mark> command is:
```bash
mv [OPTIONS] source_file(s) destination_file(s)
```

Where **source_file(s)** is the name of the files we want to rename or move, and **destination_file(s)** is the name of the destination directory or new file name. 

To make an example on how to use <mark>mv</mark> let's create a couple of random files (file1.txt, and file2.txt) and a directory (my_dir) in our Desktop. This is what you should see after running <mark>ls</mark>:
```bash
francesco@rafaela : (Desktop) -> ls
file1.txt  file2.txt  my_dir.txt
```
Now try to run the following commands and analyze the output:

{{< spoiler text="mv file1.txt 01_file1.txt" >}}
The command has renamed file1.txt. This is now the output:
```bash
francesco@rafaela : (Desktop) -> ls
01_file1.txt file2.txt    my_dir.txt
```
{{< /spoiler >}}

{{< spoiler text="mv file2.txt 02_file2.txt" >}}
The command has renamed file2.txt. This is now the output:
```bash
francesco@rafaela : (Desktop) -> ls
01_file1.txt 02_file2.txt    my_dir.txt
```
{{< /spoiler >}}

{{< spoiler text="mv 0* ./my_dir/" >}}
We now moved EVERY file that begins with 0 into my_dir:
```bash
francesco@rafaela : (Desktop) -> ls
01_file1.txt 02_file2.txt my_dir
francesco@rafaela : (Desktop) -> mv 0* ./my_dir/
francesco@rafaela : (Desktop) -> ls
my_dir
francesco@rafaela : (Desktop) -> ls my_dir/
01_file1.txt 02_file2.txt
```
{{< /spoiler >}}

{{< spoiler text="mv my_dir 01_my_dir" >}}
This command will rename the directory my_dir, but it will not alter the files inside:
```bash
francesco@rafaela : (Desktop) -> ls
my_dir
francesco@rafaela : (Desktop) -> mv my_dir 01_mydir
francesco@rafaela : (Desktop) -> ls
01_mydir
francesco@rafaela : (Desktop) -> ls 01_mydir/
01_file1.txt 02_file2.txt
```
{{< /spoiler >}}

#### Wild cards
You may have noticed in one of the previous commands that we used the * to give a very specific instruction to the shell: *every file beginning with 0*. Commands can use **wildcards** to perform actions on more than one file at a time, or to **find patterns** in a text file. Below are a few very important wildcards you might want to remember:
- The asterisk: this can represent any number of characters (including zero, in other words, zero or more characters). For instance, to list all files ending with the extension .pdf, we could write:
```bash
ls *.pdf
``` 
- Question mark ?: this can represent any single character. Example: <mark>ls file?.txt</mark> will list **ONLY** file1.txt and file2.txt
- Square brackets []: unlike the previous 2 which specify ANY character, [] lets you specify the range of characters. Example <mark> ls [fm]* </mark> will list ALL files beginning with f OR m.

#### The copy (CP) command
In Linux we use <mark>cp</mark> to copy files. The syntax, as usual, is:
```bash
cp [OPTIONS] source_file destination_file
```
A couple of important options:
- **-i** (interactive): this command will copy with a **warning** before overwriting the destination file.
- **-r** or **-R** (recursive): this will copy the directory structure recursively.
- **-p** (preserve): this will copy while **preserving** file characteristics (creation date, access time, ownership, etc.)

#### Heavy duty copy (SCP and RSYNC)
The <mark>cp</mark> is good for copying small amount of data, but CFD simulations (as some will learn!) can generate TB of data in just a couple of simulations. Moreover, results might be **sensitive**. If that's the case, your options are:
- **scp**: the very important feature of the secure copy protocol <mark>scp</mark> is that all files and passwords that are being transferred are encrypted. <mark>scp</mark> is therefore highly recommended when dealing with sensitive or proprietary data.
- **rsync**: the remote sync or simply <mark>rsync</mark> is a command line, remote and local file synchronization tool. <mark>rsync</mark> is very fast and the most important feature is that it uses an algorithm that minimizes the amount of data copied by **only moving the portion of files that are different between the source directory and the destination directory**. Therefore, <mark>rsync</mark> is extremely useful for a periodic backup of data.

#### The remove (RM) command
In Linux we use RM to remove files. The syntax, as usual, is:
```bash
rm [OPTIONS] file_name(s)
```
<span style="color:red">**DANGER: Linux DOES NOT have a recycle bin!!!**</span>

A couple of important options:
- **-i** (interactive): this command ensures that before anything is deleted it needs to be confirmed.
- **-f** (force): this will force the file(s) to be deleted. **You should generally AVOID this option, especially at the beginning**.
- **-r** (recursive): along with the current directory, this command will delete all subdirectories and files within it.
- **-v** (verbose): this will show on terminal what the command is currently doing. 

#### The FIND command
It will come a day when you will have several thousands of files, especially those of you who will run heavy numerical simulations. The <mark>find</mark> command is a very powerful tool that will help you navigate and **search** what you are looking for. Its adaptability allows users to search by name, size, modification time, or content, providing a flexible and potent solution.
```bash 
find [path] [options] [expression]
```
Example: what do you think the output of the following command will be?
```bash
find ./01_mydir/ -type f -name "*.txt"
```
{{< spoiler text="Click the arrow to display." >}}
The command has looked inside the directory 01_mydir for files ending with .txt extension. As expected it has found the following files:
```bash
francesco@rafaela : (Desktop) -> find ./01_mydir/ -type f -name "*.txt"
./01_mydir/01_file1.txt
./01_mydir/02_file2.txt
```
{{< /spoiler >}}

## File editing in CLI
#### Open text files in CLI
When using Linux, in many cases, you will not have a graphical user interface (GUI), e.g. when you are connected to a computer cluster or server. **Your very nice graphical text editors (VScode, Atom, Gedit, ...) won't work!**. Linux offers a selection of commands and tools to visualize and edit text files directly on the terminal window.

#### NANO text editor
On my website you will find [a short course on VIM text editor](https://francescoambrogi.github.io/courses/my-vim-course/) (check it out!). Here we will use a more intuitive (for beginners) command line text editor called **NANO**. Nano comes by default with most linux, mac os distributions and is an easy-to-use command line text editor for Unix and Linux operating systems. It includes all the basic functionalities, like syntax highlighting, multiple buffers, search and replace with regular expression support, spellchecking, UTF-8 encoding, and more. To open a text file in NANO you would just type:
```bash
nano file_name
```
You will notice that the editor pops up on the terminal window itself which now looks very diffent. The great thing about NANO is that you can intuitively modify the file as you would do on a regular GUI application, and it tells you the most useful commands at the very bottom.

Let's open one of the .txt we created earlier, and let's add some text to it. The NANO commands you will use the most in this course are:
- **ctrl+O**: this will save whatever text you've written but leave the file open.
- **Directional arrows**: to move around the file just like a regular document.
- **ctrl+X**: to close the file after the modifications have been saved.

#### The CAT command
A quick way to preview the contents of a text file without having to open the file in a large application, is to use the <mark>cat</mark> command. The <mark>cat</mark> command on Linux **concatenates files together**. I have modified the 01_file1.txt file to contain the following text "Ciao Francesco! Come stai?". Let's see what the output of the command <mark>cat</mark> is by typing the following:
```bash
francesco@rafaela : (Desktop) -> cat 01_mydir/01_file1.txt 
Ciao Francesco!
Come stai?
```
As expected the <mark>cat</mark> command displayed the content of the file on terminal.

#### The HEAD and TAIL commands
CAT is not the only way of efficiently visualizing text files. Sometimes we may only be interested in the BEGINNING of the text file, or in the very last lines. The <mark>head</mark> and <mark>tail</mark> commands will help in this scenario. Let's test them on the **U velocity** file below. This file comes from OpenFOAM and contains information of the streamwise velocity of a fluid flow. 

{{< spoiler text="U velocity file" >}}
```
/*--------------------------------*- C++ -*----------------------------------*\
  =========                 |
  \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox
   \\    /   O peration     | Website:  https://openfoam.org
    \\  /    A nd           | Version:  12
     \\/     M anipulation  |
\*---------------------------------------------------------------------------*/
FoamFile
{
    format      ascii;
    class       volVectorField;
    location    "284";
    object      U;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

dimensions      [0 1 -1 0 0 0 0];

internalField   nonuniform List<vector> 
12225
(
(9.85699 -0.886638 0)
(9.6663 -0.740719 0)
(9.4558 -0.429422 0)
(9.22455 -0.222148 0)
(9.00655 -0.106401 0)
(8.81446 -0.0458208 0)
(8.64763 -0.0151314 0)
(8.50547 0.000482775 0)
(8.38388 0.00840827 0)
(8.28118 0.012291 0)
(8.19288 0.0139857 0)
(8.11682 0.0149794 0)
(8.05025 0.0153808 0)
(7.99149 0.0155227 0)
(7.9386 0.0155396 0)
(7.89277 0.0152954 0)
(7.84013 0.0174052 0)
(7.83115 0.00995634 0)
(10.0545 0.227708 0)
(10.1213 0.326964 0)
(10.1196 0.26165 0)
(10.0856 0.18659 0)
(10.0435 0.134693 0)
(9.99677 0.101128 0)
(9.94406 0.0792866 0)
(9.88535 0.0645604 0)
(9.82403 0.0542457 0)
(9.76156 0.0466493 0)
(9.70015 0.040872 0)
(9.64041 0.0363031 0)
(9.58321 0.0326114 0)
(9.52893 0.0297136 0)
(9.47729 0.0271588 0)
(9.42985 0.0261196 0)
(9.38265 0.0227973 0)
(9.34781 0.0310605 0)
(10.0035 0.0581547 0)
(10.0305 0.0559486 0)
(10.056 0.0337727 0)
(10.0704 0.0328834 0)
(10.077 0.0406302 0)
(10.0779 0.0465251 0)
(10.0726 0.049336 0)
(10.0615 0.0502761 0)
(10.0463 0.0501663 0)
(10.0279 0.0494429 0)
(10.0074 0.0483852 0)
(9.9853 0.0472005 0)
(9.96226 0.0459876 0)
(9.93874 0.0448711 0)
(9.915 0.0437403 0)
(9.89178 0.0431441 0)
(9.86875 0.0420455 0)
(9.8471 0.0435137 0)
(9.99772 0.0109483 0)
(10.0111 0.0266177 0)
(10.035 0.0371192 0)
(10.0525 0.0480611 0)
(10.0644 0.0554282 0)
(10.0735 0.0581581 0)
(10.0796 0.0583233 0)
(10.0825 0.0575749 0)
(10.0829 0.0565168 0)
(10.0814 0.0553087 0)
(10.0784 0.0540191 0)
(10.0741 0.0527649 0)
(10.0688 0.0515394 0)
(10.0628 0.0504341 0)
(10.0561 0.0493478 0)
(10.0494 0.0486187 0)
(10.0424 0.047629 0)
(10.0355 0.0474476 0)
(9.99935 0.00709953 0)
(10.009 0.0316925 0)
```
{{< /spoiler >}}

- **head -n filename**: this command will show on terminal only the first **n** lines of the file. By default **n** is equal to 10.
```bash
francesco@rafaela : (Desktop) -> head -15 u_velocity 
/*--------------------------------*- C++ -*----------------------------------*\
  =========                 |
  \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox
   \\    /   O peration     | Website:  https://openfoam.org
    \\  /    A nd           | Version:  12
     \\/     M anipulation  |
\*---------------------------------------------------------------------------*/
FoamFile
{
    format      ascii;
    class       volVectorField;
    location    "284";
    object      U;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //
```
- **tail -n filename**: this command will show on terminal the last **n** lines of the file. By default **n** is equal to 10.

#### Even better the LESS command
The <mark>less</mark> command is a Linux terminal pager that shows a file’s content one screen at a time. It is useful when dealing with large text files because it does not load the entire file but accesses it page by page, resulting in fast loading speeds.
```bash
less [OPTIONS] filename
```
Useful options of the less command are:
- **-E**: less automatically exits after reaching the end of the file.
- **-N**: less displays line numbers at the beginning of each line.
- **-help**: gives a complete list of options available.

#### The GREP command
Probably one of the most useful command in the shell, the <mark>GREP</mark> command is used for searching and manipulating text patterns within files. <mark>grep</mark> is widely used by programmers, system administrators, and users alike for its efficiency and versatility in handling text data. The basic syntax of the <mark>grep</mark> command is:
```bash
grep [OPTIONS] pattern [files]
```
Useful options of the <mark>grep</mark> command are:
- **-i**: ignores, case for matching
- **-c**: this prints only a count of the lines that match a pattern.

As an example let's use the 01_file1.txt we modified earlier, and let's "grep" the word "stai":
```bash
francesco@rafaela : (Desktop) -> grep -i stai 01_mydir/01_file1.txt 
Come stai?
```
This command will show the entire line where that word (pattern) appears in the file.

## I/O redirection
In Linux standard inputs and outputs (I/O) are distributed across 3 streams:
1. Standard input - **stdin** numbered as 0.
2. Standard output - **stdout** numbered 1.
3. Standard error - **stderr** numbered 2.

During standard interactions between the user and the terminal, standard input comes from the user’s keyboard. Standard output and standard error are displayed on the user’s terminal as text. Stdin, stdout, and stderr are referred to as the standard streams. Let's try to pass the percentage sign (%) to the <mark> ls </mark> command:
```bash
francesco@rafaela : (Desktop) -> ls %
ls: %: No such file or directory
```

#### Stream redirection
Linux includes commands to **redirect** each stream:
- **>** - redirect standard output.
- **<** - redirect standard input.
- **2>** - redirect standard error.

To give an example on how to redirect a stream, we are going to perform the following steps:
1. First use the command <mark>echo</mark> to print something on the terminal:
```
francesco@rafaela : (Desktop) -> echo Ciao Francesco!
Ciao Francesco!
```
2. In the previous step "Ciao Francesco!" is the standard output of the <mark>echo</mark> command. We are now going to redirect the standard output to a new .txt file called greetings.txt:
```bash
francesco@rafaela : (Desktop) -> echo Ciao Francesco! > greetings.txt
francesco@rafaela : (Desktop) -> ls
01_mydir      greetings.txt
```
3. The <mark>echo</mark> command of the previous step has generated no output on screen because we have redirected to the greetings.txt file. Therefore, by running the <mark>ls</mark> command we now see a new file in the working directory, as expected. Let's use the <mark>cat</mark> command to see its content:
```bash
francesco@rafaela : (Desktop) -> cat greetings.txt 
Ciao Francesco!
```
4. The file greetings.txt now contains the output of the <mark>echo</mark> command. 

#### Streams redirection - append
Linux includes commands to redirect each stream without OVERWRITING:
- **>>** - redirect standard output.
- **<<** - redirect standard input.
- **2>>** - redirect standard error.

As an example, let's try to "append" the sentence "Come stai?" to the already created greetings.txt file:
```bash
francesco@rafaela : (Desktop) -> echo Come stai? >> greetings.txt 
francesco@rafaela : (Desktop) -> cat greetings.txt 
Ciao Francesco!
Come stai?
```
As expected, the stream redirection DID NOT overwrite the file content.

#### Pipes in Linux
Pipes are used in Linux to redirect a stream from one program to another. When a program's standard output is sent to another through a pipe, the first program's output will be used as input to the second, rather than being printed on terminal. The syntax for a pipe is the following:
```bash
command1 | command2
```

If the output of the <mark>ls</mark> command is a list of the directory content, what would be the output of the following line:
```bash
francesco@rafaela : (Desktop) -> ls
01_mydir      greetings.txt
francesco@rafaela : (Desktop) -> ls | less
```
<span style="color:red"> TRY IT OUT! </span>


## Bash scripting

Essentially anything you type in the command line can be put in a **bash script**. A bash script is nothing but a recipe that tells the shell what command to execute and in what order. The two main reasons you might want to learn more about BASH scripting are: **efficiency** and **productivity**. 

#### The SHEBANG
There are a couple of important rules we need to keep in mind when creating BASH scripts:
1. BASH scripts always begin with a **shebang** <mark> #!/bin/bash </mark>. The shebang is simply an absolute path to the BASH interpreter.
2. By convention, BASH scripts have a .sh extension.

#### My first BASH script
Using the commands we have learned so far, let's create our first bash script:
```bash
echo '#!/bin/bash' > my_script.sh
echo 'echo Ciao, Francesco!' >> my_script.sh
echo 'echo Come stai?' >> my_script.sh 
```
The result should be the following:
```bash
francesco@rafaela : (Desktop) -> cat my_script.sh 
#!/bin/bash
echo Ciao, Francesco!
echo Come stai?
```

Our first BASH script is now ready to be run, and the expected result should be "Ciao, Francesco! Come stai?" printed on the terminal. The syntax to run a BASH script from terminal is the following:
```bash
francesco@rafaela : (Desktop) -> ./my_script.sh 
-bash: ./my_script.sh: Permission denied
```

BASH gaves us an error! The reason for it is because my_script.sh is a file that (as of now) cannot be executed (remember what a program is!). We do not have permission to execute the file. Here it come another EXTREMELY useful command ...

#### The CHMOD command
In Linux the <mark>chmod</mark> command stands for "change mode" and it is used to change the access mode of a file. Permissions have three categories: read, write, and execute respectively represented by "r", "w" and "x". The syntax to change the mode of a file is: 
```bash
chmod [OPTIONS] [mode] filename
```

To apply what we have learned to the previous example, let's first check the current permissions on my_script.sh. We will then change its permissions to add executable:
```bash
francesco@rafaela : (Desktop) -> ls -l my_script.sh 
-rw-r--r--  1 francesco  staff  50 Apr 1 21:41 my_script.sh
francesco@rafaela : (Desktop) -> chmod +x my_script.sh 
francesco@rafaela : (Desktop) -> ls -l my_script.sh 
-rwxr-xr-x  1 francesco  staff  50 Apr 15 21:41 my_script.sh
```
We should notice that now the my_script.sh file is indeed executable, and one way you can tell is that it changed color in the terminal. We can now run our first BASH script (for real):
```
francesco@rafaela : (Desktop) -> ./my_script.sh 
Ciao, Francesco!
Come stai?
```
## Conclusion
CONGRATULATIONS! You have made it through the entire course. You have have now all the necessary information to unleash your potential and become a **command line master**. I hope this course was useful to you, if you have any feedback or know of ways to make this short course better, please reach out to me. 

CIAO CIAO


