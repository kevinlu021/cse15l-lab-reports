# Lab Report 4 - Vim

*Steps 1-3 have already been completed.*

# 4. Log into ieng6
![Step 4](./Images/step4.png)

Keystrokes:
- `ssh cs15lsp23cp@ieng6.ucsd.edu <enter>` Remotely connect to your course specific CSE15L account.

# 5. Clone your fork of the repository from your Github account

![Step 5](./Images/step5.png)

Keystrokes:
- `git clone git@github.com:kevinlu021/lab7.git <enter>` After authenticating a SSH key for GitHub, we clone a forked repository of lab 7 to our ieng6 account.

# 6. Run the tests, demonstrating that they fail

![Step 6](./Images/step6.png)

Keystrokes:
- `ls` Check to make sure the `lab 7` repository was successfully cloned
- `javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java` This command compiles all the Java files in the current directory while including the Hamcrest and JUnit libraries in the classpath.
- `java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests` Run the tester file ListExamplesTests.java


