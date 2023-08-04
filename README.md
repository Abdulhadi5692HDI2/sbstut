# How to make a simple Batch Script

Main: [https://rentry.co/sbstut](https://rentry.co/sbstut)

Mirror 2: [https://rentry.org/sbstut](https://rentry.org/sbstut)

![Note](https://i.imgur.com/ABM0mQ8.png)

## Introduction
This is basically one of those Batch Script tutorials.
This one will teach about basic stuff, arguments, functions and stuff.

## Hello World!
This is our starting point!
``` batch
@echo off
echo Hello World!
pause
exit
```

If you run this script, it should look something like this:
![Output](https://i.imgur.com/TFQQoA1.png)

and you can press `space` or any other key to exit!

Let me explain, line `1` makes  the command line invisible so it looks pretty.
Line `2` uses `echo` to print `Hello World!` to the screen.
Line `3` uses `pause` to wait for any key input
Line `4` exits the script.

## Changing the colors and title of the window!
Let's modify the script a bit.

``` batch
@echo off
title My Awesome Script
color 0a
echo Hello World!
pause
exit
```

If you run the script, the result should look something like this
![Output](https://i.imgur.com/GerrhP9.png)

The titlebar has changed to `"My Awesome Script"`
And the color of the text has turned Green.

Let's explain, Line `2` uses `title` to change the title of the window.
Line `3` uses `color` to change the color to green, `0a` represents black background on green text (in hexadecimal)!
The rest is the same.

Pretty cool :)

## Functions and variables
Functions and variables are VERY VERY useful (especially in batch scripting).

So once again, we modify the script
``` batch
@echo off
set TITLE=My Awesome Script
set TEXT=Hello World!
set COLOR=0a

goto :main

:main
title %TITLE%
color %COLOR%
echo %TEXT%
pause
exit
```


`set TITLE` sets the variable `TITLE` to `My Awesome Script`
and for the other variables so on.


`goto :main` just jumps to the function `main`


`:main` declares a function.


then `title`, `color` and `echo` use the variables using the format `%variablename%`.


looks the same, just more lines of code.


## Arguments!!!!!

Arguments are somewhat useful and exciting!


In Batch Script, arguments are stored in special variables (1 to 9)

You can access the value of the arguments like this:

``` batch
REM Access argument 1
echo %1
```

Time to modify the script again!

``` batch
@echo off
goto :main

:main
title %1
color %2
echo %3
```

Running the script like this:
`C:\users\username> helloworld.bat Script 0a Hello!`

should make the following result:

![Output](https://i.imgur.com/dUxVrvp.png)

## Comments
Comments help us to outline and explain pieces of code.

In Batch Script there's 2 ways to make comments in code.
``` batch
REM this is a comment
:: this is also a comment
```

`REM` and `::`, the differences?

the first one may cause lag if used too much.

## IF Statements
IF statements are very very very very useful.

Here's a example, (it should be self explanatory!):

``` batch
@echo off
REM use %random%, a special variable that returns a random number
set CODE=%random%
set CODE2=%CODE%001
if not %CODE%==%CODE2% (
	echo not equal lol.
)
pause
exit
```

The result should look like this:
![Output](https://i.imgur.com/09z235C.png)

## Files and Folders
### Folders!!!
To create a folder in batch script, you simply use the `mkdir` command.
``` batch
@echo off
mkdir normal
exit
```
To remove a folder, use `del` and `rmdir`
``` batch
@echo off
del normal\*.*
rmdir normal
exit
```
### Files!
To make a file, use `echo`  to make a file using the `>` to redirect output to the file (overwriting the current contents)
``` batch
@echo off
echo funni > file.txt
exit
```
To append stuff to a file, use `echo` using the `>>` to redirect output to the file (appending the data)
``` batch
@echo off
echo something >> file.txt
exit
```
To delete a file, use `del`
``` batch
@echo off
del taxes-2023.docx
exit
```
To copy a file, use `copy`
``` batch
@echo off
copy file.txt ..\file-diameter.txt
exit
```

#### Checking if a file exists!
Using the `if` statements, it's possible.

Check if a file exists:
``` batch
@echo off
if exist file.txt echo exists!
exit
```

Check if a file does not exist:
``` batch
@echo off
if not exist sanity.txt echo file "sanity.txt" does not exist!
exit
```

## User input
User input allows someone to type stuff in.

Here's a fresh example
``` batch
@echo off 
set /p name=What's your name: 
echo Hello %name%!
pause
exit
```

This makes use of the `/p` switch for the `SET` command.

The result should look somewhat similar to this:
![Output](https://i.imgur.com/xU0goqN.png)

## "Arrays"
Ok just kidding, arrays don't exist as a type, but can be implemented.

Like this:
``` batch
@echo off
set realarray[0]=real
set realarray[1]=not
set realarray[2]=.
echo %realarray[1]% %realarray[0]% %realarray[2]%
exit
```

### "Structures"
Structures also don't exist, but you know the drill. (IMPLEMENT AND STUFF)

Something like this looks similar:
``` batch
@echo off
REM this is very unusable
set realstruct[0].Number = %random%
set realstruct[0].Name = random
set realstruct[1].Invalid = %realstruct[0].Number%%random%

REM who would even need this!
echo Name = %realstruct[0].Name%
echo Number = %realstruct[0].Number%
echo Invalid bit = %realstruct[1].Invalid%
```
