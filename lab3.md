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


