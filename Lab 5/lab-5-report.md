# Lab 5 Report
## Original Post


What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?

> I am on my personal MacBook. I opened and cloned Lab 3 repository via Github Desktop and am editing the code in Visual Studio Code.



Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.

> Here is what my symptom looks like:

![error](./Images/error.png)

> Because `input1` is an array of size 1, reversing it should effectively do nothing — the output should be the same array. However, not only does my test fail when I use assertArrayEquals, but it seems there is an IllegalArgumentException error.


Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.

> My code for the JUnit tests is as follows:
```
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
  ``` 
  > My reverseInPlace code is as follows:
  ```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  ```
  > And, as you can see in my previous screenshot, I ran the two following commands
  > `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`
  > `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests.java`

## TA Response

> wsg gang, <br>
>   I would recommend double checking your terminal commands. Just a hint, when you run the `java` command and feed in <file name>, the computer will search for the file <file name>.class, so in this case it would search for "ArrayTests.java.class". Notice anything wrong? \*rawr\* <br>

> Additionally, I would recommend running tests on more rigorous examples. If you're reversing an array, it would be a good idea to test a longer array, of length 2 or possibly greater, to see if the behavior still matches what you expect. You currently are only testing edge cases which is good, but not enough! 
> Hope that helps ;)
  


