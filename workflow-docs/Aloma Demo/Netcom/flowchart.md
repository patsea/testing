```mermaid
flowchart TD
    A[Lead Submits Form] --> B{Valid Contact Information?}
    B -->|"Yes"| C[Create Contact Record]
    B -->|"No"| D[Log Invalid Submission]
    
    C --> E[Analyze Contact Profile]
    E --> F{Existing Customer?}
    
    F -->|"Yes"| G[Update Customer Record]
    F -->|"No"| H[Create New Lead Profile]
    
    G --> I[Check Account Status]
    H --> J[Lead Qualification Process]
    
    I --> K{Account Active?}
    K -->|"Yes"| L[Route to Account Manager]
    K -->|"No"| M[Route to Reactivation Team]
    
    J --> N{Qualified Lead?}
    N -->|"Yes"| O[Assign to Sales Team]
    N -->|"No"| P[Add to Nurture Campaign]
    
    L --> Q[Send Welcome Message]
    M --> R[Send Reactivation]
