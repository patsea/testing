```mermaid
flowchart TD
    A[Lead Inquiry Received] --> B{Lead Information Available?}
    
    B -->|"Yes"| C[Add Lead to CRM System]
    B -->|"No"| D[Request Additional Information]
    
    C --> E[Generate AI Response]
    D --> E
    
    E --> F[Send Personalized Response]
    
    F --> G[Schedule Follow-up Activity]
    
    G --> H[Update Lead Status]
    
    H --> I{Requires Further Action?}
    
    I -->|"Yes"| J[Create Task Assignment]
    I -->|"No"| K[Mark Process Complete]
    
    J --> L[Notify Sales Team]
    
    L --> M[Lead Nurturing Initiated]
    
    M --> N[Process Complete]
    K --> N
    
    %% Professional styling
    classDef primary fill:#1E3A8A,stroke:#1E40AF,stroke-width:2px,color:#fff,font-weight:600
