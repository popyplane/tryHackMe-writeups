# Room: <Room Name>

**Platform:** TryHackMe
**Category:** Learn
**Difficulty:** Easy
**Estimated time:** `20 min`
**Tags:** `Linux fundamentals`

---

## TL;DR

Here are the very beginning of Linux usage. Explanation of what is a terminal and a machine to test them in real time!

---

## 1) Linux Background

##### Where is linux used?
**Linux** may appear more complex than other operating systems like **Windows**, but it is a *lightweight* and *highly versatile* platform. It’s used extensively in everyday technologies, powering websites, car control systems, Point of Sale (PoS) terminals, and even critical infrastructure.

##### Flavours of Linux
The term **Linux** refers to a family of operating systems built on the ***UNIX foundation***. Being open-source, Linux has countless distributions tailored for different purposes. Among them, **Ubuntu** and **Debian** are the most common, offering flexibility to run as both servers and desktop systems. For this room, Ubuntu is used as the base distribution, known for its efficiency—even capable of running on systems with just `512MB` of RAM.

---

## 2) Interacting With Your \*First\* Linux Machine (In-Browser)
This stage only shows us a *Linux* machine deployable using the given `Start Machine` button.
They don't ask anything to do yet.

## 3) Running Your \*Firsts\* Few Commands
Now they introduce *the terminal*. As Linux is much more lightweight than other OSs, this comes with some disavantages such as the lack of *Graphical User Interface* (GUI). In that way, the only way to communicate with the machine remains *the terminal*.
It is purely text-based and can be a bit intimidating at first but don't be afraid, after some commands you'll be soon familiar with.

Let's dive in now! We can test the first command. Type `echo` then anything you want to display it on the terminal:

![Echo command](images/echo_command.png)

And voilà! You just made your first command!

We can also try the command `whoami` to know which user we are connected with:

![whoami command](images/whoami_command.png)

Here as we can see, we are connected with the user `tryhackme`

## 4) Interacting With the Filesystem!

Okay! So now we've done some commands, let's introduce those I'm using quite everyday now as a developer. Those commands are used to navigate through the file system, checking wich files are present inside the current directory etc.

- `ls` : It's giving a **listing** of files and directories in the current directory. You can also run `ls` + `[directory name]` to output the listing of that directory.

- `cd` : Short for **Change Directory**, you just have to type `cd` + `[the location you want}` to go to that location.

- `cat` : That command principaly shows the content of a file. As previous commands, you have to specify which file you want to see this way `cat` + `[file]`. This can also be used to transfer the content of a file to another but we'll see this later.

- `pwd` : This stands for **Print Working Directory**. While navigating through files using `cd`, it can be easy to get lost. Using `pwd` is a short way to know where you currently are inside the filesystem.

## 5) Searching For Files
When you need to find a file, using manually `cd` and `ls` can be very loong depending on how the filesystem is organized.
Instead, we can use `find`. At this point, things are about to get complicated.

If we are searching a file while knowing it's full name it's still easy. You just have to put the command `ls` + `-name` + `[filename]`.
Here we are using a flag `-`, quite all commands can have options while using flags, here it's to specify that we are searching a file with that name.

Okay and know what if we don't remember the exact filename? We can try to search for all `.txt` files with the command `find -name *.txt`.

Now if we want to search *specific* informations inside a file? You can use `grep`. First you need to specify what you're looking for, then the file which you want to search in. `grep "[terms searched]" [filename]`.

## 6) An Introduction to Shell Operators
In Linux, you can chain and redirect commands using a few handy operators.
The `&` lets you run a command in the background so you can keep using the terminal while it runs.
For example, `ping google.com &` starts pinging in the background and gives you back control.
Then there’s `&&`, which is used to run a second command only if the first one succeeds — for instance, `mkdir test && cd test` will only move into the folder if it was created successfully.
Now for redirection: `>` sends the output of a command into a file, replacing anything that was already there (`echo hello > file.txt`).
If you don’t want to overwrite but instead add to the file, use `>>` (`echo " world!" >> file.txt`).
It’s super useful for logging, saving output, or chaining scripts without cluttering your terminal.
These simple operators make your commands way more powerful once you start combining them.

---

## 7) Conclusion
This piece, although very useful for beginners, did not teach me anything new. I spend a huge amont of time redacting those writeups and i think some rooms are a lost of time, maybe i'll speedrun these to focus on later more interesting rooms.


