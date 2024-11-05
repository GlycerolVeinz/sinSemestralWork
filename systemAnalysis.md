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

### Notes from GlycerolVeinz
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
- Outsourced payment gate ? 

### 1. All Users - Log In
- **Description**: The user logs in to their account using login credentials.
- **Prerequisites**: The user has an active account and valid login credentials.
- **Consequences**: The user is authenticated and has access to their account.

### 2. Club Admin - Report a Review
- **Description**: The admin can flag a problematic review for investigation if it is deemed inappropriate.
- **Prerequisites**: There is a review on the profile that requires intervention.
- **Consequences**: The review is flagged and forwarded for further investigation or action.

### 3. Club Admin - Respond to a Review
- **Description**: The admin can respond to a review to provide an answer or clarify the situation.
- **Prerequisites**: The review is available for response.
- **Consequences**: The admin's response is saved and displayed alongside the review.

### 4. Club Admin - Edit an Event
- **Description**: The admin edits the details of an already created event (time, date, description).
- **Prerequisites**: The event already exists in the system.
- **Consequences**: The updated details are saved and the relevant participants are informed.

### 5. Club Admin - Book a Performer for an Event
- **Description**: A client or the club books a specific performer for an event.
- **Prerequisites**: The performer is available for booking.
- **Consequences**: The performer's booking is confirmed and added to the calendar.

### 6. Club Admin - Change Performer's Availability
- **Description**: The admin adjusts the performer's availability for specific dates or events.
- **Prerequisites**: The performer has a set profile and availability calendar.
- **Consequences**: The performer's availability is updated and visible to clients.

### 7. Club Admin - Edit Club/Staff Profile
- **Description**: The performer updates their own or a staff member's profile, adds photos, bio, and updates their calendar.
- **Prerequisites**: The profile already exists.
- **Consequences**: The profile is updated and the new information is available to clients.

### 8. Club Admin - Delete Performer Profile
- **Description**: The admin permanently deletes a performer's profile.
- **Prerequisites**: The performer’s profile is active in the system.
- **Consequences**: The performer’s profile is deleted and is no longer visible to users.

### 9. Club Admin - Create Performer Profile
- **Description**: The admin creates a new profile for a performer in the system.
- **Prerequisites**: The admin has the necessary information about the performer.
- **Consequences**: The profile is created and visible to clients.

### 10. Club Admin - Create an Event Invitation
- **Description**: The club creates an invitation for an upcoming event and sends it out.
- **Prerequisites**: The club has the permission to create and manage events.
- **Consequences**: The invitation is sent and displayed to participants.

### 11. Club Admin - Cancel an Event
- **Description**: The club cancels a planned event.
- **Prerequisites**: The event is planned and has reservations.
- **Consequences**: The event is canceled and clients are informed of the cancellation.

### 12. Club Admin - Confirm Event Booking [^1]
- **Description**: The club confirms a client's reservation for an event.
- **Prerequisites**: The client has a pending reservation.
- **Consequences**: The reservation is confirmed and the client is informed.

### 13. Club Admin - Reject Event Booking ??? [^1]
- **Description**: The club rejects a client's reservation for an event.
- **Prerequisites**: The client has a pending reservation.
- **Consequences**: The reservation is rejected and the client is informed.

### 14. Client - Pay for Premium Membership
- **Description**: The client pays for premium features (subscription).
- **Prerequisites**: The user has access to the account and selects a premium plan.
- **Consequences**: The premium membership is activated and the user has access to premium features.

### 15. Client - Provide Personal Information [^2]
- **Description**: The user adds personal information to their profile (e.g., name, contact).
- **Prerequisites**: The user has an active profile.
- **Consequences**: The information is saved to the user's profile.

### 16. Client - Make a Reservation
- **Description**: The client reserves a performer for a specific time slot.
- **Prerequisites**: The client has an active account and the performer has available times.
- **Consequences**: The reservation is confirmed and saved.

### 17. Client - View Performers
- **Description**: The client views the list of available performers.
- **Prerequisites**: The client is logged in.
- **Consequences**: The list of performers is displayed.

### 18. Client - View Performer Profile
- **Description**: The client views the details of the selected performer's profile.
- **Prerequisites**: The performer has an active profile.
- **Consequences**: The performer's profile is displayed to the client.

### Notes from GlycerolVeinz
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