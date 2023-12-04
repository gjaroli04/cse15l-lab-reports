# Lab Report 5
---

## Part 1

### Student's Post:
**Title:** Exception in PrimeNumberGenerator - Help Needed!

**Description:** Hey everyone! I'm working on a Java program (PrimeNumberGenerator.java) to generate prime numbers from 0 to 50, but I'm encountering an exception. I've attached a screenshot showing the symptom. The error message indicates an ArrayIndexOutOfBoundsException. My guess is that there's something wrong with the generatePrimes method. I understand that there is something wrong in array indexation but I am not able to figure it out. Any help in figuring this out would be appreciated!

**Screenshot of Exception:**
![image](https://github.com/gjaroli04/cse15l-lab-reports/assets/146787965/b157a5ac-20fa-469d-9c7d-e307da53abe9)

**Screenshot of generatePrimes:** <br>
![image](https://github.com/gjaroli04/cse15l-lab-reports/assets/146787965/75943901-96f5-4052-9965-a8661a9aa800)

### TA's Response
**Title:** Re: Exception in PrimeNumberGenerator - Help Needed!

Hello there! Thank you for reaching out. It appears that you've come across an ArrayIndexOutOfBoundsException. 

This occurs when attempting to access an element in an array that does not exist. Let's delve into your generatePrimes method to gain a better understanding. Within your generatePrimes method, you have initialized the primes array with a length of 0. Yet, you are attempting to add elements to it using primes[primes.length] = num;. As the array has a length of 0, this will consistently result in an out-of-bounds error. 

To navigate this issue, consider how you can adjust the array's size dynamically as you collect prime numbers. I have a guiding question for you: How might you resize the array to make space for the prime numbers you discover?

Give it a try and don't hesitate to ask for clarification!

