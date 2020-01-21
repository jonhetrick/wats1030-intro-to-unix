# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*
  ```
  ➜  wats1030-intro-to-unix git:(master) pwd 
    /Users/jonleeh/SU_Projects/wats1030-intro-to-unix
  ```
* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*

    ```
    LICENSE                       README.md                     challenge_files               nix_scavenger_hunt.md         nix_scavenger_hunt_stretch.md super_scavengers.md
    ```
* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*

    ```
    total 48
    drwxr-xr-x    9 jonleeh  staff   288B Jan 20 18:22 .
    drwxr-xr-x   15 jonleeh  staff   480B Jan 20 18:22 ..
    drwxr-xr-x   12 jonleeh  staff   384B Jan 20 18:32 .git
    -rw-r--r--    1 jonleeh  staff   1.1K Jan 20 18:22 LICENSE
    -rw-r--r--    1 jonleeh  staff   2.7K Jan 20 18:22 README.md
    drwxr-xr-x  111 jonleeh  staff   3.5K Jan 20 18:22 challenge_files
    -rw-r--r--    1 jonleeh  staff   5.7K Jan 20 18:32 nix_scavenger_hunt.md
    -rw-r--r--    1 jonleeh  staff   319B Jan 20 18:22 nix_scavenger_hunt_stretch.md
    -rw-r--r--    1 jonleeh  staff   255B Jan 20 18:22 super_scavengers.md
    ```
* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://man.he.net/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*

    ```
    -a      Include directory entries whose names begin with a dot (.).
    -l      (The lowercase letter ``ell''.)  List in long format.  (See below.)  A total sum for all the file sizes is output on a line before the long listing.
    -h      When used with the -l option, use unit suffixes: Byte, Kilobyte, Megabyte, Gigabyte, Terabyte and Petabyte in order to reduce the number of digits to three
             or less using base 2 for sizes.
    ```
* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*

    ```
    Applications System       Volumes      cores        etc          opt          sbin         usr
    Library      Users        bin          dev          home         private      tmp          var
    ```

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*

    ```
    /
    ```

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*
    ```
    /Users/jonleeh
    ```
* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*
  * 3
* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*
  * /Users/jonleeh/SU_Projects/wats1030-intro-to-unix
* Press the up arrow on your keyboard. *What just happened?*
  * Shows your previous command that you attempted to run.
* Press the up arrow a few more times. *What do you see?*
  * earlier commands
* Run the `history` command. *What do you see?*
  * history of all commands I have ran.

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*
  * jonleeh
* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*
  * No, just two instances of me jonleeh and jonleeh
* How long has your system been running? Use `uptime` to see, and *paste the result here:*

    ```
    18:50  up 9 days, 38 mins, 2 users, load averages: 2.43 2.09 1.89
    ```

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*
  * From highest CPU useage to lowest I see a snapshot of all processes running on my machine at this time.
* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*
  * TOP is showing me a live view of processes on my machine and along with other important data like swap and memory etc. in regards to those processes. 

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*
  * 2
* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*
  * Last updated: 01-15-2015
* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*

    ```
    ➜  challenge_files git:(master) ✗ find . -name "modi_laboriosam.txt" -print
    ./tmp/modi_laboriosam.txt
    ```

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*
  
    ```
    ➜  challenge_files git:(master) ✗ grep -H WA *.user | wc -l
       2
    ```
* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

    ```
    ➜  challenge_files git:(master) ✗ grep -R Waldo *
    serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt consectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.
    ```

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*
  * All the output from ls command
* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*
  * Gives you a page at a time too look at.
* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*

    ```
    jonleeh          14055   0.0  0.0  4371920   4640   ??  Ss    5:47PM   0:00.07 /System/Library/PrivateFrameworks/FMClient.framework/Versions/A/XPCServices/FMIPClientXPCService.xpc/Contents/MacOS/FMIPClientXPCService
    jonleeh          14034   0.0  0.0  4333656   1616   ??  S     5:47PM   0:00.01 /System/Library/PrivateFrameworks/DeviceCheckInternal.framework/devicecheckd
    jonleeh          14009   0.0  0.0  4416964   7988   ??  S     5:47PM   0:00.04 /usr/libexec/siriknowledged
    jonleeh          13975   0.0  0.1  4451960   9256   ??  S     5:47PM   0:00.27 /usr/libexec/adprivacyd
    jonleeh          13941   0.0  0.1  4516924  15348   ??  S     5:47PM   0:00.40 /System/Library/PrivateFrameworks/AMPLibrary.framework/Versions/A/Support/AMPLibraryAgent --launchd
    jonleeh          13888   0.0  0.1  4459972  18276   ??  S     5:47PM   0:00.72 /usr/libexec/remindd
    jonleeh          13710   0.0  0.0  4395216   3360   ??  S     5:38PM   0:00.03 /usr/libexec/WiFiVelocityAgent
    ```
