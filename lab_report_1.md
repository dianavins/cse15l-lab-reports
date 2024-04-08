# BASIC FILESYSTEM COMMANDS
## `cd`
1. an example of using the command with no arguments.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cd
   ```
   **Output:** ``
   This output occured because `cd` has no output, since its function is to change directories. There is no error in the output.
2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `/home/`
   ```
   cd /home/example_directory1
   ```
   **Output:** `example_directory1`
   This output occured because `cd` with an argument changes your current directory to that of the argument and then outputs the current directory, which in our case becomes `example_directory1`. There is no error in the output.
3. an example of using the command with a path to a file as an argument.
  **Prior absolute path:** `/home/`
   ```
   cd /home/example_directory1/example_file.txt
   ```
   **Output:** `example_file.txt`
   This output occured because cd with an argument changes your current directory to that of the argument and then outputs the current directory, which in our case becomes 'example_file.txt'. There is no error in the output.
## `ls`
1. an example of using the command with no arguments.
   **Prior absolute path:** `/home/`
   ```
   ls 
   ```
   **Output:** `exmple_directory1 example_directory2`
   This output occured because `ls` outputs the files and folders held in our current directory, which in our case is `exmple_directory1 example_directory2`. There is no error in the output.
2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `/home/`
   ```
   ls /home/example_directory1
   ```
   **Output:** `example_file1.txt examplefile2.txt`
   This output occured because `ls` outputs the files and folders held in our current directory, which in our case is `example_file1.txt examplefile2.txt`. There is no error in the output.
3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `/home/`
   ```
   ls /home/example_directory1/example_file.txt
   ```
   **Output:** `example_file.txt`
   This output occured because `cd` outputs the current directory, which in our case is `home`. There is no error in the output.
## 'cat'
1. an example of using the command with no arguments.
   **Prior absolute path:** `/home/`
   ```
   cat
   ```
   **Output:** waits for user input.
   This output occurs because Without a file as an argument, `cat` waits for input from standard input (keyboard)
2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `/home/`
   ```
   cat /home/example_directory1
   ```
   **Output:** `cat: workspace/lab: Is a directory`
   This output occured because `cat` can't be used on directories, thereby causing an error.
3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `/home/`
   ```
   cat /home/example_directory1/example_file.txt
   ```
   **Output:** displays the contents of `example_file.txt`.
   This output occured because `cat` displays the contents of the file given.
