##  Start Using SQL Firewall {#GUID-76CF0F5C-E858-465B-BD36-83CDD641083B} 

In order to begin using SQL Firewall you need to complete the following steps. Ensure you have already completed the  [ prerequisites ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=ADMDS-GUID-3ECFE635-B4A2-485A-8246-43945E1950C9) before starting these steps. 

These steps will walk you through 

  1. [ Enabling SQL Firewall on your Oracle Database 23ai or above ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-C9613AA1-6D0A-47A6-A7CA-91F255B7A92B)
  2. [ Collecting SQL traffic ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-B32EAC1E-8441-42A2-801C-A7CDA9FBB6AF)
  3. [ Stopping the collection of SQL traffic ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-24082FCA-287E-4CCE-81EB-9280CE39562D)
  4. [ Generating and enforcing SQL Firewall policies ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-EAF114CF-3305-4F31-8151-0CDB5BBE4ABF)
  5. [ Viewing SQL Firewall violation logs ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-7A39F81C-C532-4656-8DF1-F853020C8B8E)
  6. [ Creating audit trails and alert policies for SQL Firewall violations ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-1BB98347-6DAF-4C77-A0FC-DF82E4C076AF)
  7. [ Configuring notifications for SQL Firewall violations ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-B029DA28-EC4C-4866-937D-1E019BCCF3C7)



By completing these steps you will be taking steps to protect your database fleet against SQL injection attacks and compromised accounts. 

###  Step 1: Enable SQL Firewall On Your Target Database {#GUID-C9613AA1-6D0A-47A6-A7CA-91F255B7A92B} 

This steps ensures that SQL Firewall is enabled on your target database. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Click  Enable  . This can be done through either the button under the name of the database security configuration or the  Enable  option under the Target database section of the Database security configuration information tab. 
  6. Wait for the resource to change to Active before continuing to the next step. 



###  Step 2: Start SQL Collection for a Database User {#GUID-B32EAC1E-8441-42A2-801C-A7CDA9FBB6AF} 

This step starts the collection of expected SQL statements and expected database connection paths for the database user. Run the typical application workload from the trusted database connection paths. 

  1. In the Configuration details page from the previous step, click  Create and start SQL collection. 
  2. Select the database user for which collection needs to be created. 
  3. Select the SQL Collection Level: 
     * User issued SQL commands - These are SQL statements that were issued directly from the user to be executed on the database. This is the default. 
     * User issued SQL commands and SQL commands issues from PL/SQL units - This includes SQL statements issued directly from the user as well as SQL statements within a PL/SQL unit which is invoked by the user. 

Note: SQL collection will *not* record any internal recursive SQL statements. 

  4. Click  Create and start SQL collection. 
  5. Perform typical daily tasks in your applications for the selected database user. 
  6. Allow the SQL collection to run for some time. This is discussed further in [ Step 3: Monitor the Progress of SQL Collection with Insights ](start-using-sql-firewall.md#GUID-24082FCA-287E-4CCE-81EB-9280CE39562D) . 



###  Step 3: Monitor the Progress of SQL Collection with Insights {#GUID-24082FCA-287E-4CCE-81EB-9280CE39562D} 

In this step you will monitor the collection of SQL statements and determine when collection can be stopped. Monitor the SQL collection until you see there are no new incoming unique SQL statements or trusted connection paths from the running workload. 

  1. Click the  SQL collection insights  tab. 
  2. The information on the SQL collection tab refreshes every hour, if necessary click  Refresh Insights  . 
  3. (Optional) Select the time period for which you would like to review the SQL collection. 
  4. Review the Unique SQL statements chart. 

The collected SQL statements are analyzed to determine if they are unique over the span of the collection period and this chart displays the number of unique SQL statement on the selected time interval. Once there are no more new unique SQL statement being initiated, i.e. the chart remains steady at zero, it is recommended to stop the collection. Waiting until the number of unique SQL statements comes to zero ensures that you collect all statements that are typically executed on your target database and helps establish a status quo. 

For example, if there are 250 SQL statements executed on the first day of the collection but only 225 of those are unique then the chart will show 225 for that day. In the following week if the same 250 statements and an additional 200 new and unique statements are executed then the chart will only show 200. This is because the 250 statements were already collected and observed in week one, thus they are not unique. The number of unique SQL statements will reach zero when there are no more unique SQL statements are observed. See [ Figure 2-3 ](start-using-sql-firewall.md#GUID-24082FCA-287E-4CCE-81EB-9280CE39562D__FIG_TDT_5P2_WYB) for reference. 

It may take several days to weeks for you to collect enough unique SQL statements to stabilize at zero. 

Figure 2-3 Unique SQL Statements chart in SQL Collection Insights 

  


![Shows a line graph for Unique SQL statements that starts at 225, decreases to 175 over the course of three weeks, drops to 45 in the following week, reaches 0 one week later and stays there for an additional four weeks, jumps to 60 one week later, and then drops back down and remains at zero. When the number of unique SQL statements drops to zero, you may stop collecting. Zero indicates that the firewall is no longer seeing new unique SQL statements, meaning you have collected all unique SQL statements.](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlfw/img/sql_diagram.png)5. Review the Client IP, Client OS user, and Client program charts. 

These charts show you the number of client IP addresses, OS users, and programs, respectively, that are executing SQL commands on your target database each day. The specific context information can be viewed in the table below the charts. 

Since SQL statements should be coming from the same session contexts each day, it is recommended to stop the collection when the charts stabilize at a certain value day to day. 

  6. Review the list of session context types and values. 

Reviewing the list of client IP addresses, client OS users, and client programs allows you to determine where your traffic is coming from. With this information you can set up rules that log or block traffic from all other locations. This is further discussed in [ Step 4: Generate and Enforce SQL Firewall Policies ](start-using-sql-firewall.md#GUID-EAF114CF-3305-4F31-8151-0CDB5BBE4ABF) . 

  7. Once you have collected a sufficient amount of unique SQL statements, click  Stop  to stop the collection. 

Once you have stopped the collection you will see start time, stop time, and the elapsed time under  Collection timeline  of the  SQL collection information  tab. 




###  Step 4: Generate and Enforce SQL Firewall Policies {#GUID-EAF114CF-3305-4F31-8151-0CDB5BBE4ABF} 

In this step you will review the information gathered during the collection and create policies with allowlists based on the collected data. Policies will also be enforced to either observe and allow violations or block violations. 

  1. In the SQL collection details page from the previous step, click  Generate firewall policy.  This will take you to the Firewall policy details page. 
  2. Review the SQL session context and the Unique allowed SQL statements tables. 

If desired you can add, edit, or remove session context information to be included in the policy but you can't add, edit, or remove any of the collected unique SQL statements in the policy. 

  3. (Optional) Update the allowed SQL session context values as desired. 
    1. Click  Update  for the respective row. 
    2. To remove a value, click the  X  at the end of the row in the panel. 
    3. To add a value, click  Add  and enter the new value in the empty field. 
    4. Click  Update client IP/client program/client OS user  , depending on which context information you selected. 
  4. (Optional) Download a PDF or XLS report of all Unique allowed SQL statements. 
    1. Click  Generate report  . 

A pop-up will appear. 

    2. Select which format you want the report in, PDF or XLS. 
    3. Enter a name for the report. 
    4. Optionally, enter a description for the report. 
    5. Click  Generate report  . 
    6. Download the report. You have two options: 
       * In the Generate report window, click the  here  link. The document will begin downloading. 
       * Click  Close  to close the Generate report window. Then, click the  Download report  button. A dialog box is displayed providing you options to open or save the document. 
  5. Click on  Deploy and Enforce  . 
    1. Select the enforcement scope: 
       * All (Session contexts and SQL statements) 
       * Session contexts only - This option enforces the checks only on the database connection paths. 
       * SQL statements only - This option enforces the checks only on the SQL statements. 
    2. Select the action on violations: 
       * Observe (Allow) and log violations - This option will observe and allow all SQL statements and connections to the database while logging any violations. 
       * Block and log violations - This option will block any SQL statements and database connections not listed in the policy and log the violations. Consider this option when you want SQL Firewall to prevent unauthorized SQL traffic to the database. 
    3. Audit for violations 
       * On - This option will write the violation records to the audit trail. It enables alerting and helps demonstrate compliance to your audit requirements. Ensure to start the audit trail in Data Safe to collect the audit events. These audit events contribute to the monthly free limit of 1 million audit records per month per target database. 
       * Off 
    4. Click  Deploy and enforce  . 



###  Step 5: View SQL Firewall Violation Reports {#GUID-7A39F81C-C532-4656-8DF1-F853020C8B8E} 

In this step you can view a report of violations for your enforced SQL Firewall policies. There are a variety of ways to navigate to the violations report, some of which will automatically apply filters for your selected SQL Firewall policies, target databases, time periods, and so on. 

> **note:** It is unlikely that you will see any violations immediately after enforcing a SQL Firewall policy. 

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



###  Step 6 (Optional): Create Audit and Alert Policies for SQL Firewall Violations {#GUID-1BB98347-6DAF-4C77-A0FC-DF82E4C076AF} 

In this step you will create audit and alerts policies for SQL Firewall violations so that you can better track and monitor activity on your database fleet. Though this step is optional, it is recommended as it enables alerting and helps demonstrate compliance to your audit requirements. 

Complete the prerequisites for Activity Auditing and Alerts. 

  1. Complete the [ Activity Auditing workflow ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-4A1BBE55-7779-442F-BD8C-CCE6FFB5DC57) to audit SQL Firewall violations. 

You need to have turned on  Audit for violations  when enforcing your SQL Firewall policies for the corresponding audit policies to show as enabled in Activity auditing. You can view and manage the audit policies for SQL Firewall listed under the SQL Firewall auditing section of the Audit policy details. 

> **note:** Tip: You must turn on  Audit for violations  in your SQL Firewall policy before managing the SQL Firewall audit policies in the Activity Auditing workflow. See [ Update the Enforcement of SQL Firewall Policies ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-3BA8D0C2-41A6-4994-89D2-F8DA3FEAF927) for more information. 

  2. Complete the [ Alerts workflow ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=UDSCS-GUID-E25E50BD-2018-4A22-99D2-A314A5C7799A) to receive alerts for SQL Firewall violations. 

The alert policy for SQL Firewall is  SQL Firewall violations  . 




###  Step 7 (Optional): Configure Notifications for SQL Firewall Violations {#GUID-B029DA28-EC4C-4866-937D-1E019BCCF3C7} 

In this step you will configure notifications for when a SQL Firewall violation occurs. Though this step is optional, it is recommended as it will enable you to receive near real-time alerts in the event of a SQL Firewall violation. 

In Data Safe you can create event notifications through a workflow available in SQL Firewall. This allows you to create event notifications in context. You can use the quickstart template for common events or the advanced event notification workflows to create notifications. 

Prerequisites: 

Ensure you have the necessary IAM permissions to create event notifications. For more information, see [ Permissions to Use Contextual Event Notifications ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=ADMDS-GUID-44143439-1BF8-4A36-B05F-4BEAF1741C7C) in the *Administering Oracle Data Safe* guide. 

To create notifications: 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Click the  Notifications  tab. 
  3. Click  Create notification  . 

If you don't have any notifications created for the selected resource then you will see a list of available quickstart templates. You may click on one of these instead. 

The  Create notification  side panel will appear. 

  4. Select to create an event notification from either a  Quickstart  template or an  Advanced event notification  . 

A Quickstart templates allow you to select from a list of common event scenarios. When you create a notification from a quickstart template, the Rule and Event is created automatically. 

> **note:** The Rule and Event are created in the compartment that you were working in when you started the Notification workflow. Rules and Events will only trigger for the compartment and any child-compartments of the compartment that they were created in. 

  5. If you selected  Quickstart  in the previous step, make a quickstart  Template selection  . 

If you selected  Advanced event notification  in the previous step, type in a  Rule name  and select an  Event type  . 

See [ SQL Firewall Event Types ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=ADMDS-GUID-68BCE918-8E05-41E1-BEAD-3AC899123C89) in the *Administering Oracle Data Safe* guide for more information on events. 

  6. Select to either  Create new topic  or to  Select existing topic  . 
  7. Select a  Compartment  . 

> **note:** This compartment is where the topic will be created, not where the rule and event will be monitored in. 

  8. If you're creating a new topic, type the topic name or, if you're using an existing topic, select the topic name. 
  9. Select a  Subscription protocol  . 
  10. Provide the necessary inputs for the selected subscription protocol. 
  11. Optionally, click  Show Advanced Options  to tag the notification. 
    1. Click  \+ Another Tag  to create an additional optional tag to organize and track resources in your tenancy. 
    2. Select a  Tag Namespace  from the drop-down list. 
    3. Provide a  Tag Key  and  Tag Value  . 
  12. Click  Create notification  . 



Following the completion of these steps, SQL Firewall will start observing the incoming SQL statements and database connection paths, and will allow or block the SQL traffic to proceed to the target database based on the enforced SQL Firewall policy while logging any violations. You can monitor the SQL Firewall violations in Data Safe. If you configured audit and alert configuration, OCI notifications will be triggered in the event of a SQL Firewall violation. 
