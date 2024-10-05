# Business plan for Sinners application

## Business goals [^1]

## Justification of the Economic Feasibility of the Project

### Costs [^2] 

### Benefits [^3]

### Unit costs [^4]

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

___

### Business process model [^6]

#### Mock example diagram
```mermaid
flowchart TD
    start((Start)) --> a[Login]
    a --> b[Main menu]
    b --> c[Scroll strippers]
    c --> d[Select stripper]
    d --> e[Reserve]
    e -->|Stripper declines| c
    e -->|Stripper accepts| f[Confirm reservation]
    f --> g[Pay at location after the show]
```
- This is purely mock diagram, the actual model should be made in EA
- for better model check presentation slide "Main business events" and "Main business goals"

___

### Business requirements [^7]




[^1]: Explanation - Business goals are the high-level objectives that the project aims to achieve. These could be strategic objectives, financial outcomes, or operational improvements. They guide the entire analysis by providing the rationale behind the project.

[^2]: Explanation - Total Cost of Ownership (TCO) refers to the complete cost of owning and operating the project over its lifecycle. This includes initial costs, maintenance, and other operational costs.

[^3]: Explanation - This section should list the financial and non-financial benefits the project will bring. Financial benefits could include revenue increases or cost savings, while non-financial benefits might be improvements in customer experience or brand value.

[^4]: Explanation - Unit costs refer to the cost per unit of output, such as the cost per customer, transaction, or product sold. It helps quantify the impact of the project.

[^5]: Explanation - The Business Domain Model describes the core concepts and relationships within the business. Using a UML class diagram, you can model entities (like Customers, Orders, Products) and how they interact.

[^6]: Explanation - The Business Process Model captures how business processes flow within the project. UML Activity Diagrams are used to model these processes as sequences of activities or tasks.

[^7]: Explanation - This section defines the business requirements and links them back to the business goals. A UML Requirements Diagram helps visualize how specific requirements are tied to goals.
