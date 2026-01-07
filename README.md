# Housing Approval Program (Pascal)

This is a simple console-based program written in **Pascal** (originally for Ezy Pascal). 

It was created around **2018/2019** as my **SBA (School Based Assessment)** for CSEC Information Technology. The program iterates through a list of applicants, takes user input for their financial details, and calculates their eligibility for housing approval based on their debt-to-income ratio.

## How it Works
The program asks for:
* Name
* Gross Salary
* Deductions
* Expenses & Repayments

It then calculates the **Net Income** and **Balance**. If the Balance is at least 50% of the Net Income, the applicant is "Approved."

## 2026 Review & Updates
I dug this up from my old archives to document my early coding history. The core logic and structure are exactly as they were when I submitted this for CSEC, but I made a few minor edits before uploading to ensure it runs correctly:

* **Input Validation:** Added checks to prevent entering negative numbers for salary or expenses.
* **Crash Prevention:** Added a check to prevent a "division by zero" error if no applicants are approved.
* **Sanity Checks:** Added logic to ensure deductions cannot exceed the gross salary.

## How to Run
This is a standard `.pas` file. You can compile and run it using:
* Free Pascal Compiler (`fpc`)
* Turbo Pascal
* Any online Pascal IDE
