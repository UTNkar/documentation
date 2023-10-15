+++
date = "2023-10-11T12:39:34+02:00"
title = "Unicore"
toc = true
weight = 15

+++

Unicore is a membership system provided my mecenat, which is 
essential for project moore since it provides user information
and membership status, which is especially important for events
since prices are cheaper when you are a UTN member. It is required
to be in the Unicore system to create a UTN account or a superuser locally. Note that you do not have
to be a member of UTN to create an account, but [registration](https://utn.se/blimedlem/) is necessary. The code for the
client is found [here](https://github.com/UTNkar/moore/blob/development/src/utils/melos_client.py).

### Unicore response objects
The User object is defined as

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

The Membership status object is defined as

    {
        "Member": bool
    }

### Unicore API-endpoints
Authentication for the following endpoints is of type Basic Auth. The endpoints
that return a User object are

https://unicorecustomapi.mecenat.com/utn/user/:ssn
https://unicorecustomapi.mecenat.com/utn/user-by-id/:id

The endpoint that returns the membership status object is

https://unicorecustomapi.mecenat.com/utn/is-member/:ssn
