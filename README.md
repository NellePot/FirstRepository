## FACTORY

#### Visual Diagram

##### Without Factory Pattern

```mermaid
flowchart TB
    subgraph W["WITHOUT Factory"]
        direction TB

        A[Registration] --> B["if type == 'manual':<br/>create UserGeneratedProfile()<br/>elif type == 'facebook':<br/>create AIFBProfile()<br/>elif type == 'instagram':<br/>create AIIGProfile()<br/>elif type == 'x':<br/>create AIXProfile()"]

        B --> C["❌ Logic is DUPLICATED"]
        B --> D["❌ Harder to modify later."]

        E[Profile Edit] --> F["if type == 'manual':<br/>create UserGeneratedProfile()<br/>elif type == 'facebook':<br/>create AIFBProfile()<br/>elif type == 'instagram':<br/>create AIIGProfile()<br/>elif type == 'x':<br/>create AIXProfile()"]

        F --> G["❌ Same profile creation logic is<br/>repeated again"]

        C --> H["Problem: Create/Modify profiles?<br/>Update multiple files."]
        G --> H
    end
```
##### WITH Factory Pattern

```mermaid
flowchart TD
    subgraph W["WITH Factory"]
        direction TB

        A["Registration / Profile Edit"] --> B["ProfileFactory.<br/>create(profile_type, data)"]

        B --> C["✅Factory decides what<br/>profile type to create"]

        C --> D["UserGeneratedProfile"]
        C --> E["AIFBProfile"]
        C --> F["AIIGProfile"]
        C --> G["AIXProfile"]

        D --> H["koUPle Profile Created"]
        E --> H
        F --> H
        G --> H

        H --> I["✅ Profile creation<br/>logic is centralized"]
        I --> J["✅ Main code does not<br/>need to know every exact class"]
        J --> K["✅ Easier to add new<br/>profile types later"]
    end
```

# OBSERVER

#### Visual Diagram

##### WITHOUT Observer Pattern

```mermaid
flowchart TB
    subgraph W["WITHOUT Observer Pattern"]
        direction TB

        A[User A hearts User B] --> B{Did User B heart back?}
        B -->|Yes| C[MatchService creates match]

        C --> D["sendMatchNotification()"]
        C --> E["enableDirectMessage()"]
        C --> F["recordSocialActivity()"]
        C --> G["generateKopiIcebreaker()"]
        C --> H["refreshMatchSuggestions()"]
        C --> I["updateUnreadMatchCount()"]

        D --> J["❌MatchService manually updates Notifications"]
        E --> K["❌MatchService manually updates Chat or DM"]
        F --> L["❌MatchService manually updates Activity Log"]
        G --> M["❌MatchService manually triggers Kopi"]
        H --> N["❌MatchService manually refreshes suggestions"]
        I --> O["❌MatchService manually updates counters"]

        J --> P["❌Problem: Match logic becomes crowded and tightly coupled"]
        K --> P
        L --> P
        M --> P
        N --> P
        O --> P

        P --> Q["Add a new match-related feature?<br/>Edit MatchService again."]
    end
```

##### WITH Observer Pattern

```mermaid
flowchart TB
    subgraph O["WITH Observer Pattern"]
        direction TB

        A[User A hearts User B] --> B{Did User B heart back?}
        B -->|Yes| C[Match Event Created]

        C --> D["✅notifyObservers(match)"]

        D --> K["Show match notification"]
        D --> L["Enable direct message"]
        D --> M["Record social activity"]
        D --> N["Kopi suggests an opening message"]
        D --> P["Refresh possible matches"]
        D --> Q["Update match or message count"]

        K --> R["✅Each feature reacts on its own"]
        L --> R
        M --> R
        N --> R
        P --> R
        Q --> R

        R --> S["Add a new feature?<br/>Just add another observer."]
    end
```

# ADAPTER

#### Visual Diagram

##### WITHOUT Adapter Pattern

```mermaid
flowchart TB
    subgraph W["WITHOUT Observer Pattern"]
        direction TB
    A["koUPle App"]

    A --> B["IF Facebook:<br/>read full_name,<br/>about,<br/>likes,<br/>photos"]
    A --> C["ELIF Instagram:<br/>read username,<br/>bio,<br/>followed_topics,<br/>media"]
    A --> D["ELIF X:<br/>read display_name,<br/>profile_description,<br/>hashtags,<br/>profile_images"]

    B --> E["❌Scattered platform-<br/>specific logic<br/>❌Hard to maintain<br/>❌Hard to add<br/>new platforms"]
    C --> E["❌Scattered platform-<br/>specific logic<br/>❌Hard to maintain<br/>❌Hard to add<br/>new platforms"]
    D --> E["❌Scattered platform-<br/>specific logic<br/>❌Hard to maintain<br/>❌Hard to add<br/>new platforms"]

    E --> H["koUPle must understand every<br/>social media API directly"]
end
```





