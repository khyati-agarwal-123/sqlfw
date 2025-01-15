##  Gain Insights from SQL Firewall {#GUID-39F44079-CDB9-476C-954D-E0DFCF8480E3} 

After successfully setting up SQL Firewall to monitor and block and allow SQL activity on your Oracle Database 23ai target databases, you'll want to ensure that you understand the dashboard and violations report. You should also understand what actions to take in the event of a high volume of violations. 

###  View the SQL Firewall Dashboard {#GUID-F3EC5619-A84A-4C03-8069-716C34527E8F} 

When you select  SQL Firewall  under  Security center  in Oracle Data Safe you will see the dashboard of SQL Firewall information for the last week. This dashboard provides you with a high-level view of your SQL Firewall implementation across your fleet of Oracle Database 23ai or above target databases in your selected compartment(s). 

To filter the dashboard you can alter the compartments, time period, and databases that you can see information for by: 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 



The dashboard shows the following information: 

  * SQL Firewall violations  chart - Shows the number of SQL statement violations and the number of context violations throughout your Oracle Database 23ai or above fleet per day. This allows you to determine patterns in the number of SQL statement and session context violations and identify spikes in violations that should be investigated. 
  * SQL Firewall enforcement mode  chart - Shows you a break down of how many of your SQL Firewall policies either "block" or "observe" SQL statements or session contexts that violate your policies. 
  * SQL Collections  chart - Shows you a break down of the number of SQL collections in each life cycle state: ` COLLECTING, COMPLETED, DELETED, FAILED, NEEDS_ATTENTION. `
  * Target Summary  tab - Shows you a break down per registered Oracle Database 23ai or above of the number of database users that SQL statements are actively being collected for, the number of policies that block violations, and the number of polices that allow and observe violations. You can click on the name of a target database to see its SQL Firewall configuration details and drill down deeper into the SQL collections, SQL Firewall policies, and Work Requests on the target database. 
  * Violations Summary  tab - Shows you a break down per registered Oracle Database 23ai or above of the total number of violations, the number of SQL violations, and the number of Context violations. You can click on the name of a target database to see a more detailed violations report. 
  * The  Notifications  tab - Shows you what event notifications and subscriptions you have created for SQL Firewall. More specifically, it displays the event, rule name, topic name, and when the event notification was created. This table will only show Events that you have created directly within Data Safe. In addition to displaying existing event notifications, you can also create new notifications by using the Create notification button. See [ Create and Modify Event Notifications in SQL Firewall ](create-and-modify-event-notifications-sql-firewall.md#GUID-2BF3D79B-3BCA-446D-97E1-D41D5CD4D83B) for more information. 



###  View Violations {#GUID-D9FB17ED-2E54-4B17-8DD4-B27D03341783} 

There are multiple ways that you can view context and SQL statement violations once you have enforced SQL Firewall policies. 

  * View all violations 
  * View target specific violations 
  * View policy specific violations 



Complete these steps to view a report of all violations across your database fleet. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Under  Related resources  , click  Violation reports. 
  3. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  4. Select which report you would like to see from the  Predefined reports  tab: 
     * All violations report - Both SQL and context violations 
     * SQL violations report - Violations on SQL statements 
     * Context violations report - Violations on database connection paths 
  5. Once at the report you may perform all [ standard report actions ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-530B9F4B-5271-4A6A-B1C6-ECC6465896F5) in Oracle Data Safe such as: 
     * Apply basic filters 
     * Apply advanced SCIM filters 
     * Create custom reports 
     * Schedule reports 
     * Generate and download reports 
     * Manage which columns to display 



Complete these steps to view a report of all violations on a specific target database from the last week. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Click the  Violation summary  tab. 
  3. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  4. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  5. Select the name of a target database from the list. 

This will take you to the violation report. 

  6. The violation report will be automatically filtered to show only the violations for the selected target database from the selected time period. 
  7. Once at the report you may perform all [ standard report actions ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-530B9F4B-5271-4A6A-B1C6-ECC6465896F5) in Oracle Data Safe such as: 
     * Apply basic filters 
     * Apply advanced SCIM filters 
     * Create custom reports 
     * Schedule reports 
     * Generate and download reports 
     * Manage which columns to display 



Complete these steps to view a report of violations specific to a selected SQL Firewall policy. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Select the name of a target database from the list on the  Target summary  tab. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL Firewall policies  . 
  6. Select a SQL Firewall policy from the list. 

This will take you to the Firewall policy details page. 

  7. Under  Enforcement information  , click  View report  next to  Violation reports  . 
  8. The violation report will be automatically filtered to show only the violations for the selected database user on the selected target database. 

This will take you to the violation report. 

  9. Once at the report you may perform all [ standard report actions ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-530B9F4B-5271-4A6A-B1C6-ECC6465896F5) in Oracle Data Safe such as: 
     * Apply basic filters 
     * Apply advanced SCIM filters 
     * Create custom reports 
     * Schedule reports 
     * Generate and download reports 
     * Manage which columns to display 



**Related Topics**

  * [ View and Manage Violations Report ](view-and-manage-violations-report.md#GUID-530B9F4B-5271-4A6A-B1C6-ECC6465896F5)



###  Follow-Up Actions for SQL Firewall {#GUID-D7DEFBFE-1B8B-4216-B8C9-E2DF83E01F01} 

In an ideal scenario where the SQL collection has captured all expected SQL statements and trusted database connections, violations indicate potential database attacks such as compromised account access and SQL Injection attacks. But if the collected statements or database connections are not complete or there are new authorized SQL statements following an application update, there is a possibility to see a surge in violations. Ensure to update the SQL Firewall policies to collect these additional statements to avoid false positives in the violation reports. 

**Related Topics**

  * [ Update SQL Firewall Policies ](manage-sql-firewall.md#GUID-EAEF3A85-9E02-4F17-8039-42F2B91ABFD7)


