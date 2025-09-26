# Exercise: Sending Email Using UiPath

## Objective
To automate sending an email using UiPath’s **Send SMTP Mail Message** activity.

---

## Step-by-Step Instructions

### 1. Create New Project
- Open **UiPath Studio** → New Project → Process  
- Name the project `SendEmailExample`

### 2. Add Variables
- Create the following variables in **Data Manager**:
  | Name   | Data Type      | Scope | Purpose                        |
  |--------|----------------|-------|--------------------------------|
  | pass   | SecureString   | Main  | Stores email account password securely |
  | result | String         | Main  | Stores the status code of sent email |

### 3. Use Send SMTP Mail Message Activity
1. Drag **Send SMTP Mail Message** into the workflow.  
2. Configure the following properties:  

| Property          | Value / Description                                      |
|------------------|----------------------------------------------------------|
| **To**           | `"recipient@example.com"`                                 |
| **Subject**      | `"test mail"`                                             |
| **Body**         | `"Today, 23/09/2025, we're testing email automation"`    |
| **Attachments**  | Optional – click **Attach Files** to add attachments    |
| **Port**         | `25` (or your SMTP server port)                         |
| **Server**       | `"smtp.gmail.com"`                                       |
| **Email**        | `"your_email@gmail.com"`                                 |
| **SecurePassword** | Assign variable `pass` (SecureString)                  |
| **UseOAuth**     | Checked/Unchecked depending on authentication method    |
| **StatusCode**   | `result` (to store result of email sending)             |

---

### 4. Add Confirmation Message
- Drag a **Message Box** activity below **Send SMTP Mail Message**.  
- Set **Text** = `"Email sent!"` to notify when the email is successfully sent.

---

## Workflow
1. Configure SMTP settings and login credentials.  
2. Compose email with recipient, subject, body, and optional attachments.  
3. Send email using **Send SMTP Mail Message**.  
4. Show **Message Box** confirmation.

---

## Output
- Email is sent to the specified recipient.  
- **Message Box** confirms `"Email sent!"`.  
- The `result` variable stores the status code returned by the SMTP server.

<img width="1919" height="1105" alt="Screenshot 2025-09-26 215855" src="https://github.com/user-attachments/assets/5aad31af-1d44-4433-a95c-c2c50a24e1a0" />
<img width="1917" height="1140" alt="Screenshot 2025-09-26 215907" src="https://github.com/user-attachments/assets/d0ff4159-25ee-4f59-b28e-620dd5d84cc1" />

## Result

Thus, email automation was successfully executed using UiPath.
