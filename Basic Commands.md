# Basic Linux Commands

## File & Directory Management

1.  **`ls` (list):** Lists files and directories.
    *   `ls -l` (long listing)
    *   `ls -a` (show hidden files)
    *   `ls -lh` (human-readable sizes)
2.  **`cd` (change directory):** Changes the current directory.
    *   `cd ..` (go up one level)
    *   `cd ~` (go to home directory)
3.  **`pwd` (print working directory):** Shows the current directory's path.
4.  **`mkdir` (make directory):** Creates a new directory.  `mkdir my_directory`
5.  **`rmdir` (remove directory):** Removes an empty directory.
6.  **`rm` (remove):** Removes files or directories.
    *   `rm myfile.txt`
    *   `rm -r my_directory` (recursive removal)
7.  **`cp` (copy):** Copies files or directories.
    *   `cp myfile.txt newfile.txt`
    *   `cp -r my_directory new_directory`
8.  **`mv` (move):** Moves or renames files or directories.
    *   `mv myfile.txt newfile.txt`
    *   `mv myfile.txt my_directory`
9.  **`touch`:** Creates an empty file or updates a file's timestamp. `touch newfile.txt`
10. **`realpath`:** Displays the absolute, canonical pathname. `realpath myfile.txt`

## Viewing & Editing Files

11. **`cat` (concatenate):** Displays the contents of a file. `cat myfile.txt`
12. **`less`:** Views file contents one page at a time (use spacebar to scroll, 'q' to quit). `less myfile.txt`
13. **`head`:** Displays the first few lines of a file. `head -n 10 myfile.txt` (first 10 lines)
14. **`tail`:** Displays the last few lines of a file.
    *   `tail -n 10 myfile.txt` (last 10 lines)
    *   `tail -f myfile.txt` (follow file changes)
15. **`nano` or `vi/vim`:** Text editors for creating and editing files. `nano myfile.txt`
16. **`code`:** Opens a file or directory in VS Code (if installed). `code myfile.txt`, `code .` (current directory)

## Searching

17. **`grep` (global regular expression print):** Searches for patterns in text. `grep "keyword" myfile.txt`
18. **`find`:** Searches for files and directories based on various criteria. `find . -name "myfile.txt"`

## Permissions

19. **`chmod` (change mode):** Changes file permissions. `chmod 755 myfile.txt` (755 is a common permission setting).

## Other Useful Commands

20. **`man` (manual):** Displays the manual page for a command. `man ls`
21. **`diff`:** Compares files line by line. `diff file1.txt file2.txt`
22. **`wc` (word count):** Counts lines, words, and bytes in a file. `wc myfile.txt`

This focused list is now ideal for users primarily concerned with managing files, viewing their contents, and searching. I've also added a couple of other useful commands that fit within this scope: `diff` and `wc`.
