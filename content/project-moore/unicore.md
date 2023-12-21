---
title: "Unicore"
toc: true
weight: 15
---

Unicore, provided by Mecenat, is a critical membership system for Project Moore. It supplies important user information and membership status. This is particularly important for events where UTN members benefit from reduced prices. To create a UTN account or become a local superuser, one must be registered in the Unicore system. While UTN membership is not mandatory for account creation, completing [registration](https://utn.se/blimedlem/) is essential. The client code is available [here](https://github.com/UTNkar/moore/blob/development/src/utils/melos_client.py). In other words, the UTN user and the Unicore user are distinct entities. For a person to sign up for a UTN account and become a UTN user, they must first be registered in the Unicore system.

### Unicore Response Objects

The User object and the Membership status object have specific structures.

The **User object** structure includes details such as the user's name, social security number (SSN), contact information, and other relevant personal data:

{{% details "`User`" %}}
```python
{
    "Adress1": string,
    "Adress2": string,
    "Adress3": string,
    "AdressFromdatum": DateTime?,
    "AdressHandlid": int?,
    "AdressRegdatum": DateTime?,
    "AdressTomdatum": DateTime?,
    "Adressid": int?,
    "Adresstyp": int?,
    "Id": int,
    "Postnr": string,
    "Postort": string,
    "Alder": int?,
    "Avlidendatum": DateTime?,
    "Avplock": bool,
    "Efternamn": string,
    "Epost": string,
    "Fodelsedatum": DateTime?,
    "Fornamn": string,
    "Handlid": int,
    "Huvudpersonid": int,
    "Ingautskick": bool,
    "IngenMedlemstidning": bool,
    "Kvinna": bool,
    "Man": bool,
    "Medlemsnr": string,
    "Personnr": string,
    "Regdatum": DateTime?,
    "Sekretess": bool,
    "Tele1": bool,
    "Tele2": bool,
    "Tele3": bool,
    "Program": [
        {
            "Benamning": string,
            "Handlid": int,
            "Regdatum": DateTime?,
            "Sokordid": int
        }
    ],
    "Registrerad": bool,
    "Betalningdatum": DateTime?
}
```
{{% /details %}}

The **Membership status object** contains information regarding the user's current membership status with UTN, including whether the user is an active member:

```python
{
    "Member": bool
}
```

### Unicore API Endpoints

Authentication for accessing the API endpoints is managed through Basic Auth. The endpoints that return a User object include:

- `https://unicorecustomapi.mecenat.com/utn/user/:ssn` - Retrieves user information based on their social security number.
- `https://unicorecustomapi.mecenat.com/utn/user-by-id/:id` - Retrieves user information based on their unique identifier.

The endpoint for obtaining the Membership status object is:

- `https://unicorecustomapi.mecenat.com/utn/is-member/:ssn` - Provides the membership status of a user based on their social security number.

{{% notice note %}}
It would be beneficial to synchronize these two data sources in the future to streamline the user experience and administrative processes. For example, synchronization could be achieved by: (1) Implementing an API integration between UTN's account management system and Unicore, where user data is automatically updated in real-time or through scheduled syncs. (2) Allowing single sign-on (SSO) capabilities, where users can use their Unicore credentials to access UTN services without needing separate login details. (3) Creating a middleware application that regularly checks for updates in the Unicore system and applies them to the corresponding UTN user profiles.
{{% /notice %}}
