# Lab Report 2
***

**Part 1** <br>

The bug I chose from Lab1 (ArrayTests.java) is testReverseInPlace():

* A failure-inducing input for the buggy program, as a JUnit test and any associated code:
```
@Test
public void testReversedFailureInducing) {
    int[] input1 = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reverseInPlace(input1));
}
```

* An input that doesn’t induce a failure, as a JUnit test and any associated code:
```
@Test
public void testReversedNotFailureInducing() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reverseInPlace(input1));
}
```
* The symptom, as the output of running the tests:
![Image](Symptom.png)	

* The bug, as the before-and-after code change required to fix it:
    - Before:
      ```
        static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
        }
        return arr;
      }
    - After:
      ```
        static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
            newArray[i] = arr[arr.length - i - 1];
        }
        return newArray;
        }
    - Explanation: The bug in the original reversed method is that it modifies the arr array itself, which should not be changed. To fix it, the code I implemented assigns the reversed elements to the newArray and returns the newArray.
 
**Part 2: ** <br>
Command: -size

**Example 1:** <br>
Command: 
```
find ./technical -type f -size -2k
```
Output:
```
./technical/biomed-sizes.txt
./technical/plos/pmed.0020191.txt
./technical/plos/pmed.0020226.txt
```
<br>

**Example 2:** <br>
Command:
```
find ./technical -type f -size +50k
```

Output:
```
./technical/biomed/1471-2156-3-17.txt
./technical/biomed/1472-684X-1-5.txt
./technical/biomed/gb-2001-2-8-research0030.txt
./technical/biomed/gb-2002-3-5-research0025.txt
./technical/government/Gen_Account_Office/Paper_Walker11-2002_acpro122.txt
```

The first example filters out files less than 5 KB and the second example filters out files greater than 50 KB. This is great for filtering file ranges and excludes files that are too small or big for usage.

