---
title: "Usuwanie spotkań"
weight: 60
---

Spróbuj dodać funkcjonalność usuwania spotkań na podstawie dotychczasowych informacji.

{{% expand title="Spróbuj napisać **samodzielnie**, zanim klikniesz :-)" %}}

```jsx
async function handleDeleteMeeting(meeting) {
    const response = await fetch(`/api/meetings/${meeting.id}`, {
        method: 'DELETE',
    });
    if (response.ok) {
        const nextMeetings = meetings.filter(m => m !== meeting);
        setMeetings(nextMeetings);
    }
}
```

{{% /expand %}}

Upewnij się, że da się usunąć spotkanie, które przed chwilą zostało dodane. Jeśli
zidentyfikujesz tutaj jakiś problem - spróbuj go naprawić.
