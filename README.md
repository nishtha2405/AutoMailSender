### Automated Case Details PDF Generation and Email Notification System

#### Objective:
The goal of this project is to automate the generation of case detail PDFs from a spreadsheet and send email notifications with the PDF attached, particularly when a case is scheduled for the current day.

#### Key Components:

1. **Google Sheets**:
   - A spreadsheet named "Court Status" contains case details in a structured format.
   - Each row represents a different case, with specific columns for client name, appeal, court, date of filing, case number, opposing party, current status, last date, next date, brief for, drafting, decided on, and execution.

2. **Google Drive**:
   - A template Google Doc that acts as the base for the PDF.
   - Temporary and destination folders to handle file operations during PDF creation.

3. **Google Apps Script**:
   - **Create_bulk_pdf**: Main function to read data from the Google Sheet, process each row, and trigger PDF creation if the case is scheduled for today.
   - **Create_pdf**: Function to create a PDF from the template, populate it with case details, save it, and send it via email.
   - **time_alert**: Function to check if a case is scheduled for today and call `Create_pdf` accordingly.

#### Workflow:

1. **Data Fetching**:
   - The script retrieves data from the "Court Status" sheet, excluding the header row.

2. **Processing Each Case**:
   - For each row, the script extracts relevant case details and logs the client name for debugging.
   - Calls `time_alert` to check if the case is scheduled for today.

3. **Date Check**:
   - `time_alert` compares today's date with the next scheduled date of the case.
   - If the dates match, it triggers the PDF creation process.

4. **PDF Creation**:
   - `Create_pdf` makes a temporary copy of the template document, populates it with case details by replacing placeholders, and converts it to a PDF.
   - The PDF is saved in the destination folder and the temporary file is deleted.

5. **Email Notification**:
   - The script sends an email with the created PDF attached to a specified recipient.

#### Benefits:
- **Automation**: Reduces manual work by automating the process of generating and sending case details.
- **Timeliness**: Ensures timely notifications are sent when cases are scheduled for the current day.
- **Efficiency**: Streamlines the workflow by leveraging Google Apps Script for seamless integration between Google Sheets, Google Docs, and Gmail.

#### Usage:
- This system can be scheduled to run daily using Google Apps Script's triggers, ensuring that relevant case details PDFs are generated and sent automatically.

By integrating various Google Workspace services through Google Apps Script, this project efficiently handles the repetitive task of generating and emailing case details based on a schedule, improving productivity and accuracy in handling legal case notifications.
