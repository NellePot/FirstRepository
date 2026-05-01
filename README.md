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
