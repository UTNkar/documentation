+++
title = "Raffle entries"
date =  2020-11-11T10:02:31+01:00
weight = 10
+++

## Participation
A _raffle entry_ is submitted by a user who wants to participate in a raffle.
If a user wants to partake in, for example, the River rafting event, they will have to submit a raffle entry.
Raffle entries are submitted to the registration system by visiting `/register` and filling in a form.
The form may also be reachable through the main page. Raffle entries can only be submitted during a certain time
window specified by the site administrator. For example, the river rafting event may only allow raffle entries to be
submitted prior to the river rafting pub typically held in February.

In the registration system codebase, the `RaffleEntry` model represents a single raffle entry. Extensions and
modifications of the `RaffleEntry` model should not be done directly, but rather through creating subclasses
(which should also be [subtypes!](https://www.cs.princeton.edu/courses/archive/fall98/cs441/mainus/node12.html))
that derive from `RaffleEntry`.

## States
Raffle entries have an associated _state_, depending on user actions, if raffles have been held, and what the
result was for a single raffle.

- New raffle entries start out as having _mail unconfirmed_, until the user clicks the link sent by the system to the mail they provided.
- Confirmed raffle entries are by default _waiting_ until a raffle has been held.
- Once a raffle has been held, a raffle entry is either _won_ or _lost_.
  - Raffle entry holders who have won can claim their place, making them _accepted_.
  - Raffle entry holders who have won but not claimed their place until the next raffle are made _lost_.
  - Raffle entry holders who have won but decline their place are made _declined_, which is a final state.
- Raffle entry holders who have lost can reapply, once again putting them in _waiting_.
- Raffle entry holders who are accepted will be able to register an account, making them _confirmed_, which is a final state.

Currently, there is no mechanism to punish or otherwise correct participants who have claimed their place but not created their account.
In such an event, the event hosts should contact the participant in question.
