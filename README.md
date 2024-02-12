# OverTheWire
The is a write-up to show a level-by-level progression of OverTheWire Bandit - a war game utilizing cybersecurity. 

Markdown Language help utilized: [Adam P's  GitHub](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Bandit
On this war game, the goal is to utilize Secure Shell (or SSH) to interact with bandit.labs.overthewire.org on port 2220.

To begin, I reviewed the SSH manual page - [given on OverTheWire](https://man7.org/linux/man-pages/man1/ssh.1.html).

On this page, you will notice that "-p" is the command that specifies port number.

Knowing this, our next steps come in the form of actually contacting OverTheWire through our secure shell.

**The following command line was used to access OverTheWire:** 

* ssh [bandit0@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit0.html) -p 2220

Following this we are prompted to input the username and password, which are both given ("bandit0" for both).

Through this, we are allowed to begin the levels within Bandit!

    Side note: all passwords discovered at the end of each level is the password needed to progress to the next level.
    Side note: steps discussed are in order of action!



## Bandit 0
In this level, we are told that the password to reach the next level is stored a *readme* file within the home directory. 

Going back to the ssh manual, we can find that the commands "ls" and "cat" are what we will need for this level.

* ls
    * We use the command ls in order to view the files within the *_CURRENT_* directory.
    * Entering the command results in that mentioned readme file popping up within our terminal.

* cat
    * We use the command cat in order to CONCATENATE the contents of that readme file and display it within our terminal.
    * Not being nearly as simple as when we used the ls command, we type the following command line to retreive our illusive password:
        * cat readme (scary, right?)

Assuming we followed the steps correctly, the password should now appear inside of the terminal:

<details><summary>Password:</summary>
  <pre>
  boJ9jbbUNNfktd78OOpsqOltutMc3MY1
  </pre>
</details>

Thank you to [Professor Eickholt](https://github.com/reickcs/overthewire/blob/main/README.md?plain=1) for the cool way of hiding text!



## Bandit 1
Our next step is to close our current connection with bandit0 and reconnect to OverTheWire through bandit1 (provided by the site). 

For this, the "exit" command is used.

We will now need to reconnect using bandit1 - **The following command line was used to access OverTheWire:** 

* ssh [bandit1@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit2.html) -p 2220

Remember that long password we got from the readme file on level 0? Were going to need it here.

**_--I HOPE YOU DIDN'T TRY TO CTRL+V THE PASSWORD INTO THE TERMINAL!--_**

CTRL+V (and CTRL+C for that matter) does not work in our current conditions. When you attempt to CTRL+V / CTRL+C into a terminal the action will *hang*.

To avoid this scenario, we use CTRL+SHIFT+V (or CTRL+SHIFT+C): a work-around learned in class.

Upon pasting in the password, we are now connected! 

**The following steps were used to further our progress:**

* The "ls" command, as we will need to find another file.
    * As specified by the website, we are looking for a file named "-" which contains our next password.

* The "cat" command, as said file contains our password.
    * HOWEVER, simply using the command line "cat -" will not do anything.

        * Am I somehow no longer inside of the home directory?
        * No, we would not see the file "-" if we were not.

            * I actually got pretty stumped here for awhile. For what reason would "cat -" not work? 
            * [A quick Google search later...](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)
            * Turns out "cat -" redirects you to *stdin*, meaning the terminal is ready for more input from the user.

    * We will use "cat ./-" as specified by the StackOverflow article. 

After utilizing the command line, the password should be displayed in our terminal.

<details><summary>Password:</summary>
  <pre>
  CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
  </pre>
</details>



## Bandit 2
Our next step, yet again, is to close our current connection with bandit1 and reconnect to OverTheWire through bandit2 (provided by the site).

Once more, the "exit" command is used to disconnect us from bandit1.

We will now need to reconnect using bandit2 - **The following command line was used to access OverTheWire:**

* ssh [bandit2@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit3.html) -p 2220

Utilizing the password gained from "-" in the last level, we gain access to level 2!

This level seems unique in the sense that the file we are looking for is multiple words (including white spaces).

**For now, we use the following commands to get where we want to go:**

* ls

    * We will always need to utilize this command while dealing with a directory, as this is how we see what files are in the current home directory.

* cat

    * We will always need "cat" as well, as its our way of retrieving the passwords we need.
    * "cat spaces in this filename"

        * **RECORD SCRATCH SFX**
        * "What do you mean that doesn't work?" - Me
        * The solution surprisingly did not come from a google search, but rather a lightbulb moment! 

            * When dealing with multiple word file names, you must encase the file name within ''.
            * In terms of syntax, we basically just asked to concatenate "cat spaces" with a bunch of other garbage behind it that will not be recognized.
            * Seeing as "spaces" is *not* the name of the file, of course it wouldn't work.

    * ~~"cat spaces in this filename"~~ "cat 'spaces in this filename'"

Utilizing that command line, we will be given our password.

<details><summary>Password:</summary>
  <pre>
  UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
  </pre>
</details>

        
## Bandit 3
Disconnect and reconnect time!

What do you do when you wanna leave somewhere? "Exit" (command)

Get back in there soldier - **The following command line was used to access OverTheWire:**

* ssh [bandit3@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit4.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

In this level the catch seems to be that our file, containing the password, is hidden in the "inhere" directory.

**Let's try it out:**

* ls
    * Okay, the "inhere" directory comes up!

* cd
    * This command is used to change the working directory!
        * [Manual](https://man7.org/linux/man-pages/man1/cd.1p.html)
    * We must use "cd" in this case because the file we are looking for is in a different directory (i.e. not the home directory).
    * Be careful, as syntax requires you to add "/" after the directory name in order to clarify that it is indeed a directory.
    * The command line to input is: "cd inhere/"

* ls (again?)
    * Yes! ls again.
    * Why?
        * Well, now that we have successfully changed directories, we must now be made aware of the files in this directory.
    * Lets try it out:
        * "Okay this doesn't work either..." - also me
        * Well, the file **is** hidden...
            * Per the manual, adding "-a" after an ls will allow you to see ALL of the files; even the hidden ones!
    * The full command should look like this: "ls -a" (assuming we are INSIDE of the "inhere" directory).

* cat
    * After the "ls -a" command, we can see that there is a file named ".hidden".
    * This is what we were looking for!
    * The full command should look like this: "cat .hidden"
        * We do not need to change the syntax in this case, as "." is a valid character that is recognizable.

Assuming everything went alright, we should now have the password in our terminal.

<details><summary>Password:</summary>
  <pre>
  pIwrPrtPN36QITSp3EQaw936yaFoFgAB
  </pre>
</details>


## Bandit 4
It is time once again to disconnect and reconnect.

We use our exit command to disconnect.

**The following command line was used to access OverTheWire:**

* ssh [bandit4@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit5.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

* Side note: feel free to use the "reset" command if your terminal is getting messy! This information was provided on the OverTheWire website linked above.

Level 4, huh? It would seem that our password is in the inhere directory!

There is a catch however; the file our password is in is the only human-readable file in the directory...

**Well, let's get started:**

* ls
    * This should be inferred going forward; we will always need to use our ls command to see whats in our directory.
    * All right, our "inhere" comes up!

* cd
    * We will need inside of "inhere", so we use our cd command.
    * "cd inhere/"

* ls (part 2)
    * Okay, thats a couple of files...
        * Let's try and concatenate the first one on the list:
            * Okay, I can't read that.
            * I got stuck here for some time, as it would be inefficient to sift through all of the files manually looking for the one I can read.
                * As it would turn out, the rest of the files are in binary!
                * All is saved, though! I found something that should help with a quick search.

* for x in {range}
    * HUH?
    * Well, [An article on RedHat](https://www.redhat.com/sysadmin/bash-scripting-loops) suggested that it may be easier to do this with a loop!
        * Think of this like a "for loop" in our high-level programming languages (c/c++, python, etc)
            * High level programming languages are those closest to human language.
    * **The command line should look like this:** for x in {0..9}; do file ./-file0$x; done
        * for x in {0..9}; do file ./-file0$x; done
            * As we saw when we used the ls command inside "inhere", the files are named "-file0$" sequentially from 00-09.
                * This allows us to iterate through the files in order.
            * the command "file" assimilated into this loop will allow us to receieve information about any of the files used as parameters!
                * However, the use of this command makes it so that we must include the "./" infront due to "-" beginning the file name.
    * Following this command, we should see that -file07 is the one that contains ASCII text!
        * We can also see that the data type for the rest of the files is "data".

* cat
    * Probably the most simple part of this level!
    * "cat ./-file07" 
        * Remember what we have to do when a file name is lead by a "-"!

So long as everything went alright, we now have our next password in our terminal.

<details><summary>Password:</summary>
  <pre>
  koReBOKuIDDepwhWk7jZC0RTdopnAYKh
  </pre>
</details>


## Bandit 5
Guess what? Disconnect again :)

Exit command to disconnect.

**The following command line was used to access OverTheWire:**

* ssh [bandit5@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit6.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

For level 5, we're given a little more criteria for our file containing the password:

1. human-readable
2. 1033 bytes in size
3. not executable

**Time to get to it:**

* ls
    * To find our "inhere" directory!

* cd
    * We need in there, badly!
    * "cd inhere/"
        * Don't forget syntax requirements!

* ls
    * 20 folders, huh? Seems a little excessive if you ask me...
        * All jokes aside, let's see what inside of the first one.
            * We can see that each of the folders have multiple files.
        * It would be inefficient to go through each of the folders and files to look for a single file that meets our criteria.

* find
    * WOAH new command alert!
    * [Manual](https://man7.org/linux/man-pages/man1/find.1.html)
        * Going through the manual for the find command, we see that there are ways for us to search based on criteria.
            * -size n
                * This distinction allows for us to search based on n units of space.
                * We will be using 'c' for bytes, as thats the size / space identifier given to us as criteria.
            * -type c
                * This distinction allows for us to search based on whether a file is of type "c".
                * We will be using 'f' for regular file
            * -executable 
                * This distinction allows for us to search based on whether a file is executable or not.
                * We will be using '! -executable', since our criteria states that our file is NOT executable.
                    * **Reminder:** the '!' operator means "not".
    * The command line should look like this:
        * find -type f -size 1033c ! -executable

* cat
    * Now, after inputting this command line, we should see that "./maybehere07/.file2" - this is the location of the file with our password.
    * "cat ./maybehere/.file2" 

Considering all went well, we can now see the password in our terminal.

<details><summary>Password:</summary>
  <pre>
  DXjZPULLxYr17uwoI01bNLQbtFemEgo7
  </pre>
</details>


## Bandit 6
Hey, you! Yes, you. What's the opposite of connecting?

<details><summary>Answer:</summary>
  <pre>
  Disconnecting - just as you should use the exit command now!
  </pre>
</details>

**The following command line was used to access OverTheWire:**

* ssh [bandit6@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit7.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

We've come to level 6 now! Just a few more to go.

Looks like we have some criteria to follow again:

1. owned by user bandit7
2. owned by group bandit6
3. 33 bytes in size

**With that, we can now start the level:**

* find
    * Woah there! Didn't you say we'd always need to use the ls command first?!
        * Yes, BUT I wanted to try and see if find would work from any directory.
        * Turns out, you can!
    * We should use the [Manual](https://man7.org/linux/man-pages/man1/find.1.html) again.
        * /
            * We will utilize the "/" operator in order to distinguish that we would like to start from the root folder.
        * -user bandit7
            * We will utilize "-user bandit7" because this allows for the distinction of the USER owner of the file.
        * -group bandit6
            * We will utilize "-group bandit6" because this allows for the distinction of the GROUP owner of the file.
        * -size c
            * Just as in level 5, we have a size description of the file we are looking for
            * Again, we will be utilizing "-size 33c" in order to distinguish that we are looking for a file whose size is 33 bytes.
    * The full command line should look like this:
        * find / -user bandit7 -group bandit6 -size 33c
    * With the find command line having been input, we should now have the directory and name of the file on our terminal.
        * "/var/lib/dpkg/info/bandit7.password"

* cat
    * Just as the sun rises and sets, we too have our own certainties - concatenating for our password!
    * "cat /var/lib/dpkg/info/bandit7.password"

If you entered that correctly, you should now have the next password on your terminal.

<details><summary>Password:</summary>
  <pre>
  HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
  </pre>
</details>


## Bandit 7
Hey... I know I've said it a lot, but I am going to have to ask you to disconnect once more using that exit command.

**The following command line was used to access OverTheWire:**

* ssh [bandit7@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit8.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

Coming to level 7, the only information we are given is that the password is strored in the file "data.txt" next to the word "millionth".

Does not seem too hard upon first glance, but we will hold our reservations until later!

**Here we go!**
* ls
    * Yes, we are back to using ls as our first command.
    * Since the level tells us what the file is called, we simply need to see if it is in our current directory.
    * Trying to read the file as is = stinky, we need to find a way to do this.

* grep
    * New command line DLC just dropped
        * [Manual](https://man7.org/linux/man-pages/man1/grep.1.html)
        * As stated in the manual, the grep command lets us see lines that match patterns.
        * Our "pattern" just so happens to be the information they gave us for the level!
    * When combined with the "cat" command, we are able to pinpoint the line in which the word "millionth" occurs.

* cat
    * Now all we have to do is combine our cat and grep commands.
        * Important piece of information: the commands MUST be separated by the "|" operator for syntax reasons.
        * The command line should look like this:
            * "cat data.txt | grep millionth"

If done correctly, we should now see the string associated with the word "millionth", which happens to be our password.

<details><summary>Password:</summary>
  <pre>
  cvX2JJa4CFALtqS87jk27qwqGhBM9plV
  </pre>
</details>     


## Bandit 8
You only have to disconnect two more times after this! I am still going to need you to do that now, using the exit command, though.

**The following command line was used to access OverTheWire:**

* ssh [bandit8@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit9.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

For level 8, we are told that our password is stored in data.txt and that our password is the only line of text that occurs only once.

**Seems to be a UNIQ situation (ba dum tss)... No? We'll just get into it then:**

* ls
    * As stated previously, ls will *most likely* be your first move.
    * We need to see if "data.txt" is in our current directory, right?

* sort
    * New commmand
    * I was actually pretty stuck on this one. I didn't take me long to realize that I couldn't just use the same as level 7.
        * Since there repeats, its pointless to search that way.
    * Found help on [This site](https://www.liamdelahunty.com/tips/linux_remove_duplicate_lines_with_uniq.php)
    * Per the website sort will sort the file, while uniq will list unique data.

* uniq
    * New command
    * Assimilated / piped into the same command line as sort, as it lets us distinguish between UNIQUE lines and reoccuring ones.
        * Sounds perfect for what we're looking for!
        * uniq -u
            * We will utilize "uniq -u", as this is the identifer for listing only unique LINES.
    * The command line should look as follows:
        * "sort data.text | uniq -u"

Since our password was the only unique line in the file, inputting the command should allow you access to the next password.

<details><summary>Password:</summary>
  <pre>
  UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
  </pre>
</details>


## Bandit 9
Only one more disconnect after this one... That doesn't mean you can slack now! 

I'll wait. Just continue with the document once you've disconnected.

**The following command line was used to access OverTheWire:**

* ssh [bandit9@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit10.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

For level 9, we are told that the password is stored in data.txt in one of the few human-readable strings and preceeded by several "=" characters.

At first glance, that seems like quite a search. However, I believe we have used everything we will need in this level already.

**Let's see if that checks out:**

* ls
    * Great, data.txt shows up when using our ls command. We do not need cd as the file is in our directory.
    * Our next step will jump straight to the point, as I believe they gave us the key in the description of the level.

* cat / grep
    * In order to read specifc lines from the file, we need to have more criteria to use in the command.
    * We will utilize "strings" as criteria for the command line.
        * This is because our password is part of one of few human-readable **strings**.
    * The next step would be to utilize the grep command for the lines that start with "=".
        * We do this because the string our password is in is also preceeded by "=" characters. 
    * The command line should look as follows:
        * "cat data.txt | strings | grep ="

If everything went as planned, we should see multiple lines with the "=" characters in our terminal.

You should notice something immediately; the lines are directing you to the password!

Though not directly POINTING the lines spell out "the Password is", followed by our password.

<details><summary>Password:</summary>
  <pre>
  truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
  </pre>
</details>


## Bandit 10
Woo-hoo! The last time you're require to disconnect and reconnect!

Once you've disconnected with the exit command, we can begin our last level covered by this write-up.

**The following command line was used to access OverTheWire:**

* ssh [bandit10@bandit.labs.overthewire.org](https://overthewire.org/wargames/bandit/bandit11.html) -p 2220

* CTRL+SHIFT+C -> CTRL+SHIFT+V (put the password in)!

The last level we will be covering is level 10.

Our information for this level is as follows:

1. The password is stored in data.txt
2. data.txt contains base64 encoded data

Initially, I thought this level would be a lot harder than it turned out to be. I could almost guarantee a new command before even starting it.

**No more wasting time, the end is nigh!**

* ls
    * As expected, our last level begins with our ls command.
    * As "data.txt" appears, we know we are in the correct directory!

* cat
    * Pretty obvious, right?
    * We will definitely be needing the cat command, as we need to know whats inside of the file.

* decode
    * New command!
    * Found help on [this site](https://ioflood.com/blog/base64-linux-command/#:~:text=To%20encode%20data%20in%20Linux,making%20it%20safe%20for%20transmission.&text=In%20this%20example%2C%20we%27re,string%20to%20the%20base64%20command.)
        * "-d" or "--decode" will decode the base64 encoded data that it is passed.
    * The command line should look as follows:
        * "cat data.txt | base64 --decode"

With the command line input, we should be able to see "The password is..." on our terminal.

With this password collected, we have successfully completed levels 0 - 10 of OverTheWire's Bandit wargame.

<details><summary>Password:</summary>
  <pre>
  IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
  </pre>
</details>


## Conclusion
My experience with the first 10 levels of the Bandit wargame was exceptionally positive. I have a small amount of ssh knowledge from previous classes, but this assignment has done wonders for my understanding of the subject. Though I struggled at times, the activity is engaging enough to where it never really felt as if I was doing an assignment. I feel as if I have a much better understanding of what this class is supposed to be about through this assignment as well. I took the liberty of trying to incorporate humor into this write-up to engage the reader and show that these types of things can truly be enjoyable!

Pictures would have been a great addition to this write-up, but my own procrastination issues got in the way of that.

Through this assignment, I am sure to continue with OverTheWire's Bandit wargame. I feel as if I am more inclined to do so after gaining the knowledge this activity had to offer - it has made me feel as if cybersecurity is something I could actually do.