-----

# Dog Age Calculator

This simple C++ console application calculates a dog's age in "human years" based on a common conversion formula. It demonstrates basic input/output operations, variable handling, and robust input validation to ensure a smooth user experience. This project was completed as part of **Codecademy's C++ intro course**.

## Features

  * **User Input:** Prompts the user to enter their dog's age and name.
  * **Input Validation:** Ensures the dog's age is a valid whole number greater than 2. It will repeatedly ask for input until valid data is provided, preventing crashes from incorrect entries (like text or decimals).
  * **Age Conversion:** Calculates human years using the formula:
      * The first 2 dog years count as 21 human years.
      * Each subsequent dog year counts as 4 human years.
  * **Personalized Output:** Displays a fun message including the dog's name and its calculated age in human years.

## How to Compile and Run

To compile and run this project, you'll need a C++ compiler (like g++).

1.  **Save the Code:**
    Save the provided C++ code into a file named `dog_age_calculator.cpp` (or any other `.cpp` extension).

2.  **Open a Terminal/Command Prompt:**
    Navigate to the directory where you saved the file.

3.  **Compile:**
    Use the following command to compile the code:

    ```bash
    g++ dog_age_calculator.cpp -o dog_age_calculator
    ```

    This command compiles `dog_age_calculator.cpp` and creates an executable file named `dog_age_calculator` (or `dog_age_calculator.exe` on Windows).

4.  **Run:**
    Execute the compiled program:

    ```bash
    ./dog_age_calculator
    ```

    On Windows, you might just type:

    ```bash
    dog_age_calculator.exe
    ```

## Example Interaction

```
Enter your dog's age: 1
Please enter a dog age greater than 2.
Enter your dog's age: 1.5
Invalid input. Please enter a whole number for the dog's age.
Enter your dog's age: 5
Please enter your dog's name: Buddy
My name is Buddy! Ruff ruff, I am 33 years old in human years.
```

-----

## Code

```cpp
#include <iostream>
#include <string>
#include <limits> // Required for std::numeric_limits

int main() {
    int dog_age;

    // Loop until valid input (integer > 2) is received
    while (true) {
        std::cout << "Enter your dog's age: ";
        std::cin >> dog_age;

        // Check if the input operation failed (e.g., non-integer entered)
        if (std::cin.fail()) {
            std::cout << "Invalid input. Please enter a whole number for the dog's age.\n";
            std::cin.clear(); // Clear the error flags on std::cin
            // Discard the invalid input up to the newline character
            std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
        } 
        // Check if the input was a valid integer but <= 2
        else if (dog_age <= 2) {
            std::cout << "Please enter a dog age greater than 2.\n";
        }
        // If input is valid (integer and > 2), break the loop
        else {
            break; 
        }
    }
    
    std::string dog_name;
    std::cout << "Please enter your dog's name: ";
    std::cin >> dog_name;

    int early_years = 21;
    int later_years = (dog_age - 2) * 4;
    int human_years = early_years + later_years;
    
    std::cout << "My name is " << dog_name << "! Ruff ruff, I am " << human_years << " years old in human years.\n";

    return 0; 
}

```
