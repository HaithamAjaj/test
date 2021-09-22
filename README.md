### getConversations

#### URL:

http://localhost:3000/data-gncwell/development/conversations

- _api_key_ must be provided in the cookie header.

#### Method:

GET

### Response:

```JSON
{
    "data": {
        "conversations": [
            {
                "id": "16781",
                "conversation_memberships_count": 2,
                "dietitian_id": "17177",
                "patient_id": "17697",
                "includes_multiple_clients": false,
                "updated_at": "2021-09-07 08:58:23 +0300",
                "last_message_content": "test1",
                "last_note_viewed_id": "162891",
                "owner": {
                    "full_name": "scott.saeger@gnc.com -"
                },
                "invitees": [
                    {
                        "id": "17697",
                        "full_name": "Haitham Ajaj",
                        "active": true,
                        "timezone": "Asia/Jerusalem"
                    }
                ]
            },
            {
                "id": "17242",
                "conversation_memberships_count": 3,
                "dietitian_id": null,
                "patient_id": null,
                "includes_multiple_clients": true,
                "updated_at": "2021-08-26 23:30:06 +0300",
                "last_message_content": "\nHi everyone\n\n",
                "last_note_viewed_id": null,
                "owner": {
                    "full_name": "scott.saeger@gnc.com -"
                },
                "invitees": [
                    {
                        "id": "17697",
                        "full_name": "Haitham Ajaj",
                        "active": true,
                        "timezone": "Asia/Jerusalem"
                    }
                ]
            }
        ]
    }
}
```

- The query that was used

```graphQL
query getConversations{
      conversations{
          id
          conversation_memberships_count
          dietitian_id
          patient_id
          includes_multiple_clients
          updated_at
          last_message_content
          last_note_viewed_id
          owner{
              full_name
          }
          invitees {
              id
              full_name
              active
              timezone
          }
      }
    }
```
