0x19. Postmortem

By Amir Gambo Ibrahim

Issue Summary:

Duration: August 10, 2023, 14:30 — August 11, 2023, 02:15 (UTC)

Impact: Slow response times and intermittent downtime for the User Authentication Service. Users Affected: Approximately 30% of users experienced delays or were unable to log in.

Root Cause:

The root cause of the outage was an unexpected surge in traffic due to a combination of a marketing campaign launch and a sudden increase in new user registrations. This led to an overload of the User Authentication Service and subsequent degradation in performance.

Timeline:

August 10, 14:30 (UTC): Issue detected by an increase in error rates and latency in the User Authentication Service.
August 10, 14:45 (UTC): Monitoring alert triggered, and the on-call engineer-initiated investigation.
August 10, 15:00 (UTC): Initial assumption was an underlying database bottleneck, so database queries and connection pools were examined.
August 10, 16:00 (UTC): Investigation into database revealed no anomalies; focus shifted to network infrastructure.
August 10, 18:30 (UTC): Misleading path taken as firewall rules were adjusted, but no improvement observed.
August 10, 19:30 (UTC): Incident escalated to infrastructure and networking teams for collaboration.
August 10, 20:45 (UTC): Collaborative efforts identified a surge in incoming requests as the likely culprit.
August 11, 00:30 (UTC): Load balancer configurations were adjusted to distribute traffic more efficiently.
August 11, 02:15 (UTC): Service performance fully restored, incident resolved.
Root Cause and Resolution:

Root Cause:

The surge in traffic led to a bottleneck in the User Authentication Service’s load balancer, causing slow responses and timeouts.


Resolution:

Load balancer configurations were optimized to handle the increased load by adding additional instances and adjusting connection limits. This allowed the system to distribute incoming requests more effectively, reducing the strain on individual instances.


Corrective and Preventative Measures:

Improvements/Fixes:

Implement automatic scaling: Set up auto-scaling mechanisms to handle sudden increases in traffic by adding new instances dynamically.
Enhanced monitoring: Implement more granular monitoring of system resources and traffic patterns to detect anomalies earlier.
Traffic shaping: Introduce traffic shaping mechanisms to mitigate sudden traffic spikes and prevent overwhelming the system.
Tasks to Address the Issue:

Update load balancer configurations to include dynamic scaling based on traffic thresholds.
Develop and implement comprehensive monitoring and alerting for load balancer performance and traffic patterns.
Establish communication channels between development, infrastructure, and networking teams for faster incident resolution.
Conduct load testing simulations regularly to assess system capacity and identify potential bottlenecks.
Conclusion:

