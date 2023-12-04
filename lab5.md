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

---


### TA's Response
**Title:** Re: Exception in PrimeNumberGenerator - Help Needed!

Hello there! Thank you for reaching out. It appears that you've come across an ArrayIndexOutOfBoundsException. 

This occurs when attempting to access an element in an array that does not exist. Let's delve into your generatePrimes method to gain a better understanding. Within your generatePrimes method, you have initialized the primes array with a length of 0. Yet, you are attempting to add elements to it using primes[primes.length] = num;. As the array has a length of 0, this will consistently result in an out-of-bounds error. 

To navigate this issue, consider how you can adjust the array's size dynamically as you collect prime numbers. I have a guiding question for you: How might you resize the array to make space for the prime numbers you discover?

Give it a try and don't hesitate to ask for clarification!

---


### Student's Follow-Up Response
**Title:** Re: Exception in PrimeNumberGenerator - Help Needed!

**Description:**
Thanks for your quick response! I see the issue now. I've modified the generatePrimes method to use an ArrayList to dynamically store the prime numbers.
I've also updated the main method to handle the List<Integer> result. The program runs successfully now, and I'm getting the expected prime numbers. Thanks for your guidance!

**Screenshot of Successful Run:** <br>
![image](https://github.com/gjaroli04/cse15l-lab-reports/assets/146787965/a21612ff-df36-4d87-b5aa-25a172384185)

**Description of Bug:**
The bug in the provided code is an ArrayIndexOutOfBoundsException occurring in the generatePrimes method of the PrimeNumberGenerator Java program. The issue stems from attempting to add elements to an array with an initial length of 0. Specifically, the line primes[primes.length] = num; is causing the exception.

When the array primes is initialized with a length of 0, it has no valid index to store elements. The attempt to access the index primes.length exceeds the bounds of the array, leading to the mentioned exception.The fix involved using an ArrayList to dynamically store the prime numbers and then converting it back to an array for the result.

Thank you for your help!

---

**1. FIle and Directory Structure:** <br>
![image](https://github.com/gjaroli04/cse15l-lab-reports/assets/146787965/b9beee9c-dbea-46f7-8185-01cace349b45)

My directory was named LabReport5, and it had all the files as shown in the above screenshot.

**2. The contents of each file before fixing the bug:** <br>
PrimeNumberGenerator.java:
```
public class PrimeNumberGenerator {
    public static void main(String[] args) {
        int startRange = 0;
        int endRange = 50;

        int[] primeNumbers = generatePrimes(startRange, endRange);

        System.out.println("Prime numbers between " + startRange + " and " + endRange + ":");
        for (int prime : primeNumbers) {
            System.out.print(prime + " ");
        }
    }
    
    public static int[] generatePrimes(int start, int end) {
        int[] primes = new int[0];  // Initialize an empty array

        for (int num = start; num <= end; num++) {
            if (isPrime(num)) {
                primes[primes.length] = num;
            }
        }

        return primes;
    }

    public static boolean isPrime(int number) {
        if (number < 2) {
            return false;
        }

        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                return false;
            }
        }

        return true;
    }
}
```
test.sh:
```
echo "Generating prime numbers from 0 to 50..."
# Function to check if a number is prime
is_prime() {
    number=$1
    if [ $number -lt 2 ]; then
        return 1  # Not prime
    fi
    for ((i = 2; i <= number / 2; i++)); do
        if [ $((number % i)) -eq 0 ]; then
            return 1  # Not prime
        fi
    done
    return 0  # Prime
}

# Generate prime numbers and store them in expected_prime_numbers.txt
for ((num = 0; num <= 50; num++)); do
    if is_prime $num; then
        echo $num >> expected_prime_numbers.txt
    fi
done

echo "Prime numbers generated and stored in expected_prime_numbers.txt."

javac PrimeNumberGenerator.java
java PrimeNumberGenerator > actual_prime_numbers.txt


diff expected_prime_numbers.txt actual_prime_numbers.txt

if [ $? -eq 0 ]; then
    echo "Test passed: The prime numbers match!"
else
    echo "Test failed: The prime numbers do not match."
fi
```

expected_prime_numbers.txt:
```
2
3
5
7
11
13
17
19
23
29
31
37
41
43
47
```

actual_prime_numbers.txt:
```

```

**3.The full command line (or lines) you ran to trigger the bug:**
```
bash test.sh
```

Specifically, inside test.sh this was what command I ran that triggered the bug:
```
javac PrimeNumberGenerator.java
java PrimeNumberGenerator > actual_prime_numbers.txt
```

**4. A description of what to edit to fix the bug**

The bug was fixed by modifying the generatePrimes method to use an ArrayList for storage of prime numbers. The ArrayList allows elements to be added, eliminating the need to specify a fixed size upfront. 
Revised code for generatePrimes:
```
public static List<Integer> generatePrimes(int start, int end) {
    List<Integer> primesList = new ArrayList<>();

    for (int num = start; num <= end; num++) {
        if (isPrime(num)) {
            primesList.add(num);
        }
    }

    // Convert ArrayList to array (if needed)
    return primesList;
}

```

With this modification, the prime numbers are dynamically added to the primesList, and the method returns a List<Integer>. This approach resolves the ArrayIndexOutOfBoundsException issue. There were some changes made to the main method as well by using "List<Integer> primeNumbers = generatePrimes(startRange, endRange);" instead of "int[] primeNumbers = generatePrimes(startRange, endRange);" so we could use Dyanmic ArrayList there as well. Additionally, I also added two more import statements to allow the use of ArrayLists.

