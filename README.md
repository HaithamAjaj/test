#### URL:

http://localhost:3000/data-gncwell/development/appointment_deletion

- _api_key_ must be provided in the cookie header.

#### Method:

POST

#### Body:

- The body is JSON
- The _id_ is the appointment id and it must be provided.
- appointment id can be fetched from Get-Appointments feature.
- Delete recurring is optional and when It’s checked is true then the recurring appointment will be deleted, and if you don’t provide it in the body, it’s false by default.

```JSON
{
    "id": "27130",
    "deleteRecurring":false
}
```

### Response:

- If it is successful, it will return the _id_ of deleted appointment and the message field contain null like the following:

```JSON
{
    "data": {
        "deleteAppointment": {
            "appointment": {
                "id": "27130"
            },
            "messages": null
        }
    }
}
```

- If the _id_ wasn’t specified the following result will appear:

```JSON
{
    "error": true,
    "message": "id value must be provided"
}
```

- If the provided id was incorrect, the response will contain a message of _"Request failed with status code of 404"_
