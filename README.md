##### Without Factory Pattern

```mermaid
flowchart TD
    A[User starts profile creation] --> B{Profile type}

    B --> C[Registration code creates UserGeneratedProfile]
    B --> D[Registration code creates AIFBProfile]
    B --> E[Registration code creates AIIGProfile]
    B --> F[Registration code creates AIXProfile]

    C --> G[Problem: registration code knows every profile class]
    D --> G
    E --> G
    F --> G

    G --> H[Problem: adding a new profile type means editing main code again]
```

##### With Factory Pattern

```mermaid
flowchart TD
    A[User starts profile creation] --> B[Send profile_type and data to ProfileFactory]

    B --> C{ProfileFactory decides what to create}

    C --> D[UserGeneratedProfile]
    C --> E[AIFBProfile]
    C --> F[AIIGProfile]
    C --> G[AIXProfile]

    D --> H[koUPle Profile Created]
    E --> H
    F --> H
    G --> H

    H --> I[Benefit: profile creation is centralized]
    I --> J[Adding a new profile type only updates the factory]
```
