# Java Radix Sort

This project was developed to strengthen my understanding of non-comparative sorting algorithms in Java. It implements Least Significant Digit (LSD) Radix Sort to arrange an array of non-negative `Integer` objects in ascending order.

The program sorts the array one digit position at a time using a stable Counting Sort operation. It displays the state of the array after each pass and pauses so the user can observe how the algorithm progresses.

## Features

- Implements Radix Sort without using built-in sorting methods
- Sorts an array of non-negative `Integer` objects
- Uses stable Counting Sort for each digit position
- Processes the units, tens, and hundreds digits
- Displays the original array
- Displays the array after every sorting pass
- Pauses between passes for step-by-step observation
- Displays the final sorted array
- Separates the algorithm from the test program

## Concepts Demonstrated

- Radix Sort
- Least Significant Digit (LSD) sorting
- Counting Sort
- Stable sorting
- Non-comparative sorting
- Arrays
- Integer arithmetic
- Digit extraction
- Helper methods
- Static methods
- Loops
- Algorithm analysis
- Separation of concerns

## Technologies Used

- Java
- Java Development Kit (JDK)
- Java Standard Library
- Visual Studio Code
- Git
- GitHub
- Terminal / Command Line

## Project Structure

```text
JavaRadixSort/
├── Screenshots/
│   ├── Output1.png
│   ├── Output2.png
│   ├── Output3.png
│   ├── Output4.png
│   ├── RadixSort1.png
│   ├── RadixSort2.png
│   └── RadixSortTest.png
├── RadixSort.java
├── RadixSortTest.java
├── README.md
└── .gitignore
```

- `RadixSort.java` – Radix Sort and Counting Sort implementation
- `RadixSortTest.java` – Test array and program entry point
- `Screenshots/` – Source code and step-by-step output screenshots
- `.gitignore` – Excludes compiled Java files and editor settings
- `README.md` – Project documentation

## How to Run

### Prerequisites

- Java Development Kit (JDK 11 or later)
- Git
- A terminal or command-line environment

Verify that the required tools are installed:

```bash
java -version
javac -version
git --version
```

### Steps

1. Clone the repository:

```bash
git clone https://github.com/aliramirez08/JavaRadixSort.git
```

2. Navigate to the project directory:

```bash
cd JavaRadixSort
```

3. Compile both Java files:

```bash
javac RadixSort.java RadixSortTest.java
```

4. Run the test program:

```bash
java RadixSortTest
```

5. Press Enter after each sorting pass to continue.

## Code Examples

### Test Array

```java
Integer[] arr = {
    783, 99, 472, 182, 264, 543,
    356, 295, 692, 491, 94
};
```

The array contains positive integers with different numbers of digits.

### Finding the Maximum Value

```java
private static int getMax(Integer[] arr) {
    int max = arr[0];

    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }

    return max;
}
```

The largest value determines how many digit positions the algorithm must process.

### Extracting a Digit

```java
int digit = (arr[i] / exp) % 10;
```

The `exp` value identifies the current digit position:

- `1` processes the units digit
- `10` processes the tens digit
- `100` processes the hundreds digit

### Stable Counting Sort

```java
for (int i = n - 1; i >= 0; i--) {
    int digit = (arr[i] / exp) % 10;
    output[count[digit] - 1] = arr[i];
    count[digit]--;
}
```

The array is processed from right to left when building the output array. This preserves the relative order of elements with matching digits, making the Counting Sort operation stable.

### Radix Sort Passes

```java
for (int exp = 1; max / exp > 0; exp *= 10) {
    countingSort(arr, exp);

    System.out.print(
        "After pass " + pass + " (exp = " + exp + "): "
    );
    System.out.println(Arrays.toString(arr));

    System.out.println("Press Enter to continue...");
    System.in.read();

    pass++;
}
```

The loop performs one stable Counting Sort operation for each digit position.

## Example

### Original Array

```text
[783, 99, 472, 182, 264, 543, 356, 295, 692, 491, 94]
```

### After Pass 1 — Units Digit

```text
[491, 472, 182, 692, 783, 543, 264, 94, 295, 356, 99]
```

### After Pass 2 — Tens Digit

```text
[543, 356, 264, 472, 182, 783, 491, 692, 94, 295, 99]
```

### After Pass 3 — Hundreds Digit

```text
[94, 99, 182, 264, 295, 356, 472, 491, 543, 692, 783]
```

### Final Sorted Array

```text
[94, 99, 182, 264, 295, 356, 472, 491, 543, 692, 783]
```

## Complexity Analysis

Let:

- `n` represent the number of elements
- `d` represent the number of digits in the largest value
- `b` represent the numeric base, which is 10

| Measurement | Complexity |
|---|---|
| Time | `O(d × (n + b))` |
| Auxiliary space | `O(n + b)` |

Because the numeric base is fixed at 10, the running time is commonly simplified to `O(d × n)`.

## What I Learned

This project strengthened my understanding of how Radix Sort processes values one digit at a time instead of comparing entire values directly. I learned why the stability of Counting Sort is essential: elements with the same current digit must remain in their existing relative order for later passes to produce the correct result.

Displaying the array after each pass helped me visualize how the values gradually move into their final positions. I also gained practice analyzing time and space complexity and separating an algorithm implementation from its test class.

## Future Improvements

- Accept values from user input
- Support arrays of different sizes
- Add validation for empty arrays
- Add support for negative integers
- Replace `Integer[]` with the more memory-efficient `int[]`
- Add automated unit tests
- Compare Radix Sort with comparison-based algorithms
- Measure execution time for larger datasets
- Add an option to disable pauses
- Generate random test arrays
- Visualize the counting buckets after each pass

## Screenshots

### RadixSort.java — Part 1

![RadixSort.java Part 1](Screenshots/RadixSort1.png)

### RadixSort.java — Part 2

![RadixSort.java Part 2](Screenshots/RadixSort2.png)

### RadixSortTest.java

![RadixSortTest.java](Screenshots/RadixSortTest.png)

### Original Array and First Pass

![Original Array and First Pass](Screenshots/Output1.png)

### Second Pass

![Second Pass](Screenshots/Output2.png)

### Third Pass

![Third Pass](Screenshots/Output3.png)

### Final Sorted Array

![Final Sorted Array](Screenshots/Output4.png)
