# Custom PRNG in Java

## Class and Method Usage

- **CustomPRNG(long seed, long modulus, long multiplier)**  
  Initializes the PRNG with the given seed, modulus, and multiplier.

- **double nextDouble()**  
  Generates the next pseudo-random number between 0 and 1.

- **double[] generateRandomArray(int size)**  
  Generates an array of pseudo-random numbers of the specified size.

- **private long customFunction(long x, long n)**  
  Internal method implementing the custom function as per the hint:

## Mathematical Details

  The pseudo-random numbers are generated using a **modified Linear Congruential Generator (LCG)** formula with a custom function to improve   randomness.

   ***Linear Congruential Generator (LCG) Formula***

  \[
  X_{n+1} = (a \cdot X_n + c) \mod m
  \]

  Where:
  - \(X_0\) = seed (initial value)
  - \ \(a\) = multiplier
  - \(c\) = increment (we use 1)
  - \(m\) = modulus (large integer)

  This formula generates a sequence of integers \(X_1, X_2, X_3, \dots\) deterministically, but they appear pseudo-random.

  ***Custom Function***

  To introduce slight non-linearity, a custom function is applied to each new value:

  \[
  f(|x|, |n|) = 
  \begin{cases} 
  x \cdot \left(\frac{n}{x} - 1\right) & \text{if } x \cdot \left(\frac{n}{x} - 1\right) \le n \\
  x & \text{otherwise}
  \end{cases}
  \]

  - Here, \(x\) is the current LCG value.
  - \(n\) is the modulus.
  - This function slightly alters the LCG output to reduce regular patterns.

  ***Generating the Final Random Number***

  Finally, the random number is scaled to be between 0 and 1:

  \[
  r = \frac{X'}{m} \quad (0 \le r < 1)
  \]

  Where:
  - \(X'\) = output of the custom function applied to the LCG value
  - \(m\) = modulus

  This gives a pseudo-random floating-point number suitable for general applications.

  ***How to Compile and Run***

    1. For compile the code: javac CustomPRNG.java
    2. For run the code: java CustomPRNG

  
