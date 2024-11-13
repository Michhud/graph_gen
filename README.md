# graph_gen
Generates Mermaid JS graphs from text interactively


## Test cases
Some nice test cases:

### 1. Flow chart
```
graph TD
    A[Start] --> B{Is data valid?}
    B -- Yes --> C[Process data]
    B -- No --> D[Show error message]
    D --> E[Exit]
    C --> F{Is data complete?}
    F -- Yes --> G[Store data in database]
    F -- No --> H[Ask user to complete missing fields]
    H --> F
    G --> I{Is there a report to generate?}
    I -- Yes --> J[Generate report]
    I -- No --> K[Send notification]
    J --> L[Email report to user]
    L --> M[Exit]
    K --> N[Send success notification]
    N --> M
    M --> O[Log the process]
    O --> P[End]

    %% Sub-process for error handling
    subgraph ErrorHandling [Error Handling]
        direction TB
        D[Show error message]
        E[Exit]
    end

    %% Sub-process for database operations
    subgraph DatabaseOperations [Database Operations]
        direction LR
        G[Store data in database]
        I[Generate report]
        K[Send notification]
    end

    %% Sub-process for user interaction
    subgraph UserInteraction [User Interaction]
        direction RL
        H[Ask user to complete missing fields]
        F{Is data complete?}
    end

    %% Styling nodes and links
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#bbf,stroke:#333,stroke-width:2px
    style C fill:#bfb,stroke:#333,stroke-width:2px
    style D fill:#fbb,stroke:#333,stroke-width:2px
    style F fill:#f9f,stroke:#333,stroke-width:2px
    style G fill:#bfb,stroke:#333,stroke-width:2px
    style H fill:#ffb,stroke:#333,stroke-width:2px
    style I fill:#bbf,stroke:#333,stroke-width:2px
    style J fill:#bfb,stroke:#333,stroke-width:2px
    style L fill:#bfb,stroke:#333,stroke-width:2px
    style K fill:#f9f,stroke:#333,stroke-width:2px
    style N fill:#bbf,stroke:#333,stroke-width:2px
    style M fill:#bbf,stroke:#333,stroke-width:2px
    style O fill:#bbf,stroke:#333,stroke-width:2px
    style P fill:#f9f,stroke:#333,stroke-width:2px
```

### 2. Sequence diagram
```
sequenceDiagram
    participant A as User
    participant B as Web Server
    participant C as Database
    participant D as Third Party API
    participant E as Email Service

    A->>B: Sends login request
    B->>C: Check user credentials
    C->>B: Return credentials validation status
    B->>A: Return login success or failure
    A->>B: Sends data for processing
    B->>C: Save data to database
    C->>B: Return confirmation
    B->>D: Request external API data
    D->>B: Return API response
    B->>E: Send email notification
    E->>A: Email sent successfully
    A->>B: Logs out
    B->>C: Update session status
    C->>B: Return session update confirmation
    B->>A: Return logout success message
```