# System analysis for Sinners application

## System requirements

### SRQ-001 – Payment System  (BRQ-001)

The application must provide an integrated payment system to ensure fast, convenient, and anonymous transactions for clients.

**Description**:

- Each client must have their own in-app account.
- Payments can be made either through the club’s counter or through a secure third-party payment gateway.
- The payment interface shall be easy to use and must provide instant (maximum 1 minute delay) feedback on successful/failed transactions.
- Failed transactions should provide a reason.
- Transaction history must be saved and accessible from the client’s account.

### SRQ-1 – Reservations  (BRQ-102, BRQ-103)

The application must provide a convenient framework for choosing performers through the club’s page and through a Tinder-like swiping mechanism, as well as for selecting the time of performance.

#### SRQ-101 – Choice of Performer

- The club’s page must have a tab with a list of all performers, allowing clients to pick a performer.
- Tinder-like part: clients should be able to swipe photos of performers left (dislike) or right (like).
- After choosing the performer, the client must be redirected to choose the time.
- Only actively employed performers can be shown.
- Each performer's profile must have a brief description and rating.
- Blocked performers must never be displayed in the swipe mechanism.
- Blocked clients must never be shown the performers who blocked them.

#### SRQ-101 – Choice of Time

- The client must be able to see the performer's schedule.
- The system must be resilient towards double-booking.
- After selecting a date and time, this slot must be temporarily booked (for 5 minutes) to finish the reservation process.
- The client must be able to choose both the time and duration of the performance.

#### SRQ-102 – Reservation Confirmation

- When the client confirms the reservation, the performer must be notified.
- The client must be notified that their reservation is on hold until the performer confirms.
- When the performer confirms or rejects the reservation, the client must be notified.

#### SRQ-103 – Mandatory Status Update

- The system must automatically display a pop-up window when a performer logs into the application if they have any past or scheduled performances that require a status update.
- The pop-up window must display all performances requiring an update, including all necessary information (datetime, client's nickname, reservation ID).
- The performer must be able to mark each performance as **Completed** or **Canceled**.

**Notes**:

- All reservations must be stored.
- Each client and performer must be able to see their reservation history.

### SRQ-2 – Feedback  (BRQ-101, BRQ-202, BRQ-205, BRQ-208)

The application must include a system for leaving reviews on performances/clubs and offer functionality for blocking and reporting clients/performers to enhance the user experience.

#### SRQ-201 – Performer Reviews

- Clients must be able to write a review for any **Completed** performance from their reservation history.
- The review must include a rating (1-5, discrete) and may optionally have a text description.
- Reviews must have a separate tab in the performer’s profile.

#### SRQ-202 – Complaints and Blocking

- Clients/performers must be able to block other clients/performers through their profile.
- Blocked clients must be unable to make a reservation with the performer who blocked them.
- Clients/performers must be able to report another client/performer through their profile.
- Client support services must be able to read the reports and take action (e.g., ban the user from using the application).
- If a user is banned, they must receive a notification.

#### SRQ-203 – Club Reviews

- Clients must be able to write a review on any club where they have had a **Completed** reservation.
- The club page must have a separate tab with ratings and reviews.
- Club reviews must have a rating (1-5, discrete) and may optionally have a text description.
- Club administrators must be able to react to the reviews.

### SRQ-3 – Club Management System  (BRQ-301)

The system must provide club administrators with access to a centralized management interface, allowing them to view and manage data related to all performers, clients, and reservations associated with their club.

#### SRQ-301 – Performer Management

- Club administrators must have access to all data related to their employed performers (personal data, reservation history, including upcoming reservations, availability).

#### SRQ-302 – Client Management

- Club administrators must be able to access profiles of all clients who have/had reservations at their club, including reservation history and subscription level.
- Club administrators must not have access to data unrelated to the reservation due to anonymity reasons.

### Notes from GlycerolVeinz on System Requirements

- Define what the system must do (functional) and how well it should perform (non-functional)
- System requirements are usually split into functional and non-functional
- Numbering of requirements should be kept in groupings (as in business requirements)
- Good system requirement should be Clear, Measurable, Feasible, Testable, Consistent

#### Examples

##### Functional

- FR-002: Performer Reservation:
  - Clients should be able to browse and reserve available performers.
  - Reservation confirmations should be sent to the user within 5 minutes via push notification or email.

##### Non-functional

- NFR-002: Performance:
  - The system must handle up to 10,000 simultaneous users with an average response time of less than 2 seconds.

## Use cases

### Actors

- User
  - Club's manager
  - Performer
  - Client
- Developer
- Outsourced payment gate

### Any User

#### 0. Register a New User

- **Description:** Users register with the system and create an account.
- **Prerequisites:** The user provides all required information for registration.

#### 1. Login

- **Description:** Users log in to their account using credentials.

### Club Admin

#### 2. Report a Review

- **Description:** Admin can flag a problematic review for investigation if deemed inappropriate.
- **Outcome:** The review is flagged for further investigation or action.

- **Active actors :**
  - Club Admin
  - System

- **Main flow :**
  - User selects an objectionable review.
  - User chooses *report a review* option.
  - System opens complaint menu.
  - User fills in the report details.
  - System sends complaint to development team for an analyssis.

#### 3. Respond to a Review

- **Description:** Admin can reply to a review to provide a response or clarify a situation.

- **Active actors :**
  - Club admin
  - System

- **Main flow :**
  - User selects a review that he would like to respond to.
  - User chooses *reply* option.
  - System opens reply menu.
  - User fills in a reply.
  - System sends a notification for reply's author.
  
#### 4. Edit Event Details

- **Description:** Admin modifies the details of an already created event (time, date, description).

#### 5. Book a Performer for an Event

- **Description:** The club reserves a specific performer for an event.
- **Prerequisites:** The performer is available for booking.

#### 6. Update Performer's Availability

- **Description:** Admin adjusts a performer’s availability for specific dates or events.

#### 7. Manage Club or Employee Profiles

- **Description:** Admin updates club or employee profiles, adding photos, bio, and availability.

#### 8. Remove Performer Profile

- **Description:** Admin permanently removes a performer’s profile.

#### 9. Create Performer Profile

- **Description:** Admin creates a new profile for a performer in the system.

#### 10. Create Event Invitation

- **Description:** The club creates and sends an invitation for an upcoming event.

#### 11. Cancel Event

- **Description:** The club cancels a scheduled event.
- **Outcome:** Clients are notified of the cancellation.

### Clients

#### 13. Add Funds to My Account

- **Description:** Clients can buy funds through a third-party site to add to their profile. These funds are used to pay for performances.

#### 14. Pay for Premium Membership

- **Description:** The client pays for premium features.

#### 15. Add Personal Information

- **Description:** Users add personal information to their profile (e.g., name, contact).

#### 16. Create a Reservation

- **Description:** Clients book a performer for a specific time slot.
- **Prerequisites:** The performer has available slots. And user has selected a performer of his liking.

- **Active actors :**
  - Client
  - Performer
  - System

- **Main flow :**
  - User selects a time slot and clicks "Reserve."  
  - System checks the performer's availability for the selected slot.  
  - If available, the reservation is created for the performer.  
  - System notifies the performer of the new reservation.
  - System notifies the client that the reservation is pending confirmation.
  - Performer reacts to reservation (accepts or rejects).

#### 17. View Performers

- **Description:** Clients view a list of available performers.

#### 18. View Performer Profiles

- **Description:** Clients view details of a selected performer’s profile.

#### 19. View Performer Reviews

- **Description:** Clients view reviews and ratings of a selected performer.

#### 20. View Performer Availability

- **Description:** Clients view the availability calendar of a performer.

### Performers

#### 21. Confirm Booking

- **Description:** Performers confirm an event booking.

- **Active actors :**
  - Performer
  - System

- **Main flow :**  
  - User reviews the details of the booking request.  
  - User clicks "Confirm Booking."  
  - System updates the booking status to "Confirmed."  
  - System notifies the client of the confirmation.

#### 22. Reject Booking

- **Description:** Performers reject a booking if unable to accommodate or for other reasons.

- **Active actors :**
  - Performer
  - System

- **Main flow :**  
  - User reviews the details of the booking request.  
  - User clicks "Reject Booking."  
  - System notifies the client of the rejection.
  - System deletes the booking.

#### 23. Cancel Confirmed Booking

- **Description:** Performers cancel a previously confirmed booking.
- **Outcome:** The client is informed of the cancellation.

- **Active actors :**
  - Performer
  - System
  - Customer

- **Main flow :**
  - User selects the booking to cancel.
  - User clicks "Cancel Booking" and provides a reason.
  - System notifies the client of the cancellation and suggests alternative performers (if applicable).
  - System deletes the booking.  

#### 24. Report a Client

- **Description:** Performers report inappropriate client behavior.
- **Prerequisites:** The client participated in an event or performance, and there was problematic behavior.

- **Active actors :**
  - Performer
  - System

- **Main flow :**
  - User navigates to the "Completed Performances" section.  
  - User selects the event involving the client.
  - User clicks "Report Client" and provides details of the inappropriate behavior.  
  - System flags the report for review and notifies the appropriate team.
  - System issues a warning/suspension/ban to the client.
  - System updates user's profile so that performer can't be booked by the reported client.
  - System notifies the performer of the action taken.

#### 25. Rate a Client

- **Description:** Performers leave a review and rating for a client based on their experience.
- **Prerequisites:** The performer has completed a booking with the client, and the event occurred.

- **Active actors :**
  - Performer
  - System

- **Main flow :**
  - User navigates to the "Completed Performance" section.  
  - User selects the event involving the client.  
  - User clicks "Rate Client."  
  - User provides a rating and optional review.  
  - System saves the rating and associates it with the client’s profile.  

### System Admin

#### 26. Blacklist a Client

- **Description:** The system admin places a client on the blacklist for repeated violations of rules.

#### 27. Register a Club

- **Description:** Clubs register with the system and create an account.

#### 28. Assign Performer to a Club

- **Description:** A performer is added as an employee of a club.
- **Prerequisites:** The performer requests collaboration with the club, and the club confirms.

### List
  
- [ ] Register a New User @FrysarovaKaterina
- [ ] Login @FrysarovaKaterina
- [ ] Report a Review @GlycerolVeinz
- [ ] Respond to a Review @GlycerolVeinz
- [ ] Edit Event Details @zlochina
- [ ] Book a Performer for an Event @FrysarovaKaterina
- [ ] Update Performer's Availability @anokhver
- [ ] Manage Club or Employee Profiles @anokhver
- [ ] Remove Performer Profile @anokhver
- [ ] Create Performer Profile @anokhver
- [ ] Create Event Invitation @zlochina
- [ ] Cancel Event @zlochina
- [ ] Add Funds to My Account @panyuars
- [ ] Pay for Premium Membership @panyuars
- [ ] Add Personal Information @panyuars
- [ ] Create a Reservation @GlycerolVeinz
- [ ] View Performers @FrysarovaKaterina
- [ ] View Performer Profiles @FrysarovaKaterina
- [ ] View Performer Reviews @FrysarovaKaterina
- [ ] View Performer Availability @FrysarovaKaterina
- [ ] Confirm Booking @GlycerolVeinz  
- [ ] Reject Booking @GlycerolVeinz
- [ ] Cancel Confirmed Booking @GlycerolVeinz
- [ ] Report a Client @GlycerolVeinz
- [ ] Rate a Client @GlycerolVeinz
- [ ] Blacklist a Client @zlochina
- [ ] Register a Club @panyuars
- [ ] Assign Performer to a Club @anokhver

### Notes from GlycerolVeinz on Use Cases

- Represent interactions between actors (users or external systems) and the system
- Good use case diagram should identify actors and their roles, be simple and understandable, include key scenarios, correctly use relationships, and maintain logical organization.

#### Example

- Login to Application
  - Actor: Client
  - Description: The client logs into the application using a username and password or social media credentials.

## Notes for changes / updates

- Pick better names for use cases
- [^1] Not in our case, events should be only displayed to lure in clients. Also strippers are reserved for events (can't be reserved by a client while they are on an event)
- [^2] Need to talk this out with a team
- Don't you dare to model login !!!
- In processes description use mostly User / System (general naming) **if possible**
- [^3] Don't write *"obvious"* conditions
- Separate use cases by number (like in BRQs) maybe ddifferentiate by main actor ?
- Usual mistakes
  - Model shows in-system navigation
  - Model uses system in stead of Time actor
  - Wrong way onf *"Include"* / *"Exclude"*
  - Model encapsulates time hierarchy
- Don't make it actor-centric
