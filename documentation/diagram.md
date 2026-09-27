# Feature: Personal Cabinet
## Use Case: Leave Feedback

The main participants are the User and the System. The diagram illustrates how an authorised user rates a completed booking from 1 to 5 stars and optionally leaves written feedback.
```mermaid
flowchart TD
    A((Start)) --> B(User clicks Leave feedback)
    B --> C(System displays feedback form)
    C --> D(User selects rating from 1 to 5)
    D --> E(User optionally enters a comment)
    E --> F{Submit feedback?}

    F -- No --> G(Discard unsaved feedback)
    G --> H(Return to Personal Cabinet)
    H --> Z1((End))

    F -- Yes --> I{Rating selected?}
    I -- No --> J(Display validation message)
    J --> D

    I -- Yes --> K(Save feedback)
    K --> L{Feedback saved successfully?}

    L -- No --> M(Display error message)
    M --> N{Retry?}
    N -- Yes --> K
    N -- No --> Z2((End))

    L -- Yes --> O(Display confirmation message)
    O --> P(Return to Personal Cabinet)
    P --> Z3((End))
```
