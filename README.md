# rpachallenge
Note: Since I do not have the Windows operating system, the project was developed using UiPath Studio Web. Studio Web projects are compatible with the latest version of the Enterprise and Community editions of Studio and can be opened in both Studio and StudioX.

Preconditions to run the bot in Studio Web:
	- Studio Web is installed and configured. Crate UiPath Automation Cloud Account (cloud.uipath.com)
	- You have the solution folder on your machine. Folder available on GitHub (RPA Challenge)
	- Your browser (Chrome) supports the file-edit permission prompt.

Checklist — Open an existing local solution
    1. Click "Open solution"
    2. In the new browser window, navigate to the solution’s folder
    3. Select the solution folder
    4. Click "Select Folder"
    5. In the browser pop-up asking permission to edit files, click "Allow"
    6. Confirm the local solution opens in Studio Web

Note:
Click “Debug on Cloud” to run the bot in the cloud.
To run the bot locally, you must have UiPath Assistant installed.

To open a project in Studio Desktop from the “Workspace” page in Studio Web, select “View more documentation images” and then “Open in Studio Desktop” on the right side of the project.

If UiPath Studio is installed on your computer, select the option to open it when prompted by your browser. The project opens in a new instance of Studio.

The goal of this process is to create a workflow that will input data from a spreadsheet into the form fields on the screen.

Step 1 — Download and read the spreadsheet
1. Use Application/Browser
   - Action: Open the RPAChallenge link  
   - Properties: Close = Never, Open = Always, Resize = Maximize, InputMethod = Simulate
2. Click
   - Action: Click the Excel file download button (employee info)
3. Wait for download
   - Action: wait for the Excel file to appear in the “Downloads” folder
4. Read Range
   - Action: read the Excel spreadsheet
   - Output: dt_EmployeeInf (DataTable)

Step 2 — Fill out the form for each employee
1. Use Application/Browser
   - Action: attach the already open browser  
   - Properties: Close = Always, Open = Never, Resize = None
2. Click
   - Action: click the “Start” button
3. For Each Row in Data Table (dt_EmployeeInf)
   - Index variable: intIndex (stores the index of the current row)
   - Loop body:
     a. Try / Catch / Finally (encompassing the form-filling actions)
        - Try:
          - Type Into (multiple) — fill the form fields with the values from the current row
          - Log Message (Info) — log progress with the row index (intIndex)
        - Catch:
          - Log Message (Error) — log the row that generated the exception
     b. Click — click the “Submit” button to submit the record

Suggested variables and names
- dt_EmployeeInf — DataTable containing data read from Excel  
- intIndex — Integer (iteration index/counter)

Practical notes (brief recommendations)
- Check if the file is in the Downloads folder before opening it
- After reading the file, check whether the variable "dt_Employee" is null or empty
