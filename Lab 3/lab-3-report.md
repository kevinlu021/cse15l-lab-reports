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

### `-i`: grep runs the given input as case insensitive.

```
Input: 
kevinmac@Kevins-MacBook-Air technical % grep -i "fOuND" ./911report/chapter-9.txt

Output:
companies).111 Firefighters found the stairways they entered intact, lit, and clear
                Tower found a working elevator, which he took to the 16th floor before beginning to
                and found their mere presence to be calming.
                civilians were still on it. In a few instances healthy civilians were found on
            A battalion chief and a ladder company found a working elevator to the 40th floor and
                and found none.
                the NorthTower from the Marriott found a working elevator in a bank at the south end
                on the 78th-floor sky lobby were found by an FDNY company. They were freed from the
                found the full collapse of the South Tower so unfathomable that they radioed back to
```

* The commmand runs through the chapter-9.txt file and searches for any instance of the word "found", regardless of capitalization.
* Note the indents are not a result of any of our doing, but rather simply represent the whitespace from the indents of the original text file.

```
Input:
kevinmac@Kevins-MacBook-Air technical % grep -i -c  "fOuND" ./911report/chapter-9.txt

Output:
9
```
* Note that grep's command line options can be used in conjunction with one another. Here, we search for lines that contain "found" and simply print the count of the number of lines that match.

### `-l`: Display the file names only.

```
Input:
kevinmac@Kevins-MacBook-Air technical % grep -l "extreme" ./911report/*.txt

Output:
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-8.txt
```

* Due to the fact that we are searching if individual files contain key words, using `*` to automatically pass in multiple files, instead of manually typing them out is very useful.

```
Input: 
kevinmac@Kevins-MacBook-Air technical % grep -l -i "hhh" ./*/*.txt

Output:
./biomed/1471-2164-3-18.txt
./biomed/1471-2164-3-8.txt
./biomed/1475-9268-1-1.txt
./plos/pmed.0020103.txt
```
* We were able to search through multiple directories containing thousands of lines to easily find what we were looking for.

### `-n`: Display the matched lines and their line numbers.

* This is a very useful command to find the exact part in a file that matches your key word.

```
Input:
kevinmac@Kevins-MacBook-Air technical % grep -n -i "six weeks before the sep" ./*/*.txt

Output:
./911report/chapter-9.txt:117:            Six weeks before the September 11 attacks, control of the WTC was transferred by net
```

* Note the indents are once again from the original layout of the text file.

```
Input:
kevinmac@Kevins-MacBook-Air technical % grep -n -r "immunohistochemical feat" ./biomed

Output:
./biomed/1471-213X-1-11.txt:206:          show changes in immunohistochemical features.
```

* Note: `-r` allows us to search recursively through a directory and go through all of its files' contents.
* In line 206 of 1471-213X-1-11.txt, the key word was found.

### `-C n`: Prints n lines that come before and after the result.

```
Input:
kevinmac@Kevins-MacBook-Air technical % grep -n -r -C 2 "immunohistochemical feat" ./biomed

Output:
./biomed/1471-213X-1-11.txt-204-          stratified epithelium of ectocervix exhibit
./biomed/1471-213X-1-11.txt-205-          differentiation associated with morphological changes and
./biomed/1471-213X-1-11.txt:206:          show changes in immunohistochemical features.
./biomed/1471-213X-1-11.txt-207-          Interestingly, although lamina propria of ectocervix
./biomed/1471-213X-1-11.txt-208-          showed the presence of primitive (CD14) moderately
```

* This is an add on to the previous command. Grep will take all the matching lines, and print those lines alongside the previous and following 2 lines. In this case, grep only found one matching line, so 5 lines were outputted.

```
Input:
kevinmac@Kevins-MacBook-Air technical % cat ./911report/chapter-13.3.txt | grep -C 1 then

Output:
returning to the United States, Hage was met at the airport by FBI agents,
                interrogated, and called the next day before the federal grand jury then
                investigating Bin Ladin. Because he lied to the grand jury about his association
--
                Bin Ladin family sold UBL's share of the inheritance and, at the direction of the
                Saudi government, placed the money into a specified account then frozen by the Saudi
                government in 1994.
```

* Here, we get the contents of the chapter-13.3.txt file using `cat` and pipe them into the grep command for the key word "then". It finds one match and prints the line before and after that match.
