```mermaid
flowchart TD
    A[Lead Capture Initiated] --> B{Contact Exists in CRM?}
    B -->|"No"| C[Create New Contact Record]
    B -->|"Yes"| D[Update Existing Contact]
    
    C --> E[Generate AI Response]
    D --> E
    
    E --> F[Send Automated Reply]
    F --> G[Schedule Follow-up Tasks]
    G --> H[Update Contact Timeline]
    H --> I[Trigger Lead Scoring]
    I --> J{Lead Score Threshold Met?}
    
    J -->|"Yes"| K[Notify Sales Team]
    J -->|"No"| L[Continue Nurture Sequence]
    
    K --> M[Lead Processing Complete]
    L --> N[Add to Marketing Queue]
    N --> M
    
    %% Professional styling
    classDef primary fill:#1E3A8A,stroke:#1E40AF,stroke-width:2px,color:#fff,font-weight:600
    classDef success fill
