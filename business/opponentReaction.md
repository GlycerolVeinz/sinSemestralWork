# WasteLess
## Review - SINners Business Analysis v. 0.0.3

### Team Members

#### WasteLess Team
- Denis Pak, Artem Liamkin, Ales Shvaibovich, Petr Aubrecht, Egor Batuev

#### SINners Team
- Matvej Safrankov, Veronika Anokhina, Vladyslav Zlochevskyi, Arseniy Panyukov, Kateřina Fryšarová

---

### Strengths
[^1]
- **Well-detailed finance section.**
- **Business goals and requirements** are sufficient, even after excluding the overly general ones, and clearly describe what the project aims to achieve.
- **Business Process Model** – The processes make sense here, and there’s little to criticize beyond minor details.
- **Business Domain Model** – Gives a clear picture of what the project will work with.

### Weaknesses
- Inconsistent format of submitted documentation (text on git-wiki, finance in Google Sheets, individual diagrams in separate PDF files). [^2]
- In the Business Domain model, the Review object. [^3]
- In **Business Goals and Requirements**, BG-01 and BG-03 are too general, and some BRQs are linked to unrelated BGs, or the connection is unjustified.
- In the **Business Process Model**, all processes for a given actor are in a single diagram, which complicates finding a specific process (e.g., Blocking a user can practically be anywhere – Admin, Admin-Customer, Admin-Performer). [^4]

### Comments
- **Note on the team name:** If I want to remove the stigma around striptease, I probably shouldn’t be named "SINners." [^5]

### Business Goals and Requirements
- **BG-01 Increase Club Attendance** and **BG-03: Expand Clientele and Flexible Working Hours** are too general. [^6]
  - BG-01 = As a business owner, I need more customers → more money.
  - BG-03 = As a service provider, I want more customers and flexible working hours.
- For **BG-02**, it might be possible to remove the last part, "and a larger number of customers." The previous justification here suffices.
- **BG-04** and **BG-05** are clear and specific.
- **BRQ-207** is not entirely clear in its intent. If I were to follow a literal reading, I’d get: “As a Performer('s requirements) I need Roles/tiers because (I want) differentiate between clients.” This sounds like the Performer would have roles, but it was probably meant that the Customer would have roles. [^3]
- **BRQ-303** The Event page doesn’t directly help with clients; it only displays events, which, in turn, help. It would be good to mention them explicitly. [^7]

### BRQ Diagram
- Out of **BRQ-002**, **BRQ-003**, **BRQ-301**, **BRQ-302**, and **BRQ-303**, which are linked to **BG-02**, only 002 and 003 make sense. For instance, I don’t see how a management system helps to remove the stigma around striptease. [^8] 
- The linkage of **BRQ-001** and **BRQ-204** with **BG-03** is odd. I don’t see a connection between payment methods and the number of customers. Perhaps a new **BG** for secure payments could be created here. [^9]
- **Aesthetic note:** It would be good to align **BRQs** under each other and, if possible, sort them. The reading direction in the trace doesn’t have to be in a specific direction. [^10]

### Finance
- **Scenarios are missing** (pessimistic, realistic, and optimistic). [^11]
- Otherwise, very detailed and credible.

### Business Domain Model
- The `Classes::` designation for objects is unnecessary. [^12]
- The **Customer—(report)—Performer** relationship might benefit from its own Report class, where complaints could be recorded, but if justification isn’t needed, it can remain as is. 
- Every **Review**, as written with 1 cardinality, is currently written from both the **Customer** and **Performer** simultaneously. Either change it to `0..1` or split it into two reviews (Customer review and Performer review). [^3]
- **Payment** doesn’t need to contain the **customer** attribute; the relationship line is enough. [^3]
- The **Customer** can be blocked, but information on their blocked status is not stored anywhere. Either add an attribute or simply delete them. You could also add a **status class** if there are more states in which a **Customer** can exist.
- **Aesthetic notes:**
  - **Club—Address** has an overlapping cardinality. 
  - **Performer→Review** has a remaining arrow. [^3]
  - **Reservation** has a red “A” on it?

### Business Process Model
- In general, all diagrams except for **Customer+Performer.pdf** model every possible option instead of a specific process. However, if they were divided into multiple processes, they would be good. For instance, divide "Admin" into "AdminResolveReports," "AdminEditPerformerProfile," "AdminEditsEvent," etc.
- A few more comments on individual diagrams:
  - **Admin.pdf** – missing option for login failure (also in Customer.pdf). [^3]
  - **Customer.pdf**
    - What does "leave review from history" mean? Possibly add a review to an event from history, but it’s not entirely clear. Maybe try renaming it. [^13]
    - In "make a reservation," arrows should merge into a diamond (OR) and then into the action; otherwise, it implies **AND**, which we don’t want here. [^3] 

# Sinners
## Opponent reaction
[^1] Thank you!
[^2] First of all, the documentation is kept separate because it is an early version, nothing is truly set in stone untill we fix as much as possible based an all reviews that we can get. Secondly, we tried to use the most comfortable tools for each part of business Analysis.
[^3] Noted. Will try to fix.
[^4] We understand your possible confusion, what we wanted to represent is all the possible actions one could take while using the app.
[^5] As practice shows, if you create a small controversy around something it attracts people and makes them talk about it. Which is a good thing for removing a taboo from a society. Take [*©PURE*](https://pure.app/)
[^6] They might appear too general at first, but there is a small nuance in our case. Firstly BG01 is the goal that tries to sotisfy business owners, but our app isn't even made for them. That's why we thought it would be a good goal for us, we need to satisfy owners, because we want to collaborate with them, even if our app doesn't explicitly help them. BG03 is little bit different story, we want to help strippers with their work, that is partly why we want to make this app, this goal aims to make their scheduling and work hours easier, in stead of their typical day work when they need too be present at the club whole night long because they don't know when someone will order them.
[^7] Well we know thatt events attract people, but how are they supposed to know about them if there is no page to display them? That's why we created this BRQ-303. Our app doesn't make events, clubs do, we only provide a place to present them.
[^8] We would have to disagree about BRQ-303 and BRQ-302, but BRQ-301 noted.
[^9] Actually it is linked on purpose, we want to attract people with our good payment system that is reliable.
[^10] It's purely preference, we would appreciate to leave out such comments in further opponent reviews.
[^11] That is why it is in spreadsheat, our goal was to create credible scenario, but if someone desires to know out possible scenarios he is free to adjust constants and see the outcome. (The spreadsheet is dynamic)
[^12] This comes purely from EA, we have our classes in separate package. We will try to look in to it (how to hide it).
[^13] You understood it the way we wanted you to, we don't see a possibility how to name it this simply and with same meaning other way.