# UiPath Email Automation Project

## Objective
This project demonstrates how to:
1. Send an Email using UiPath’s **Send SMTP Mail Message** activity.  
2. Download Email Attachments (e.g., resumes) using **Get IMAP/Outlook Mail Messages**.

---

## Part 1: Sending Email

### Steps
1. Create New Project
   - Open UiPath Studio → `New Project` → `Process`
   - Name it **SendEmailExample**

2. Add Variables
   | Name  | Data Type    | Scope | Purpose                              |
   |-------|--------------|-------|--------------------------------------|
   | pass  | SecureString | Main  | Stores email account password        |
   | result| String       | Main  | Stores the status code of email sent |

3. Configure Send SMTP Mail Message
   - Drag `Send SMTP Mail Message` into the workflow.
   - Properties:
     - To: `"recipient@example.com"`
     - Subject: `"test mail"`
     - Body: `"Today, 23/09/2025, we're testing email automation"`
     - Port: `25` (or your SMTP server’s port, often `587` for Gmail)
     - Server: `"smtp.gmail.com"`
     - Email: `"your_email@gmail.com"`
     - SecurePassword: `pass`
     - StatusCode: `result`

4. Add Confirmation
   - Drag `Message Box` below the SMTP activity.
   - Text = `"Email sent!"`

**Output:**  
- Email sent to the specified recipient.  
- Message Box confirms success.  
- `result` stores the SMTP status code.  

---

## Part 2: Downloading Resume Attachment

### Steps
1. Add Email Activity
   - Use `Get IMAP Mail Messages` (or `Get Outlook Mail Messages` if using Outlook).
   - Configure:
     - Server: `imap.gmail.com`
     - Port: `993`
     - Email: `"your_email@gmail.com"`
     - Password: `pass` (SecureString)
     - NumberOfMessages: e.g., `10`
     - Save output to `mailMessages` (List of MailMessage).

2. Save Attachments
   - Use `For Each` to iterate over `mailMessages`.
   - Inside loop:
     - Add `Save Attachments` activity.
     - Input: `item.Attachments`
     - Path: `"C:\Users\admin\Desktop\mail_attachments"` (or any folder).
     - This will download resumes or any attachments.

---

## Workflow Summary
- Send Email → Uses SMTP to deliver a test mail.  
- Download Resume Attachment → Uses IMAP/Outlook to fetch and save attachments locally.  

---

## Output:

<img width="1515" height="416" alt="Screenshot 2025-09-30 084438" src="https://github.com/user-attachments/assets/e8905442-acd3-4bc7-8b39-e01f955b2aab" />
<img width="1920" height="1200" alt="Screenshot (175)" src="https://github.com/user-attachments/assets/7dec1f69-5b0f-46ed-8b40-ca8752e5dba6" />
<img width="816" height="471" alt="Screenshot 2025-09-30 084557" src="https://github.com/user-attachments/assets/03e81a90-c239-438d-bc99-bef701f3ac40" />


## Result
- Email is successfully sent using SMTP.  
- Resume (or other attachments) is downloaded and saved in the given folder.  


- Make sure your antivirus/firewall allows SMTP/IMAP traffic.  
- Folder path for saving attachments must exist, otherwise create it first.  
