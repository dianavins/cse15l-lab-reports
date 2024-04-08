# BASIC FILESYSTEM COMMANDS
## `cd`
1. an example of using the command with no arguments.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cd
   ```
   **Output:** ``
   This output occured because `cd` has no output, since its function is to change directories. There is no error in the output.
   <img width="1127" alt="cd1" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/5e5c7381-bc9d-4165-8108-da21f3a49cea">

2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cd lecture1/messages/
   ```
   **Output:** `cd: messages/: No such file or directory`
   This output occured because `cd` with an argument changes your current directory to that of the argument and then outputs the current directory, which in our case becomes `example_directory1`. There is no error in the output.
   ![Screenshot 2024-04-08 144147](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/16228216-a844-4953-ae06-048c7e151c5e)

3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cd lecture1/en-us.txt
   ```
   **Output:** `cd: lecture1/en-us.txt: No such file or directory'
`
   This output occured because cd with an argument changes your current directory to that of the argument and then outputs the current directory, which in our case becomes 'example_file.txt'. There is no error in the output.
## `ls`
![Screenshot 2024-04-08 144242](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/4324cce2-369c-41d3-b460-505e6d39e88c)

1. an example of using the command with no arguments.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   ls 
   ```
   **Output:** `Hello.class  Hello.java  messages/  README`
   This output occured because `ls` outputs the files and folders held in our current directory, which in our case is `exmple_directory1 example_directory2`. There is no error in the output.
   <img width="1127" alt="ls1" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/ad1ba745-9eb5-4a30-a2d6-86bc78e1cd39">

2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   ls messages/
   ```
   **Output:** `de-code.txt  en-us.txt  es-mx.txt  zh-cn.txt`
   This output occured because `ls` outputs the files and folders held in our current directory, which in our case is `example_file1.txt examplefile2.txt`. There is no error in the output.
   <img width="1127" alt="ls2" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/4d49a2d8-8ca6-4761-adaf-4378696d0793">

3. an example of using the command with a path to a file as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   ls README
   ```
   **Output:** `README`
   This output occured because `cd` outputs the current directory, which in our case is `home`. There is no error in the output.
<img width="1127" alt="ls3" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/099b27b9-8c31-49b5-975c-db9bf4b11fcb">
   
## 'cat'
1. an example of using the command with no arguments.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cat
   ```
   **Output:** waits for user input.
   This output occurs because Without a file as an argument, `cat` waits for input from standard input (keyboard)
<img width="1127" alt="cat1" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/d612967e-61ad-442d-bdff-5823415d3afe">

2. an example of using the command with a path to a directory as an argument.
   **Prior absolute path:** `PS C:/Users/diana/lecture1 `
   ```
   cat /home/example_directory1
   ```
   **Output:** `cat: workspace/lab: Is a directory`
   This output occured because `cat` can't be used on directories, thereby causing an error.
   <img width="1127" alt="cat2" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/82472bd5-1f5a-4dda-8eda-35d44a29486c">

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
<img width="1127" alt="cat3" src="https://github.com/dianavins/cse15l-lab-reports/assets/64227228/b877b01a-f3ee-4e57-b3d6-8ca6c0aee9af">
