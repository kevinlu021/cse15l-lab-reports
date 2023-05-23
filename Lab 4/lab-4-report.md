# Lab Report 4 - Vim

*Steps 1-3 have already been completed.*

## 4. Log into ieng6
![Step 4](./Images/step4.png)

Keystrokes:
- `ssh cs15lsp23cp@ieng6.ucsd.edu <enter>` Remotely connect to your course specific CSE15L account.

## 5. Clone your fork of the repository from your Github account

![Step 5](./Images/step5.png)

Keystrokes:
- `git clone git@github.com:kevinlu021/lab7.git <enter>` After authenticating a SSH key for GitHub, we clone a forked repository of lab 7 to our ieng6 account.

## 6. Run the tests, demonstrating that they fail

![Step 6](./Images/step6.png)

Keystrokes:
- `ls <enter>` Check to make sure the `lab 7` repository was successfully cloned
- `javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java <enter>` This command compiles all the Java files in the current directory while including the Hamcrest and JUnit libraries in the classpath
- `java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests <enter>` Run the tester file ListExamplesTests.java
- Note that one test does indeed fail.

## 7. Edit the code file to fix the failing test

![Step 7](./Images/step7.png)

Keystrokes:
- `vim ListExamples.java <enter>` Open up `ListExamples.java` in the Vim editor
- `<shift + g> <enter>` Moves cursor to end of the file
- `<k><k><k><k><k><k><e>` Move cursor up six lines to line with the error, then to the end of the next work, which in this case is "index1"
- `i` Enter insert mode.
- `<right><backspace><2>` Move cursor after the "1" in "index1", delete it, and replace with "2"
- `<esc>` Return to normal mode.
- `:wq` Save and quit the editor.

## 8. Run the tests, demonstrating that they now succeed

![Step 8](./Images/step8.png)
Keystrokes:
- `ls <enter>` Check to make sure the `lab 7` repository was successfully cloned
- `javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java <enter>` This command compiles all the Java files in the current directory while including the Hamcrest and JUnit libraries in the classpath
- `java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests <enter>` Run the tester file ListExamplesTests.java
- Note all tests pass now.

## 9. Commit and push the resulting change to your Github account
![Step 9](./Images/step9_1.png)
![Step 9](./Images/step9_2.png)

- `git add ListExamples.java <enter>` Tells git we want ListExamples.java to be in our next commit.
- `git commit <enter>` Opens up vim editor to enter in our commit message.
- `<shift + g>` Moves cursor to end of the file
- `i` Enter insert mode.
- `committed` enter any message of your choosing, besides an empty one.
- `<esc>` Return to normal mode.
- `:wq` Save and quit the editor.
- `git push git@github.com:kevinlu021/lab7.git <enter>` Pushes changes to ssh link.

![Step 9](./Images/step9_3.png)

Our changes were successful!

