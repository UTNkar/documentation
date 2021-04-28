+++
date = 2021-04-23T13:59:12+02:00
title = "Reports"
toc = true
weight = 10

+++

Reports are a collection of journal entries between two different timestamps. 
Reports calculate how much each group has driven and how much they should pay. 
It also calculates the lost cost i.e. the cost for the kilometers that have not been entered into the journal, e.g. someone forgot to create a journal entry after they had driven.

![report](/images/bocken_journal_system/report.png)

### Creating a report

When creating a report, the two timestamps are chosen automatically. 
The start timestamp is the end time of the latest report. If no other report exists, it is set to the creation time of the first journal entry. 
The end timestamp is always set to the current time.

The timestamps are chosen automatically in order to prevent gaps from occuring, i.e. some journal entries being left out of a report.

When creating a report you can also set the cost per mil for each report. 
This is to prevent old reports from showing the wrong costs if the cost per mil is changed.

![Create report](/images/bocken_journal_system/create_report.png)

### Deleting a report

In order to prevent gaps from occuring if a report was to be deleted, administrators can only remove the latest report.

![Delete latest report](/images/bocken_journal_system/delete_latest.png)