# Lab Report 5
---
# Part 1 - Debugging Scenario

---
**Student Post Title:** Issues with grade.sh -- Not grading despite correct calculation syntax
I wrote my grade.sh to calculate the grade based on (total number of tests - number of failed tests) / total number of tests. The calculation is in `GRADE='100 - (($FAILS / $NUMTESTS))*100)'` (In this post, I replaced the backticks in the code with ' so that markdown wouldn't read them as backticks for a code block) but it gives me output `grade.sh: command substitution: line 46: syntax error near unexpected token '('`. What do I do?
Here is the code:
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

# step 1: clone the student's repo

git clone $1 student-submission
echo 'Finished cloning'

# step 2 check that the student code contains ListExamples.java

if [[ -f student-submission/ListExamples.java ]]; then
    echo "File Existed"
else
    echo "ListExamples.java does not exist"
    echo "Grade: 0"
    exit 1
fi

# step 3: put all relevant files in the grading-area directory
# ListExamples.java, TestListExamples.java, lib directory

cp student-submission/ListExamples.java TestListExamples.java grading-area
cp -r lib grading-area

# step 4: Compile tha java files and check that they compiled successfully
cd grading-area
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" ListExamples.java TestListExamples.java
echo "This is the exit code of javac: $?"

# step 5: Grade the student's code
touch output.txt
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples > output.txt

tail -n 2 output.txt > output2.txt
LASTLINE=$(head -n 1 output2.txt)
echo "last line: " $LASTLINE

FAILS=$($LASTLINE | cut -d ' ' -f 5)
echo "num fails: " $FAILS
NUMTESTS=$($LASTLINE | cut -d ' ' -f 2)
echo "num tests: " $NUMTESTS
GRADE=$((100 - ($FAILS * 100 / $NUMTESTS)))
echo "Grade: " $GRADE
```
Here is the full output:
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/92e19fda-280f-4b3d-8645-4075dbc37ebb)

---
**TA Response**
Your syntax seems correct, try a different method of defining variables $FAILS and $NUMTESTS. They might not be integer or float values, thereby preventing any arithmetic from being conducted. Try to utilize `awk` for simplicity since it automatically uses spaces as a delimiter.

In the original script, you were trying to use cut to extract fields based on spaces. The main issue was the complexity of the text format you were dealing with:
- The line `Tests run: 5, Failures: 1` contains text with mixed delimiters (spaces and commas).
- `cut -d ' ' -f 5` attempts to split the text by spaces and extract the 5th field. However, this approach is fragile and can fail if the exact spacing or structure of the text changes.
- It failed because `$LASTLINE` was treated as a command substitution, not a string to be processed.
  
---
**Student Response**
Here is my fixed code:
`````
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

# step 1: clone the student's repo

git clone $1 student-submission
echo 'Finished cloning'

# step 2 check that the student code contains ListExamples.java

if [[ -f student-submission/ListExamples.java ]]; then
    echo "File Existed"
else
    echo "ListExamples.java does not exist"
    echo "Grade: 0"
    exit 1
fi

# step 3: put all relevant files in the grading-area directory
# ListExamples.java, TestListExamples.java, lib directory

cp student-submission/ListExamples.java TestListExamples.java grading-area
cp -r lib grading-area

# step 4: Compile the java files and check that they compiled successfully
cd grading-area
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" ListExamples.java TestListExamples.java
echo "This is the exit code of javac: $?"

# step 5: Grade the student's code
touch output.txt
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestListExamples > output.txt

tail -n 2 output.txt > output2.txt
LASTLINE=$(head -n 1 output2.txt)
echo "last line: $LASTLINE"

# Parse the number of tests and failures from the LASTLINE
NUMTESTS=$(echo $LASTLINE | awk '{print $3}' | cut -d',' -f1)
FAILS=$(echo $LASTLINE | awk '{print $5}' | cut -d',' -f1)
echo "num fails: $FAILS"
echo "num tests: $NUMTESTS"

# Calculate the grade
GRADE=$((100 - (FAILS * 100 / NUMTESTS)))
echo "Grade: $GRADE"
`````
And here is the output. It worked, thank you!
![image](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/578f6dc1-92cb-4d90-8567-6d3026518471)
---

## Directory Structure:

`````
.
├── grade.sh
├── GradeServer.java
├── Server.java
├── TestListExample.java
├── lib
│   ├── hamcrest-core-1.3.jar
│   └── junit-4.13.2.jar
├── student-submission
│   └── ListExamples.java
└── grading-area
    ├── IsMoon.class
    ├── ListExamples.java
    ├── TestListExamples.java
    ├── output.txt
    ├── output2.txt
    ├── StringChecker.class
    ├── TestListExamples.class
    ├── TestListExamples.java
    └── lib
        ├── hamcrest-core-1.3.jar
        └── junit-4.13.2.jar
`````

----
# Part 2
Something you learned from your lab experience in the second half of this quarter that you didn't know before were JDB, VIM, bash scripts, and using git commands in the terminal other than git clone. I've never heard of JDB and am still trying to learn it. Interestingly enough, I first encountered VIM at my lab a day or two before it was introduced. I also was unaware that we could write scripts in bash, and began to understand what a "script" means in CS. Lastly, I was used to using GitHub extentions on VSCode rather than using git commands in bash, so it was useful to learn it.
