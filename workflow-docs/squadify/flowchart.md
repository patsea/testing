```mermaid
flowchart TD
    A[Lead Form Submission] --> B{Valid Email Address?}
    
    B -->|"Yes"| C[Contact Registration]
    B -->|"No"| D[Form Validation Error]
    D --> E[End - Error State]
    
    C --> F[AI Content Analysis]
    F --> G[Lead Scoring Engine]
    G --> H[CRM Integration]
    
    H --> I{Lead Score Threshold?}
    
    I -->|"High Priority"| J[Sales Alert Notification]
    I -->|"Standard"| K[Marketing Automation Queue]
    
    J --> L[Account Assignment]
    K --> M[Nurture Campaign Enrollment]
    
    L --> N[Lead Processing Complete]
    M --> N[Lead Processing Complete]
    
    %% Professional styling
    classDef primary fill:#1E3A8A,stroke:#1E40AF,stroke-width:2px,color:#fff,font-weight:600
    classDef success fill:#059669,stroke:#
