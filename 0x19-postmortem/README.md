# Postmortem Report: Go-experience System Outage

## Issue Summary:
On April 12, from 6:00 AM to 7:30 AM (GMT+3), a part of the Goexperience system responsible for handling call hangups experienced an outage. The primary cause of this incident was the deployment of untested code into the production server by our engineers. To restore the system's functionality, a rollback to the previous stable version was performed.

## Timeline (GMT+3):

6:00 AM: New code was pushed to the server.
6:10 AM: The system generated the first error report.
6:30 AM: The entire system became unresponsive.
7:00 AM: Services started gradually recovering.
7:30 AM: The system regained full capacity.

## Root Cause:

The incident occurred due to the deployment of untested code changes to the production server. These changes were intended to address a known bug but were not thoroughly tested in the staging environment prior to deployment. Consequently, the module responsible for handling calls began responding with error code 500 (server error).

## Resolution and Recovery:

To restore the system's functionality, an immediate decision was made to revert the production server to the last stable version. Following the rollback, the services gradually recovered, and by 7:30 AM, the system was running at full capacity.

## Corrective and Preventive Measures:

Based on the incident, the following corrective and preventive measures have been identified:

- Test Before Deployment: To mitigate the risk of deploying untested code, it is crucial to establish a robust testing process. All code changes should undergo rigorous testing in a staging environment that closely resembles the production environment. This testing should cover various use cases and edge scenarios to identify potential issues early on.
- Scheduled Maintenance Window: To minimize the impact on users, it is recommended to schedule maintenance activities during a designated maintenance window. In this case, changes should be made between midnight and 2 am (GMT+3), when the client load is generally lower. This ensures that any issues that may arise during the deployment can be resolved with minimal disruption to users.
- Version Control and Rollback Procedures: Maintaining a reliable version control system is essential to facilitate efficient rollback procedures. By leveraging version control, the team can easily identify the last known stable version and roll back to it in the event of an issue. This approach significantly reduces downtime and ensures a faster recovery process.
- Incident Response and Communication: Enhance incident response protocols and establish effective communication channels within the team. Streamline the process of detecting, investigating, and resolving incidents to minimize the Mean Time to Identify (MTTI) and Mean Time to Resolve (MTTR). Additionally, establish clear communication channels to keep stakeholders and clients informed during such incidents, ensuring transparency and managing expectations.

By implementing these measures, we aim to improve the overall stability and reliability of the Goexperience system, reducing the likelihood of similar incidents occurring in the future.
