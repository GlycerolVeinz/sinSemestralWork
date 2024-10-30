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

## Use case
### Actors
- User
  - Club's manager
  - Performer
  - Client
- Developer
- Outsourced payment gate ? 

### Notes from GlycerolVeinz
- Represent interactions between actors (users or external systems) and the system
- Good use case diagram should identify actors and their roles, be simple and understandable, include key scenarios, correctly use relationships, and maintain logical organization.

#### Example
- Login to Application
  - Actor: Client
  - Description: The client logs into the application using a username and password or social media credentials.