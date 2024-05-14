# Vim usage example: Lab 7
## 1. Log into ieng6
Keyboard input:
`ssh<SPACE>dvins@ieng6-201.ucsd.edu<ENTER>`
`<passphrase for key><ENTER>`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/22388e33-891f-4661-b0bd-d7204d7491c1)

##2. Clone your fork of the repository from your Github account (using the SSH URL)
`git<SPACE>clone<SPACE><CTRL><C>`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/aae7e682-4356-4265-8768-fe8d3d462423)
I then entered the repository folder:
`cd<SPACE>l<TAB>`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/e7b5153a-43ad-40e2-85c8-9f4e8af78948)

## 3. Run the tests, demonstrating that they fail
I copy and pasted the compiling and running code for java and junit files from Lab 4's instructions:
First copy: javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
`<CTRL><C><ENTER>`
Second copy: java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore
`<CTRL><C><SPACE>L<TAB>Tests`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/b032d8ee-5cfa-437a-a06e-f0719ef34dab)

## 4. Edit the code file to fix the failing test
I entered ListExamples.java using vim:
`vim<SPACE>L<TAB>.java<ENTER>` to enter the file
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/dda534c8-5350-4ba7-903a-350470b89f15)
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/5fffb86c-2d18-4a3a-ba69-bf3fb6692e2e)

`43j` to move the cursor to the line with the error
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/513bc334-be79-48c9-a62c-c3465f01f12d)

`1e` to move the cursor to the end of the first word (index2), so the cursor is now over "2"
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/91935e6b-c1a0-47fb-9184-f20c2c6d3698)

`i` to enter insert mode
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/3971623f-cb0c-4b6a-970a-ca4a60541b6f)
(you can see that you're in insert mode by the "-- INSERT --" in the lower left-hand quarter)

`<Del>1` to delete 1 and replace it with 2
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/dcb22616-cf4f-464f-a4f9-9ce594857cd5)

`<Esc>` to exit insert mode
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/884eb939-8107-46f0-99ae-c5cc0f5f3ece)
(you can see that you're not in insert mode by the lack of "-- INSERT --" in the lower left-hand quarter)

`:wq<ENTER>` to save the edits, exit the file and return to terminal
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/6cdcc99d-bcde-4243-bdf5-7ce7e921e40d)
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/3cfd752e-9492-4c66-b3b9-35492694b1d7)

## 5. Run the tests, demonstrating that they now succeed
In the command line, I used the up arrows to reach the previously used `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` to compile and then `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` to run the tests.
`<UP><UP><UP><ENTER>` to run the javac command
`<UP><UP><UP><ENTER>` to run the test file command
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/7a2d5906-8a8b-460b-9b12-aed5e8bbd724)

## 6. Commit and push the resulting change to your Github account (you can pick any commit message!)
To add the changed file to the commit:
`git<SPACE>add<SPACE>L<TAB>.java`
To create a commit and message:
`git<SPACE>com<TAB><ENTER>`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/dbe9b1f5-c901-4930-8eca-ad113032136b)
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/c605a813-f00b-4a8d-8ea4-4184b7b68781)

Scroll down below changes to be committed:
`12j`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/563fea90-deb6-456e-a5f0-b1a599e582ef)

Enter insert mode:
`i`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/250171ff-5df5-46e5-8b95-ca29883cbd71)

Enter message:
`<Del>fixed<SPACE>bug`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/17fa5c23-98c4-4f26-83c3-196153586dc2)

To escape insert mode:
`Esc`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/daa60654-4c9d-4b1b-af96-5f5585268bef)

To save file and exit:
`:wq<ENTER>`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/0f87632a-3416-4041-b0a4-8244719e1c8c)
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/13a3d163-3ef7-432e-9df5-3e94a18e4089)

Push the commit to Github:
`git<SPACE>push<ENTER>`
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/890ed14e-6078-4c31-b82d-4522df107886)
