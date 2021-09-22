#### URL:

http://localhost:3000/data-gncwell/development/prescriptions

- _api_key_ must be provided in the cookie header.
- User can specifiy _status_ in query string and it accept the values [*active*, *pending*, *error*, *hidden*]

#### Method:

GET

### Response:

```JSON
{
    "data": {
        "prescriptions": []
    }
}
```

- The query that was used

```graphQL
query getPrescriptions( $status: String) {
      prescriptions( status: $status ){
        date_written
        directions
        id
        product_name
        quantity
        refills
        status
        unit
        pharmacy{
          city
          country
          id
          state
          name
          zip
          user{
            full_name
          }
        }
      }
    }
```
