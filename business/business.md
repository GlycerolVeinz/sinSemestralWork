# Business plan for Sinners application

## Table of contents
1. [Business goals](#business-goals)
   1. [Primary Business Goals](#primary-business-goals)
   2. [Sub-Goals](#sub-goals)
2. [Justification of the Project](#justification-of-the-economic-feasibility-of-the-project)
3. [Business models](#business-models)
    1. [Business domain model](#business-domain-model)
    2. [Business process model](#business-process-model)
    3. [Business requirements](#business-requirements)

## Business goals [^1]

### Primary Business Goals

#### BG01: Functional Operation of the Application
##### Description:
This goal is considered fulfilled if we launch an application that is **functional, secure, reliable**, and ready for use by customers. Additionally, regular maintenance and a problem-solving system must be ensured to prevent sudden outages in the future.

#### BG02: Clientele Growth
##### Description:
This goal aims to establish a **long-term growth trend** in the number of clients, including both **strippers and customers**, as well as securing partnerships with clubs and eventually expanding into other cities.

#### BG03: Maintain a Good Reputation and Attractiveness for New and Existing Customers
##### Description:
The main pillar of this business goal is to **maintain and improve the positive media image** of our organization and striptease as a whole. Additionally, for our application, it is crucial to ensure the **functionality and reliability** of the review system and actively address any issues that arise to prevent mistrust due to technical or human failures.

### Sub-Goals

#### Sub-Goal 01: Actively Address Issues Raised by Customers → BG03
- This involves managing **blacklists** and excluding **difficult or inappropriate customers** as well as providing **functional customer support**.

#### Sub-Goal 02: Resolve Potential Legal Issues → BG03
- To achieve this goal, it is necessary to **anticipate potential problems** and resolve them, ensuring the **complete legal integrity and trustworthiness** of our organization. Specifically, we need to work with the **legal department** to create a strategy to address potential issues.

#### Sub-Goal 03: Create a Positive Public Perception of Striptease → BG02, BG03
- This goal is considered fulfilled if a **positive (or at least neutral) media image** of striptease is created, presenting it as a **unique form of art** that requires **talent and dedication** at a professional level, deserving proper recognition and appreciation.

#### Sub-Goal 04: Establish a Functional Marketing Model → BG02, BG03
- To achieve this goal, we need to practically test different forms of marketing, determine which is best suited for our purposes, and then use it consistently.

#### Sub-Goal 05: Expand to Other Cities → BG02
- This goal requires expanding operations to other cities, including all necessary **adjustments to the business model** for adapting to the specific environment.

#### Sub-Goal 06: Application Development → BG01
- The goal requires the creation of a **high-quality and user-friendly application** for our project.

#### Sub-Goal 07: Ensure a Competent Team for Technical Issue Resolution → BG01
- To achieve this goal, it is necessary to establish a **team capable of independently addressing technical issues** within the application, and to test its effectiveness during real operation.

back to [table of contents](#table-of-contents)
___

## Justification of the Economic Feasibility of the Project

### Costs & benefits [^2][^3] 
[Online spreadsheet with calculations](https://docs.google.com/spreadsheets/d/1pfv0A_9-FDrhvn3mnXLFHf2NRknKj2LlisVipGCFNmk/edit?gid=164423424#gid=164423424)

### Unit costs [^4]
Unit cost/cost per customer seems redundant in the context of our application as the price does not depend on the number of users unless the unexpectedly high volume requires more computation power. The only exception is the CAC (Customer Acquisition Cost), which determines how much money we spend for attracting 1 customer through marketing.

back to [table of contents](#table-of-contents)
___

## Business models

### Business domain model [^5]

#### Mock diagram
```mermaid
classDiagram
    class Tier{
        %% Maybe change name of tiers to something more in theme with strip clubs
        <<enumeration>>
        CLAY
        BRONZE
        SILVER
        GOLD
        PLATINUM
    }

    class Customer{
        -String nickname
        -Tier tier

        +makeReservation()
        +leaveReview()
        %% Browse function is swiping like on tinder
        +browseStrippers()
        %% List function is a list of all strippers
        +listStrippers()
    }

    class ClubAdmin{
        -String nickname

        +reportCustomer()
    }

    class Stripper{
        -String nickname
        -BufferedImage photo
        -Club workPlace

        +leaveReview()
        +reportCustomer()
        +acceptReservation()
    }

    class Club{
        -String name
        -Address address
    }

    class Reservation{
        -LocalDateTime date
        -Customer customer
        -Stripper stripper
    }

    class Payment{
        -LocalDateTime date
        -Customer customer
        -Reservation reservation
        -double amount
    }

    %% Relationships
    Customer "1" --> "1" Tier : "is in"
    Stripper "1..*" --> "1" Club : "works at"
    ClubAdmin "1..*" --> "1" Club : "manages"
    Reservation "*" --> "1" Customer : "is made by"
    Reservation "*" --> "1" Stripper : "is for"
```
- This is purely mock diagram, the actual model should be made in EA
- for better model check presentation slide "Main business events"

back to [table of contents](#table-of-contents)
___

### Business process model [^6]

#### Mock example diagram
##### User experience process
```mermaid
flowchart TD
    start((Start)) --> login
    login --> mainMenu
    mainMenu --> mainMenuAction{choose action}
    mainMenuAction -->|browse strippers| scrollStrippers
        scrollStrippers -->|inspect| stripper
        stripper --> reserve
        reserve --> decision{Stripper decides}
        decision -->|Stripper declines| mainMenuAction
        decision -->|Stripper accepts| confirm
            confirm --> pay[Pay at location after the show]
            pay --> afterShow{after show}
                afterShow -->|exit| END((end))
                afterShow -->|leave review| review
                    review -->|leave review for stripper| stripper

    mainMenuAction -->|list strippers| listedStrippers
        listedStrippers -->|inspect| stripper
    
    mainMenuAction -->|exit| END
    mainMenuAction -->|edit data| profile
        profile --> profileAction{choose action}
        profileAction --> |edit| profile
        profileAction --> |save| mainMenuAction
        profileAction --> |leave review from history| review
```

##### Club management process
```mermaid
flowchart TD
    start((Start)) --> login
    login --> mainMenu
    mainMenu --> clubMenu
    clubMenu --> decision{Choose action}
    decision -->|Manage events| eventsMenu[Events menu]
        eventsMenu --> eventAction{Choose action}
        eventAction -->|Create event| event
        eventAction -->|Edit event| event
        eventAction -->|Delete event| eventsMenu
        eventAction -->|Add stripper| strippersMenu

    decision -->|Manage strippers| strippersMenu
        strippersMenu --> stripperAction{Choose action}
        stripperAction -->|Add stripper to list| stripper
        stripperAction -->|Edit stripper data| stripper
        stripperAction -->|Remove stripper| strippersMenu
        stripperAction -->|Reserve stripper for event| event
    
    decision -->|Manage reviews| reviewsMenu
        reviewsMenu--> reviewsDecision{Choose action}
        reviewsDecision-->|React to review| review
        reviewsDecision-->|Report review| reviewsMenu

    decision -->|Manage reports| reportsMenu
        reportsMenu--> reportsAction{Choose action}
        reportsAction-->|Resolve report| reportsMenu

    eventsMenu --> endOfWork{End of managing}
    reportsMenu --> endOfWork{End of managing}
    reviewsMenu --> endOfWork{End of managing}
    strippersMenu --> endOfWork{End of managing}

    endOfWork --> END((End))
```

##### Stripper experience process
```mermaid
flowchart TD
    start((Start)) --> login
    login --> mainMenu
    mainMenu --> mainMenuAction{Choose action}
    mainMenuAction --> |manage reservations| reservationsMenu
        reservationsMenu --> reservationAction{Choose action}
        reservationAction --> |Decline reservation| reservationsMenu
        reservationAction --> |Accept reservation| reservation
            reservation --> afterStripAction{After Performance}
            afterStripAction --> |leave review| review
            afterStripAction --> |report customer| reservationsMenu            
            review --> |exit| END((end))

        reservationAction --> |Set availability| reservationsMenu
        reservationAction --> |exit| END((end))

    mainMenuAction --> |manage payments| paymentsMenu
        paymentsMenu --> paymentAction{Choose action}
        paymentAction --> |Redirect payment| payment
        paymentAction --> |Withdraw payment| paymentsMenu 
```

- These are purely mock diagrams, the actual models should be made in EA
- for better model check presentation slide "Main business events" and "Main business goals"

back to [table of contents](#table-of-contents)
___

### Business requirements [^7]
#### Business goals list
1. **BG01: Functional Operation of the Application**
2. **BG02: Clientele Growth**
3. **BG03: Maintain a Good Reputation and Attractiveness for New and Existing Customers**

#### Business requirements list
| ID | Requirment Name |
|----|-----------------|
| BRQ-001 | Payment system & processing |
| BRQ-002 | Marketing campaigns |
| BRQ-003 | Legal department |
| BRQ-101 | User authentication |
| BRQ-102 | User roles(tiers) | 
| BRQ-103 | User reviews | 
| BRQ-104 | User reports | 
| BRQ-105 | User reservations |
| BRQ-106 | User blacklist | 
| BRQ-107 | Browsing for users | 
| BRQ-108 | User's anonymity |
| BRQ-201 | Stripper's availability/dashboard |
| BRQ-202 | Stripper's reviews |
| BRQ-204 | Redirection of pay |
| BRQ-301 | Club's management system |
| BRQ-302 | Club's reviews |
| BRQ-303 | Club's event page |

```mermaid
graph LR
    %% Define Goals
    BG01[Functional Operation of the Application]
    BG02[Clientele Growth]
    BG03[Maintain Good Reputation and Attractiveness for Customers]

    %% Define Business Requirements
    BRQ001[Payment System & Processing]
    BRQ002[Marketing Campaigns]
    BRQ003[Legal Department]
    BRQ101[User Authentication]
    BRQ102[User Roles Tiers]
    BRQ103[User Reviews]
    BRQ104[User Reports]
    BRQ105[User Reservations]
    BRQ106[User Blacklist]
    BRQ107[Browsing for Users]
    BRQ108[User's Anonymity]
    BRQ201[Performer Availability/Dashboard]
    BRQ202[Performer Reviews]
    BRQ204[Redirection of Payments]
    BRQ301[Club's Management System]
    BRQ302[Club's Reviews]
    BRQ303[Club's Event Page]

    %% Traceability Arrows (Linking Business Requirements to Business Goals)
    BG01 --> BRQ001
    BG01 --> BRQ101
    BG01 --> BRQ102
    BG01 --> BRQ103
    BG01 --> BRQ104
    BG01 --> BRQ105
    BG01 --> BRQ106
    BG01 --> BRQ107
    BG01 --> BRQ201
    BG01 --> BRQ204
    BG01 --> BRQ301

    BG03 --> BRQ103
    BG03 --> BRQ003
    BG03 --> BRQ302
    BG03 --> BRQ202
    BG03 --> BRQ108

    BG02 --> BRQ002
    BG02 --> BEQ302
    BG02 --> BRQ202
    BG02 --> BRQ108
```

back to [table of contents](#table-of-contents)
___

[^1]: Explanation - Business goals are the high-level objectives that the project aims to achieve. These could be strategic objectives, financial outcomes, or operational improvements. They guide the entire analysis by providing the rationale behind the project.

[^2]: Explanation - Total Cost of Ownership (TCO) refers to the complete cost of owning and operating the project over its lifecycle. This includes initial costs, maintenance, and other operational costs.

[^3]: Explanation - This section should list the financial and non-financial benefits the project will bring. Financial benefits could include revenue increases or cost savings, while non-financial benefits might be improvements in customer experience or brand value.

[^4]: Explanation - Unit costs refer to the cost per unit of output, such as the cost per customer, transaction, or product sold. It helps quantify the impact of the project.

[^5]: Explanation - The Business Domain Model describes the core concepts and relationships within the business. Using a UML class diagram, you can model entities (like Customers, Orders, Products) and how they interact.

[^6]: Explanation - The Business Process Model captures how business processes flow within the project. UML Activity Diagrams are used to model these processes as sequences of activities or tasks.

[^7]: Explanation - This section defines the business requirements and links them back to the business goals. A UML Requirements Diagram helps visualize how specific requirements are tied to goals.

back to [table of contents](#table-of-contents)
