# Business plan for Sinners application

## Table of contents
1. [Business goals](#business-goals)
    1. [Primary Business Goals](#primary-business-goals)
2. [Justification of the Project](#justification-of-the-economic-feasibility-of-the-project)
3. [Business models](#business-models)
    1. [Business domain model](#business-domain-model)
    2. [Business process model](#business-process-model)
    3. [Business requirements](#business-requirements)
        1. [Development team requirements](#brq-0---development-team-requirements)
        2. [Client requirements](#brq-1---client-requirements)
        3. [Performer requirements](#brq-2---performer-requirements)

## Business goals
### Primary Business Goals
#### BG-01: Increase Club Attendance
As a club operator, I need to increase club's attendance, because it will lead to higher revenues.

#### BG-02: Remove Stigma and Raise Awareness of Striptease
As a strip club operator, I need to remove the stigma associated with striptease, because it will lead to wider acceptance of our service and a larger number of customers.

#### BG-03: Expand Clientele and Flexible Working Hours
As a stripper, I need more clients and flexible working hours, as this will increase my income and improve my work-life balance.

#### BG-04: Client Verification
As a stripper, I need a way to verify the reliability and trustworthiness of clients, because providing certain services (e.g., private performances) to unreliable individuals could pose a danger to me without the club's protection (e.g., risk of client aggression, breaking agreed-upon rules).

#### BG-05: Booking a Stripper
As a client, I need a discreet and convenient way to select and book a stripper, because this saves me time and maintains privacy.

back to [table of contents](#table-of-contents)
___

## Justification of the Economic Feasibility of the Project
### Costs & benefits
[Online spreadsheet with calculations](https://docs.google.com/spreadsheets/d/1pfv0A_9-FDrhvn3mnXLFHf2NRknKj2LlisVipGCFNmk/edit?gid=164423424#gid=164423424)

### Unit costs
Unit cost/cost per customer seems redundant in the context of our application as the price does not depend on the number of users unless the unexpectedly high volume requires more computation power. The only exception is the CAC (Customer Acquisition Cost), which determines how much money we spend for attracting 1 customer through marketing.

back to [table of contents](#table-of-contents)
___

## Business models
### Business domain model
- [Business domain model diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/Business%20Domain%20Model.pdf)

back to [table of contents](#table-of-contents)
___

### Business process model

#### Customer experience process
- [Customer experience process diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/BMPcustomer.pdf)
- [Customer and performer interaction diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/Custoemr%2BPerformer.pdf)

#### Club management process
- [Club management process diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/BMPadmin.pdf)
- [Club management and performer interaction diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/BMPadminperformer.pdf)
- [Club management and customer interaction diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/BMPcustomeradmin.pdf)

#### Performer experience process
- [Performer experience process diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/BMPperformer.pdf)


back to [table of contents](#table-of-contents)
___

### Business requirements
#### Business goals list
- BG-01: Increase Club Attendance
- BG-02: Remove Stigma and Raise Awareness of Striptease
- BG-03: Expand Clientele and Flexible Working Hours
- BG-04: Client Verification
- BG-05: Booking a Stripper

#### Business requirements list
##### BRQ-0** - Development team requirements
- BRQ-001 Payment system & processing
    - Ease of use and implementation of payment processing
- BRQ-002 Marketing campaigns
    - Attract new users
    - Remove stigma associated with striptease
    - Redirect users to the application
- BRQ-003 Legal department
    - Ensure compliance with the law
    - Protect the company from legal issues
    - Ensure the safety of users
##### BRQ-1** - Client requirements
- BRQ-101 Reviews
    - Leave feedback
    - Know other people opinions
- BRQ-102 Reservation of performers
    - Be certain that the performer will be available
- BRQ-103 Browsing/Scrolling performers
    - Find the performer that suits my needs
- BRQ-104 Anonymity
    - Keep my life separate from the application
##### BRQ-2** - Performer requirements
- BRQ-201 Performer's availability/dashboard
    - Manage my schedule
- BRQ-202 Performer's reviews
    - Know what people think about me
- BRQ-204 Redirection of pay
    - Possibility to ask for cash payment at my club
- BRQ-205 Blacklist
    - Block clients that are not reliable
- BRQ-206 Authentication
    - Be certain that the client is who they say they are
    - Increase my safety
- BRQ-207 Roles(tiers)
    - Differentiate between clients (prioritize some over others)
- BRQ-208 Reports
    - Report clients that are not reliable
##### BRQ-3** - Club requirements
- BRQ-301 Management system
    - Manage performers that work at my club
    - Manage the club's reputation
- BRQ-302 Reviews
    - Know what people think about my club
    - Attract new clients
    - Maintain a good reputation
    - React to negative feedback
- BRQ-303 Event page
    - Attract new clients
    - Spark interest in regulars

##### *How to read the list:*
As a [BRQ-Section] I need [BRQ-Requirement Name] because [Reasoning]

#### Diagram of BG and BRQ relationship
[Business goals and requirements diagram](https://github.com/GlycerolVeinz/sinSemestralWork/blob/consultation3/business/business/models/v0.0.3/BG%2BBRQ-sinners.pdf)

back to [table of contents](#table-of-contents)
___
