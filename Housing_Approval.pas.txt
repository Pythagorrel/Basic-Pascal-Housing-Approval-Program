Program Housing_Approval;

Var 
    i : integer;
    Names: array[1..30] of String;
    Gross_Salary: array[1..30] of Real;
    Total_Salary_Deductions: array[1..30] of Real;
    Total_Expenses: array[1..30] of Real;
    Total_Repayments: array[1..30] of Real;
    Net_Income: array[1..30] of Real;
    Balance: array[1..30] of Real;
    Status: array[1..30] of String;
    
    Number_Approved_Applicants : Integer;
    Number_Applicants : Integer;
    Total_Net_Income : Real;
    Average_Net_Income : Real;
    Total_Balance : Real;
    Average_Balance : Real;
                 
Begin
    Total_Net_Income := 0;
    Average_Net_Income := 0;
    Total_Balance := 0;
    Average_Balance := 0;
    Number_Applicants := 0;
    Number_Approved_Applicants := 0;

    For i := 1 to 30 do
    Begin
        Writeln('--- Applicant ', i, ' ---');
        
        Write('Enter Name: ');    
        Readln(Names[i]);
        
        { Verifying that Gross Salary is positive }
        Repeat
            Write('Enter Gross Salary (Must be positive): ');    
            Readln(Gross_Salary[i]);
            If Gross_Salary[i] < 0 Then
                Writeln('Error: Salary cannot be negative. Try again.');
        Until Gross_Salary[i] >= 0;
        
        { Verifying that Deductions do not exceed Salary }
        Repeat
            Write('Enter Total Salary Deductions: ');    
            Readln(Total_Salary_Deductions[i]);
            
            If Total_Salary_Deductions[i] < 0 Then
                Writeln('Error: Deductions cannot be negative.')
            Else If Total_Salary_Deductions[i] > Gross_Salary[i] Then
                Writeln('Error: Deductions cannot represent more than 100% of salary.');
                
        Until (Total_Salary_Deductions[i] >= 0) AND (Total_Salary_Deductions[i] <= Gross_Salary[i]);
        
        { Verifying that Expenses are positive }
        Repeat
            Write('Enter Total Expenses (Must be positive): ');    
            Readln(Total_Expenses[i]);
            If Total_Expenses[i] < 0 Then
                 Writeln('Error: Expenses cannot be negative.');
        Until Total_Expenses[i] >= 0;
        
        { Verifying that Repayments are positive }
        Repeat
            Write('Enter Total Repayments (Must be positive): ');    
            Readln(Total_Repayments[i]);
            If Total_Repayments[i] < 0 Then
                 Writeln('Error: Repayments cannot be negative.');
        Until Total_Repayments[i] >= 0;
        
        
        { --- CALCULATIONS --- }
        
        Net_Income[i] := Gross_Salary[i] - Total_Salary_Deductions[i];
        Writeln('The Net Income is: ', Net_Income[i]:8:2);

        Balance[i] := Net_Income[i] - (Total_Expenses[i] + Total_Repayments[i]);
        Writeln('The Balance is: ', Balance[i]:8:2);

        
        If Balance[i] >= 0.5 * Net_Income[i] Then
            Status[i] := 'Approved'
        Else 
            Status[i] := 'Disapproved';
            
        Writeln('The Approval Rating is: ', Status[i]);

        Number_Applicants := Number_Applicants + 1;

        If Status[i] = 'Approved' Then
        Begin
             Number_Approved_Applicants := Number_Approved_Applicants + 1;
             Total_Net_Income := Total_Net_Income + Net_Income[i];
             Total_Balance := Total_Balance + Balance[i];
        End;
        
        If Number_Approved_Applicants > 0 Then
        Begin
             Average_Net_Income := Total_Net_Income / Number_Approved_Applicants;
             Average_Balance := Total_Balance / Number_Approved_Applicants;
             
             Writeln('Current Approved Avg Income: ', Average_Net_Income:8:2);
             Writeln('Current Approved Avg Balance: ', Average_Balance:8:2);
        End;
             
        Writeln('--------------------------------');
    End;
End.