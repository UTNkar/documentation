---
title: "Membership Verification"
weight: 5
---

UTN has updated its membership verification system to Unicore, provided by Mecenat. Unicore is now a vital component of Project Moore, offering user information and membership status. This is important for events where being a UTN member entitles you to discounted prices.

Membership verification can be accessed at [utn.se/medlemskoll](https://www.utn.se/medlemskoll "Member Check").

To create a UTN account or a local superuser account, being registered in the Unicore system is required.

## API

Membership verification is also available through an API, which can be integrated with websites, apps, etc. For API usage, send a **POST** request to `https://utn.se/member_check_api/`.

### Params

The **POST** request should include a JSON object with a key/value pair of `ssn` and the individual's 'personnummer' (social security number). The 'personnummer' should be formatted as either 10 or 12 digits, with an optional dash (-). Set the content type to "application/json".

Example: `{'ssn':'980102-1234'}`

### Response

The API responds with a JSON string, and the appropriate HTTP status code will be set.

#### Success

HTTP Status Code: 200

Response: `{ "is_member": true }` or `{ "is_member": false }`

#### Errors

#### Internal Server Error

HTTP Status Code: 500

Response: Empty

#### Bad Request

HTTP Status Code: 400

Response: `{ "error": "Personnummer: A message describing the error" }`
