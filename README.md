### getNotifications

#### URL:

http://localhost:3000/data-gncwell/development/notifications

- _api_key_ must be provided in the cookie header.

#### Method:

POST

#### Body:

- The body is JSON
- read_status: This turns to true if the user clicks on the notification.
- seen_status: This turns to true if the user loads the notification.
- _NoteNotifications_ means message notification.

```JSON
{
    "read_status": false,
    "seen_status": false,
    "types": ["NoteNotification","AppointmentNotification"]
}
```

### Response:

```JSON
{
    "data": {
        "notificationCount": 2,
        "notifications": [
            {
                "id": "632072",
                "type": "AppointmentNotification",
                "message": "has a new appointment with you",
                "created_at": "2021-08-25 17:00:24 +0300",
                "creator_user_name": "scott.saeger@gnc.com -",
                "other_party_id": "17697",
                "associated_object": "26784",
                "link": "/appointments?rel_appt_id=26784&rel_appt_date=2021-08-25 12:00:00 +0300",
                "link_string": "/appointments?rel_appt_id=26784&rel_appt_date=2021-08-25 12:00:00 +0300",
                "read": null,
                "seen": false,
                "other_party": {
                    "full_name": "Haitham Ajaj",
                    "id": "17697"
                },
                "user": {
                    "full_name": "scott.saeger@gnc.com -",
                    "id": "17177"
                }
            },
            {
                "id": "632071",
                "type": "NoteNotification",
                "message": "has sent you a message",
                "created_at": "2021-08-25 16:59:39 +0300",
                "creator_user_name": "scott.saeger@gnc.com -",
                "other_party_id": "17697",
                "associated_object": "16781",
                "link": "/conversations",
                "link_string": "/conversations/16781",
                "read": null,
                "seen": false,
                "other_party": {
                    "full_name": "Haitham Ajaj",
                    "id": "17697"
                },
                "user": {
                    "full_name": "scott.saeger@gnc.com -",
                    "id": "17177"
                }
            }
        ]
    }
}
```

- I used the Following query to get these data:

```GraphQL
query getNotifications(
        $types: [String],
        $seen_status: Boolean,
        $read_status: Boolean,
    ){
        notificationCount(
        types: $types
        seen_status: $seen_status
        read_status: $read_status
        )

        notifications(
          types:$types
          seen_status: $seen_status
          read_status: $read_status
      ){
          id
          type
          message
          created_at
          creator_user_name
          other_party_id
          associated_object
          link
          link_string
          read
          seen
          other_party{
              full_name
              id
          }
          user{
              full_name
              id
          }
        }
    }
```
