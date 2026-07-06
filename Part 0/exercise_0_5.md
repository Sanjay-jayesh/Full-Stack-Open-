```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: User writes note and clicks "Save"

    Note right of browser: 1. Browser prevents default submit. 2. Browser adds note to local lsit. 3. Browser calls redrawNotes().

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of browser: Payload: {content, date}
    server-->>browser: HTTP 201 Created ({"message" : "note created"})
    deactivate server

    Note right of browser: The application does NOT reload; UI is updated.
```
