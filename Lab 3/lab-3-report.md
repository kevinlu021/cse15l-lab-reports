# Lab Report 3 - Commands

## `grep` command

### `-c`: Prints only the number of lines that match the given input
* This command is useful when the contents of the lines are unnecessary.

```
Input: 
kevinmac@Kevins-MacBook-Air technical % grep -c "a" ./biomed/rr74.txt

Output: 
351
```
* This command searches the contents of rr74.txt in the biomed folder and sees how many lines contain "a".
* The output is printed as the total number of lines.

```
Input:
kevinmac@Kevins-MacBook-Air technical % grep -c "ten" ./911report/*.txt

Output:
./911report/chapter-1.txt:38
./911report/chapter-10.txt:12
./911report/chapter-11.txt:53
./911report/chapter-12.txt:64
./911report/chapter-13.1.txt:19
./911report/chapter-13.2.txt:32
./911report/chapter-13.3.txt:20
./911report/chapter-13.4.txt:47
./911report/chapter-13.5.txt:86
./911report/chapter-2.txt:25
./911report/chapter-3.txt:129
./911report/chapter-5.txt:46
./911report/chapter-6.txt:49
./911report/chapter-7.txt:57
./911report/chapter-8.txt:45
./911report/chapter-9.txt:47
./911report/preface.txt:4
```
* Here we can see that if a pattern is provided as an input, `-c` will run individually on every result.
* The command runs through every text file in the 911reports directory and counts how many lines contain "ten".

