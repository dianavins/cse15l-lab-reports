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
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cd lecture1/messages/
   ```
   **Output:** `cd: messages/: No such file or directory`
   This output occured because `cd` with an argument changes your current directory to that of the argument and then outputs the current directory, which in our case becomes `example_directory1`. There is no error in the output.
3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cd lecture1/en-us.txt
   ```
   **Output:** `cd: lecture1/en-us.txt: No such file or directory'
`
   This output occured because cd with an argument changes your current directory to that of the argument and then outputs the current directory, which in our case becomes 'example_file.txt'. There is no error in the output.
## `ls`
1. an example of using the command with no arguments.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   ls 
   ```
   **Output:** `Hello.class  Hello.java  messages/  README`
   This output occured because `ls` outputs the files and folders held in our current directory, which in our case is `exmple_directory1 example_directory2`. There is no error in the output.
2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   ls messages/
   ```
   **Output:** `de-code.txt  en-us.txt  es-mx.txt  zh-cn.txt`
   This output occured because `ls` outputs the files and folders held in our current directory, which in our case is `example_file1.txt examplefile2.txt`. There is no error in the output.
3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   ls README
   ```
   **Output:** `README`
   This output occured because `cd` outputs the current directory, which in our case is `home`. There is no error in the output.
## 'cat'
1. an example of using the command with no arguments.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cat
   ```
   **Output:** waits for user input.
   This output occurs because Without a file as an argument, `cat` waits for input from standard input (keyboard)
2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cat /home/example_directory1
   ```
   **Output:** `cat: workspace/lab: Is a directory`
   This output occured because `cat` can't be used on directories, thereby causing an error.
3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cat /home/example_directory1/example_file.txt
   ```
   **Output:**
```
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);
    System.out.println(content);
  }
}
```
   This output occured because `cat` displays the contents of the file given.
