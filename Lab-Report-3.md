# Part 1 - Bugs
## Failure Inducing Input
```
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3, 4, 5, 6, 7};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 7,6,5,4,3 }, input1);
	}
}
```
## Non-Failure Inducing Input
```
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
}
```
## Symptom
![Symptom](https://github.com/dianavins/cse15l-lab-reports/assets/64227228/904a06b2-2685-497f-9748-7512e80e2ca9)

## The Bug
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

}
```
Fixed code:
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for (int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[i];
    }
  }
}
```
The original code would iterate through a changing array which caused the bug: it would change the first half of the array and then refer to the first half of the array to create the second half, which made a mirrored array. This fixes it by creating a new array to put the output into and then making the original array equal to this template/new array.

# Part 2 - Researching Commands: grep
1. Recursive Search (-r or --recursive):
This recursively searches all files in a directory or a pattern.
ex. 1
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -r "doctor" technical/biomed/
technical/biomed/1471-2156-4-10.txt:        Cynthia Coffman is the post-doctoral associate who
technical/biomed/1471-230X-1-6.txt:        effects (Figure 1) is striking and indicates that doctors'
technical/biomed/1471-2334-3-11.txt:        primary care doctors within one week for failure to
...
```
ex.2
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -r "doctor" technical/911/
grep: technical/911/: No such file or directory
```
2. Invert Match (-v or --invert-match):
This returns all lines of a file that don't match a pattern.
ex. 1
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -v "and" technical/biomed/1468-6708-3-1.txt
        Introduction
        Older adults are frequently counseled to lose weight,
        even though there is little evidence that overweight is
        associated with increased mortality in those over age 65.
...
```
ex. 2
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -v "and" technical/biomed/1468-6708-3-3.txt
        The problem
        unequivocally demonstrated that 3-Hydroxy-3-methylgluatryl
        coenzyme A (HMG CoA) reductase inhibitors (statins) reduce
        disease. These trials found that when compared with
...
```
3. Line Number (-n or --line-number):
This returns the line number of the line that contains the pattern in the file.
ex. 1
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -n "and" technical/biomed/1468-6708-3-1.txt
11:        between body mass index (BMI) and mortality, controlling
19:        gradual weight gain is normative and associated with the
21:        weight standards be adjusted upwards for age [ 8 ] . Such
...
```
ex. 2
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -n "and" technical/biomed/1468-6708-3-3.txt
6:        Three published [ 1 2 3 ] and one recently presented [ 4
7:        ] randomized placebo-controlled clinical trial have
10:        the morbidity and mortality associated with coronary
...
```
7. Context Control: Before, After, and Around (-B, -A, -C):
This returns the lines in the file inbetween
ex. 1
Show 2 lines before a match:
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -B 2 "and" technical/biomed/1468-6708-3-1.txt
        non-smoking older adults have investigated the association
        between body mass index (BMI) and mortality, controlling
--
        Many healthy older adults report gradual weight gain
        throughout adult life. It may be that a small amount of
--
...
```
ex. 2
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -B 2 "and" technical/biomed/1468-6708-3-3.txt
        coenzyme A (HMG CoA) reductase inhibitors (statins) reduce
        the morbidity and mortality associated with coronary
--
        placebo, statins significantly reduced the incidence of
        death, myocardial infarction, unstable angina, percutaneous
--
...
```
Show 3 lines after a match: 
ex. 1
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -A 3 "and" technical/biomed/1468-6708-3-1.txt
        between body mass index (BMI) and mortality, controlling
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
        excess risk for persons with very low BMI, but that persons
        with moderately high BMI had little or no extra risk except
--
        gradual weight gain is normative and associated with the
        most robust health as we age. It has been suggested that
...
```
ex. 2
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -A 3 "and" technical/biomed/1468-6708-3-3.txt
        persons with
        stable coronary disease. Because
        patients who had experienced an acute coronary syndrome
--
        myocardial infarction and randomized them to 16 weeks of
        atorvastatin 80 mg or placebo once daily [ 5 ] . The majorr
...
```
Show 2 lines before and after a match: 
ex. 1
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -C 2 "and" technical/biomed/1468-6708-3-1.txt
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
        excess risk for persons with very low BMI, but that persons
--
        Many healthy older adults report gradual weight gain
        throughout adult life. It may be that a small amount of
--
...
```
ex. 2
```
diana@DESKTOP-R6R97UU MINGW64 ~/docsearch (main) $ grep -C 2 "and" technical/biomed/1468-6708-3-3.txt
        persons with
        stable coronary disease. Because
--
        MIRACL enrolled 3,086 patients within 24-96 hours (mean
        63 hours) of admission for unstable angina or a non-Q-wave
--
...
```
# Citations
Part 2 commands are from ChatGPT. 
Prompt: 
"what are 4 interesting command-line options of alternative ways to use grep?" 
Output: 
"
The grep command is an incredibly powerful tool used in UNIX and Linux environments for searching plain-text data sets for lines that match a regular expression. Here are four interesting command-line options that show some of the alternative ways to use grep:
Recursive Search (-r or --recursive):
This option allows grep to read all files under each directory, recursively. This is particularly useful when you are trying to find occurrences of a string or pattern within files located in a directory and all of its subdirectories.
Example: 
grep -r "search_pattern" /path/to/directory
Invert Match (-v or --invert-match):
Using this option, grep will return all lines that do not match the specified pattern. This is useful for filtering out lines that contain certain words or patterns.
Example: grep -v "exclude_pattern" filename
Line Number (-n or --line-number):
This option causes grep to output the line number in the file before each matching line. This can be very helpful when you need to know not just if a pattern exists in a file, but where it is located.
Example: grep -n "pattern" filename
Context Control: Before, After, and Around (-B, -A, -C):
These options are used to display additional context around the lines that match the pattern. Specifically, -B (before), -A (after), and -C (context) control the number of lines before, after, and around the matched lines, respectively.
Examples:
Show 2 lines before a match: grep -B 2 "pattern" filename
Show 3 lines after a match: grep -A 3 "pattern" filename
Show 2 lines before and after a match: grep -C 2 "pattern" filename
These options can significantly enhance your ability to search and analyze files on the command line, making grep not only a tool for simple searches but also a powerful tool for complex data analysis and troubleshooting.
" 
I copied the four headings and their corresponding example templates and omitted the rest of ChatGPT's output.

