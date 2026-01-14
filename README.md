# Numerical Differentiation Using Finite Difference Methods
Forward, Backward & Central Difference for First and Second Derivatives
# Project Title
Numerical Differentiation – Forward, Backward & Central Difference Methods

# Project Overview
This project is developed as part of the Numerical Methods course.
 The objective is to numerically approximate the first and second derivatives of a function using finite difference methods and compare them with the exact analytical derivatives.
The program is written in C++ and allows the user to choose a function, enter a value of xxx, and compute:
Forward difference approximation


Backward difference approximation


Central difference approximation


Exact derivative


Absolute errors


The results are also saved into CSV files which are later used to plot Error vs Step Size (h) graphs.



# Objectives of This Project
Implement Forward, Backward, and Central Difference methods.


Approximate first and second derivatives numerically.


Compare numerical derivatives with exact analytical derivatives.


Study the effect of step size h on accuracy.


Generate CSV data for plotting graphs.


Analyze which numerical method is the most accurate.




# Finite Difference Formulas
First Derivative
Forward Difference
 f′(x) ≈ ( f(x + h) − f(x) ) / h
Backward Difference
 f′(x) ≈ ( f(x) − f(x − h) ) / h
Central Difference
 f′(x) ≈ ( f(x + h) − f(x − h) ) / (2h)
Forward and Backward methods have an error of order O(h),
 while Central Difference has error of order O(h²), making it more accurate.

Second Derivative
Forward Difference
 f″(x) ≈ ( f(x + 2h) − 2f(x + h) + f(x) ) / h²
Backward Difference
 f″(x) ≈ ( f(x) − 2f(x − h) + f(x − 2h) ) / h²
Central Difference
 f″(x) ≈ ( f(x + h) − 2f(x) + f(x − h) ) / h²
Central difference is theoretically more accurate because its truncation error is O(h²).

# Step Sizes Used
The following step sizes are used in the experiment:
h = 0.1, 0.05, 0.01, 0.005, 0.001
These values help analyze how the numerical error changes as h decreases.

# Error Calculation
For each method, the absolute error is computed as:
Error = | Exact Value − Numerical Value |
Errors are calculated separately for:
Forward Difference


Backward Difference


Central Difference



# Code Implementation & Explanation
This project is implemented in C++ using a clean and modular structure to compute numerical derivatives and their errors efficiently.
Function Structure
The program uses a structured approach to store each test function and its exact derivatives:
struct TestFunction {
    string name;
    Func f;        // original function f(x)
    Func f1_exact; // exact first derivative
    Func f2_exact; // exact second derivative
};

Test Functions
The following functions are used for testing:
Function
First Derivative
Second Derivative
sin(x)
cos(x)
−sin(x)
e^x
e^x
e^x
x³
3x²
6x

These analytical derivatives are used as the reference for error calculation.

Numerical Differentiation Functions
The program implements all three finite difference formulas for both first and second derivatives.
First derivative
Forward difference


Backward difference


Central difference


Each is computed using a separate function such as:
double forward_diff(Func f, double x, double h)
double backward_diff(Func f, double x, double h)
double central_diff(Func f, double x, double h)

Second derivative
Similarly, forward, backward, and central difference formulas are implemented as:
double forward_diff2(Func f, double x, double h)
double backward_diff2(Func f, double x, double h)
double central_diff2(Func f, double x, double h)


Derivative Calculation Process
For the user-selected function and a given value of xxx, the program:
Computes numerical derivatives using forward, backward, and central difference formulas.


Computes the exact derivative using analytical expressions.


Computes absolute errors using:


Error=Error = | Exact Value − Numerical Value |
This is done separately for:
First derivative


Second derivative


The following step sizes are used in the experiment:
h = 0.1, 0.05, 0.01, 0.005, 0.001

Error Storage and CSV Generation
The program automatically creates two CSV files:
function_X_first.csv


function_X_second.csv


Each file contains:
h, forward_error, backward_error, central_error

These files are later used to plot Error vs Step Size (h) graphs.

User Interaction
The program is fully menu-driven.
The user selects:
A function


A value of xxx


The program then prints formatted tables for:
First derivative


Second derivative


along with all numerical values and errors.
Invalid function choices are handled safely.

# How to Compile and Run
Step 1: Compile the program
Open terminal in the project folder and type:
g++ code.cpp -o diff


Step 2: Run the program
./diff


Step 3: Program Interaction
After running, the program shows:
Choose function:
1. f(x) = sin(x)
2. f(x) = e^x
3. f(x) = x^3

Example input:
Enter choice (1–3): 1
Enter x: 1

This selects
 f(x)=sin x)  at x=1
The program then prints tables for:
First derivative


Second derivative


showing numerical values, exact values, and errors for different step sizes.
CSV files are generated automatically for graph plotting.

# Sample Numerical Result
Example for f(x) = sin(x) at x = 1
| h | Forward | Backward | Central | Exact | Err(F) | Err(B) | Err(C) |
|----|----------|-----------|-----------|--------|---------|---------|---------|
| 0.1 | 0.49736 | 0.58144 | 0.53940 | 0.54030 | 0.04294 | 0.04114 | 0.00090 |
| 0.05 | 0.51904 | 0.56111 | 0.54008 | 0.54030 | 0.02126 | 0.02081 | 0.00023 |
| 0.01 | 0.53609 | 0.54450 | 0.54029 | 0.54030 | 0.00422 | 0.00420 | 0.00001 |

This table shows that the Central Difference method gives much smaller error.
# Data Description
The program generates CSV files containing:
h, forward_error, backward_error, central_error
These data files are used to draw Error vs Step Size (h) graphs for all methods.

# Graph Interpretation and Discussion
From the log–log error plots:
Forward and Backward Difference methods show linear decrease in error.


Central Difference method shows much faster decrease.


This confirms:


Forward and Backward → O(h) accuracy


Central → O(h²) accuracy


When hhh becomes extremely small, rounding errors due to floating-point arithmetic start to dominate and the error stops decreasing.
Overall, Central Difference gives the most reliable and accurate results.


# Conclusion
Finite difference methods provide an effective way to approximate derivatives when analytical solutions are not available.
Among the three methods, the Central Difference Method gives the best accuracy for both first and second derivatives because of its higher order of convergence.
This project successfully demonstrates how numerical differentiation accuracy depends on step size and method selection.
