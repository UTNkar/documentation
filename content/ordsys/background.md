+++
date = 2021-04-23T13:59:12+02:00
title = "Background"
weight = 10

+++

OrdSys was created in spring 2020 by Albin Antti ([LinkedIn](https://www.linkedin.com/in/albinantti) | [GitHub](https://www.github.com/albinantti)) and Christoffer Wallén ([GitHub](https://github.com/chwallen)) with the help of Benjamin Angeria, Aliyawer Qambari, Daniel Fehrm and the UTN digitalisation committee.

### Purpose

The purpose of OrdSys was to digitalize the way kitchen- and bar staff communicated, allowing to distance the bar from the kitchen (since no post-it notes had to be handed to anyone) and generally improving the workflow.

### Development history

The idea for a digital order management system came during June 2019 as the pub crew was starting to plan for 2019's Battle of the Sections and realized that the existing order management solution (writing the order on a post-it note and handing it to someone in the kitchen) didn't allow for customers to order food from the outdoors bar. This was problematic not only from a legal standpoint, but also simply inconvenient.

During the summer of 2019, a rudimentary version of OrdSys was developed by Albin Antti using Node with Express and Sockets, which was used during the Battle of the Sections to great reception.

The original version was more of a proof of concept, however, and lacked many crucial features such as authentication, scalability and database management. It wasn't until OrdSys was chosen as the subject of a bachelor project in spring 2020 the existing version of OrdSys started taking shape.

At this point, Christoffer, Benjamin and Aliyawer joined the project under the supervision of the current UTN SysAdmin, Daniel. The system was completely rebuilt in Django & PostgreSQL for the backend and Node & React for the frontend.

Towards the end of the bachelor project, the Covid-19 pandemic started imposing restrictions on most UTN events which greatly affected the use-case of OrdSys and required a lot of new features to be added. To allow OrdSys to be used during the TD reception 2020, Albin and Christoffer kept developing the system during the summer of 2020 resulting in the OrdSys that is in use today.
