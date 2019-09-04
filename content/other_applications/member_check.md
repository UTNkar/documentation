+++
title = "Member Check"
date =  2019-09-04T11:49:01+02:00
weight = 5
+++

UTN has a system to check if a person is a member or not.
This system uses the unions new member system (MELOS).

The member check can be found at [utn.se/medlemskoll](https://www.utn.se/medlemskoll "Member Check")

## API

The member check is also available as an api and can be used from a website, app etc.
To use the api, send a **POST** request to `https://www.utn.se/member_check/check_membership.php`.

### Params

In the **POST** request, you must send the social security number (personnummer) of the person you want to perform a member check on.
The social security number can be either 10 or 12 digits. A dash (-) is optional.
The social security number must be sent in the `ssn` parameter. Example:

ssn=980102-1234

### Response

The response will always have the form of a JSON string. The http status code will also be set accordingly.
The various responses are described below

#### Success

Http Status Code: 200

Response: `{is_member: true|false}`;

#### Errors

**Internal server error**

Http Status Code: 500

Response: Empty

OR

**Bad request**

Http Status Code: 400

Response: `{code: error_code, message: "A message describing the error"}`

The following error codes exist:

- **1** - The `ssn` parameter is missing
- **2** - The `ssn` parameter is empty
- **3** - The `ssn` is badly formated
