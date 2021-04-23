+++
date = 2021-04-23T13:59:12+02:00
title = "Adding entries"
toc = true
weight = 10

+++

Entries are added at */add-entry*. In this form the user fills in the following fields:

- **Personnummer:** The person's personnummer. This is used to find that person's agreement in the database. 
**A person must have an agreement in order to drive bocken**
- **Group:** The group the person is driving for. This determines who should pay for the journey.
The groups have been divided into main groups to make it easier to find your group.
- **Meter start and stop:** The number of kilometers on the trip meter in bocken. These determine how far you have driven.

The form also displays how many kilometers a person have driven so that they can verify that it is correct.
Finally, you have to check that you leave the car in good shape and check the recaptcha (to prevent spam).

The form then redirects you to a success page. If your agreement has expired, the success page will give the person
a notice and send an email to the klubbmästare so that both parties are aware and can contact each other to renew the agreement.

![entry form](/images/bocken_journal_system/add_entry_form.png)