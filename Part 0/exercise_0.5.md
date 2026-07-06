```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: User writes note and clicks "Save"

    Note right of browser: 1. The browser prevents the default form submit<br/>2. The browser adds the new note to the local 'notes' list<br/>3. The browser calls redrawNotes() to update the UI

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of browser: Payload: {content, date}
    server-->>browser: HTTP 201 Created ({"message": "note created"})
    deactivate server

    Note right of browser: The application does NOT reload; the UI is already updated
```
