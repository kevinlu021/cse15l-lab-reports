# Lab Report 2 - Servers and Bugs
## String Server
To make a web server that can display and take in input strings via query in the URL, the code will look something like this:
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    List<String> list = new ArrayList<>();

    public String handleRequest(URI url) {  
        if (url.getPath().equals("/")) {
            return String.format("Current String list: %s", list.toString());
        } else if (url.getPath().contains("/add")) {
            System.out.println("Path: " + url.getPath());
            String[] parameters = url.getQuery().split("=");
            if(parameters[0].equals("s")){
                list.add(parameters[1]);
                return String.format("String added!");
            }
            return "404 Not Found!";
        } else {
            if(url.getPath().contains("/search")){
                System.out.println("Path: " + url.getPath());
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    List<String> newList = new ArrayList<>();
                    for(String str : list){
                        if(str.contains(parameters[1])){
                            newList.add(str);
                        }
                    }
                    return String.format("Words that contain " + parameters[1] + ": %s", newList.toString());
                }
                
            }
            return "404 Not Found!";
        }
    }
}
class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
# How the website works
![Image](Images/firstAdd.png)
The main method sets up the web server on the desired port, in this case 6969. In the `Handler` class, `HandleRequest` is run which tests the validity of the URL that is passed in. Therefore, the URL in String form is a necessary parameter, and our String `list` is relevant because the value of it will be displayed on the server. If a valid add-message URL is passed in, `list` will be updated by having the query message added on to its current value. In this case, `list` was an empty string and `"Hi there!"` was added onto it. 
&nbsp;  
&nbsp;  
![Image](Images/secondAdd.png)
Like the previous image, the main method sets up the web server on the desired port, in this case 6969. In the `Handler` class, `HandleRequest` is run which tests the validity of the URL that is passed in. Therefore, the URL in String form is a necessary parameter, and our String `list` is relevant because the value of it will be displayed on the server. If a valid add-message URL is passed in, `list` will be updated by having the query message added on to its current value. In this case, `list` had the value `"Hi there!"` and `"I am in CSE15L"` was added onto it. 
&nbsp;  
&nbsp;  
## Lab 3 Bug
Here is an example of a faulty reverse array method: 
```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
&nbsp;  
&nbsp;  
One example of a simple but faulty input would be `[1, 2, 3]`. We expect the array after the change to be `[3, 2, 1]`. However, the JUnit test says otherwise. 
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
	}
```
&nbsp;  

```
JUnit version 4.13.2
.E
Time: 0.019
There was 1 failure:
1) testReverseInPlace(ArrayTests)
arrays first differed at element [0]; expected:<3> but was:<1>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace(ArrayTests.java:9)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<1>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 1,  Failures: 1
```

This doesn't mean that all inputs fail, however. An example would be the array `[1]`. We expect the array after the change to be `[1]`. The JUnit test supports this. 
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1 }, input1);
	}
```
&nbsp;  
```
JUnit version 4.13.2
.
Time: 0.012

OK (1 test)
```
As we can see, the symptom seems to be that with some select input cases, the array doesn't match up starting at the very first element. Looking more carefully, the first element of the array should be the previous last element, but it appears that nothing has actually changed. A close inspection at our for loop can resolve the bug. It seenms we have some logic errors. We want to swap the 0th index with the last index, 1st index with the second last, etc.. Thus, we should create a temp variable to store the value while we swap, so the swapped value isn't lost during the operation. Additionally, we don't want to double swap as that would be redundant and turn the array back to its original state. Thus, we should also only loop until arr.length/2. 
Before:
```
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```

## What I Learned
I learned how to use JUnit. It's very useful for testing individual functions to make sure that the outputs are what you expect - a great tool for debugging. 
