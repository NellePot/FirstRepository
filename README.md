#### Visual Diagram

##### WITHOUT Factory Pattern

```mermaid
flowchart TB
        direction TB

        A[Registration] --> B["if type == 'manual':<br/>create UserGeneratedProfile()<br/>elif type == 'facebook':<br/>create AIFBProfile()<br/>elif type == 'instagram':<br/>create AIIGProfile()<br/>elif type == 'x':<br/>create AIXProfile()"]

        B --> C["❌ Repeated LOGIC."]
        B --> D["❌ Hard to MODIFY."]

        E[Profile Edit] --> F["if type == 'manual':<br/>create UserGeneratedProfile()<br/>elif type == 'facebook':<br/>create AIFBProfile()<br/>elif type == 'instagram':<br/>create AIIGProfile()<br/>elif type == 'x':<br/>create AIXProfile()"]

        F --> G["❌ Profile creation logic<br/>is repeated again."]

        C --> H["Problem: Create/Modify profiles?<br/>Update multiple files."]
        G --> H
    end
```

##### WITH Factory Pattern

```mermaid
flowchart TB
            direction TB
    
            A["Registration / Profile Edit"] --> B["ProfileFactory.<br/>create(profile_type, data)"]
    
            B --> C["✅Factory decides what profile type to create"]
    
            C --> D["UserGeneratedProfile"]
            C --> E["AIFBProfile"]
            C --> F["AIIGProfile"]
            C --> G["AIXProfile"]
    
            D --> H["koUPle Profile Created"]
            E --> H
            F --> H
            G --> H
    
            H --> I["✅ Profile creation logic <br/>is centralized"]
            I --> J["✅ Main code does not need <br/>to know every exact class"]
            J --> K["✅ Easier to add new<br/>profile types later"]
        end
```
