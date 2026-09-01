# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="1282" height="811" alt="image" src="https://github.com/user-attachments/assets/fbdb9524-6852-436b-9172-d29713d3f2ee" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Member | MemberID (PK), Name, MembershipType, StartDate | Each member registers once |
| Program | ProgramID (PK), ProgramName | Yoga, Zumba, Weight Training etc. |
| Trainer | TrainerID (PK), Name, Specialization | Trainers specialize in certain programs |
| PersonalTrainingSession | SessionID (PK), Date, Time, Duration | Each session booked by a member with a trainer |
| Attendance | AttendanceID (PK), MemberID (FK), SessionID (FK), Status | Tracks whether a member attended a session |
| Payment | PaymentID (PK), MemberID (FK), Amount, Date, Type | Type: Membership or Session |
| MemberProgram | MemberID (FK), ProgramID (FK) | Resolves M:N between Member and Program |
| ProgramTrainer | ProgramID (FK), TrainerID (FK) | Resolves M:N between Program and Trainer |

---

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|--------------|---------------|-------|
| Member registers Membership | 1:1 | Total | Each Member has one Membership |
| Member joins Program | M:N (via MemberProgram) | Partial | One Member can join many Programs |
| Trainer assigned to Program | M:N (via ProgramTrainer) | Partial | One Trainer can be assigned to many Programs |
| Member books Personal Training Session with Trainer | M:N | Partial | A Member can book many Trainers |
| Session–Attendance | 1:N | Total | One Session has many Attendance records |
| Member–Payment | 1:N | Total | A Member can make multiple Payments |

---

### Assumptions
- Each session involves exactly one trainer and one member.  
- Programs are predefined (Yoga, Zumba, Weight Training, etc.).  
- Payments are only for membership or session bookings.  

---


# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="998" height="805" alt="image" src="https://github.com/user-attachments/assets/b0e55038-1721-4bae-893f-ebc0d9276a52" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Member | MemberID (PK), Name, ContactInfo | Library users |
| Book | BookID (PK), Title, Author, Category, AvailabilityStatus | Each book has unique ID |
| Loan | LoanID (PK), BookID (FK), MemberID (FK), LoanDate, ReturnDate, Fine | Tracks borrowed book details |
| Event | EventID (PK), EventName, Date, Time | Library events such as author talks |
| Room | RoomID (PK), RoomName, Capacity, Type | Each event held in one room |
| Speaker | SpeakerID (PK), Name, Expertise | Speakers/Authors invited for events |
| MemberEvent | MemberID (FK), EventID (FK) | Resolves M:N between Member and Event |
| EventSpeaker | EventID (FK), SpeakerID (FK) | Resolves M:N between Event and Speaker |

---

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|--------------|---------------|-------|
| Member borrows Books | M:N (via Loan) | Total | A Member can borrow many Books |
| Member registers for Event | M:N (via MemberEvent) | Partial | Members can attend multiple Events |
| Event uses Room | 1:N | Total | One Room can host many Events |
| Event has Speaker | M:N (via EventSpeaker) | Partial | One Event can have multiple Speakers |

---

### Assumptions
- Books can be borrowed multiple times by different Members.  
- Each Event happens in one Room at a specific time.  
- A Speaker can participate in multiple Events.  

---


---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1175" height="762" alt="image" src="https://github.com/user-attachments/assets/f345cd41-e014-4ac9-a1f7-576c7a6fe047" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Customer | CustomerID (PK), Name, Phone | Each customer can make multiple reservations |
| Reservation | ReservationID (PK), Date, Time, GuestCount, CustomerID (FK) | Stores reservation details |
| Table | TableID (PK), Location, Capacity | One table can host different reservations over time |
| Waiter | WaiterID (PK), Name | Waiter assigned to reservations |
| Bill | PaymentID (PK), Amount, ServiceCharge, Total, ReservationID (FK), CustomerID (FK) | Bill generated for reservation |

---

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|--------------|---------------|-------|
| Customer makes Reservation | 1:N | Total | A Customer can make multiple Reservations |
| Reservation assigned to Table | 1:N | Total | One Table can host multiple Reservations |
| Reservation served by Waiter | 1:N | Partial | A Waiter can serve multiple Reservations |
| Reservation generates Bill | 1:1 | Total | Each Reservation generates one Bill |
| Customer makes Bill (Payment) | 1:N | Total | A Customer can have multiple Bills |

---

### Assumptions
- One reservation uses one table and one waiter.  
- Bill is generated automatically after service.  
- Customer details stored for every reservation.  

---



## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
