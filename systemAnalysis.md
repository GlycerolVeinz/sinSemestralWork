# System analysis for Sinners application

## System requirements 
### Functional

### Non-functional

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

### 12. Club Admin - Confirm Event Booking
- **Description**: The club confirms a client's reservation for an event.
- **Prerequisites**: The client has a pending reservation.
- **Consequences**: The reservation is confirmed and the client is informed.

### 13. Club Admin - Reject Event Booking
- **Description**: The club rejects a client's reservation for an event.
- **Prerequisites**: The client has a pending reservation.
- **Consequences**: The reservation is rejected and the client is informed.

### 14. Client - Pay for Premium Membership
- **Description**: The client pays for premium features.
- **Prerequisites**: The user has access to the account and selects a premium plan.
- **Consequences**: The premium membership is activated and the user has access to premium features.

### 15. Client - Provide Personal Information
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
