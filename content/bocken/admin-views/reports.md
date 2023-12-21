---
title: "Reports"
toc: true
weight: 10
---

Reports summarize journal entries within a specific time frame, detailing the distance driven by each group and the corresponding payment due. They also include the lost cost, which accounts for any kilometers driven but not recorded in the journal, for example, if a journal entry was forgotten.

A report comprises only its start and end timestamps and does not keep a duplicate of the journal entries. Therefore, if any journal entries included in a report are modified, the report will reflect these changes automatically.

![View report](/images/bocken/report.png)

### How to Create a Report

To create a report:

1. The system automatically sets the start and end timestamps to avoid missing entries. The start timestamp follows the end of the last report, or if there's no prior report, the time of the first journal entry. The end timestamp is the current time.
2. You can set the cost per kilometer for each report to ensure accuracy, even if rates change over time.

The automatic timestamp selection prevents gaps, ensuring no entries are omitted from a report.

![Creating a report](/images/bocken/create-report.png)

### Deleting a Report

To preserve the continuity of reports and prevent gaps, only the most recent report can be deleted by administrators.

![Delete the latest report](/images/bocken/delete-latest.png)
