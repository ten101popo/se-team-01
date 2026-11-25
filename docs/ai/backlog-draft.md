Tool: Gemini assistant (backlog draft)
Date: 2026-11-25
Prompt: docs/ai/backlog-prompt.txt

# Product Backlog Draft: Campus Lab Equipment Borrowing System

## 1. User Stories

### Story 1: Browse available lab equipment by category
As a student working on a lab project
So that I know whether required boards or instruments are available before walking to the lab
I want to browse lab equipment by category and see available stock counts

- Happy path: Selecting category "Microcontrollers" shows every non-archived item in that category with its current available quantity.
- Sad path: Selecting a category that has no matching equipment shows an empty list with the message "No equipment found in this category".

### Story 2: Submit an equipment loan request
As a student borrower
So that I can reserve available lab equipment for my project work
I want to submit a loan request specifying the item, quantity, and return date within 14 days

- Happy path: Submitting a request for an available item with a return date 7 days ahead creates a pending LoanRequest and shows a confirmation summary.
- Sad path: Requesting an item with zero available stock or a return date beyond 14 days is rejected with a clear validation message and the earliest expected return date.

### Story 3: Approve or reject pending loan requests
As a lab technician
So that equipment is handed out fairly and stock counts reflect issued items
I want to review pending loan requests and approve or reject each one

- Happy path: Approving a pending request marks it as Approved, decrements available Equipment stock, and records the technician's decision timestamp.
- Sad path: Rejecting a request without entering a reason is blocked with "Please provide a rejection reason", or approving when stock already dropped to zero shows "Insufficient stock to approve".

### Story 4: Record equipment return and update stock
As a lab technician
So that returned instruments become available to other students immediately
I want to record the return of borrowed equipment and inspect its condition

- Happy path: Marking an active LoanRequest as Returned increments available Equipment stock and sets the actual return date.
- Sad path: Marking a returned item as damaged flags the unit as Broken instead of returning it to available stock.

### Story 5: Send due-date reminder email before return deadline
As a student with an active equipment loan
So that I return lab equipment on time and avoid delaying classmates
I want to receive an automated institutional email reminder before my loan due date

- Happy path: For active loans approaching their due date (assumed 2 days prior; *unconfirmed in intent*), the system sends an email via university SMTP listing the item and return deadline.
- Sad path: When the university SMTP server is unreachable, the system logs the delivery failure for retry and displays an alert on the technician dashboard without crashing.

### Story 6: Manage lab equipment catalog and broken status
As a lab technician
So that the online catalog matches physical lab inventory
I want to add new equipment items, update stock quantities, and mark broken units unavailable

- Happy path: Adding a new oscilloscope with category, total quantity, and working status makes it immediately visible in the catalog.
- Sad path: Submitting a blank item name or negative stock count is rejected with a validation message.

### Story 7: Online loan renewal [NOT IN INTENT - OPEN QUESTION]
As a student borrower
So that I can finish debugging my project without visiting the lab desk
I want to extend my active loan online once if no one else requested the item

- Happy path: Clicking "Renew" extends the due date by 7 days. *[Marked: answers Open Question 2 without customer confirmation.]*
- Sad path: Renewal is blocked if the loan is already overdue.

### Story 8: Late-return fine payment gateway [NOT IN INTENT]
As a lab administrator
So that late borrowers pay monetary penalties online
I want to charge overdue fines via QR PromptPay

- Happy path: Overdue borrower pays fine via QR code. *[Marked: not requested in intent at all.]*
- Sad path: Payment timeout leaves fine unpaid.

## 2. Assumptions not in the intent
1. Reminder emails are sent 2 days before the due date (Open Question 1).
2. Institutional email ends with `@cdti.ac.th`.
3. Each LoanRequest covers one equipment model for simplicity in Iteration 0.

## 3. Areas of concern
- **Concurrent approvals:** Two technicians approving the last available unit simultaneously could cause negative stock unless checked atomically.
- **SMTP delivery reliability:** University mail filters may delay automated reminders.
- **Open questions unresolved:** Lead time for email reminders (Q1) and online renewal policy (Q2) require customer proxy confirmation.
