##  Manage SQL Firewall {#GUID-5B4BF7F3-DCFF-4A33-A517-9654552608D3} 

Managing your SQL Firewall policies and configurations helps ensure that your databases are protected from threats while also ensuring that intended SQL actions can be taken on your databases. See the below topics for information on how to update your SQL Firewall configurations and policies. 

###  Update the Database Security Configuration {#GUID-AE0EC467-91B7-4679-A95A-32A6FDA2D18B} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Perform any of the following tasks: 
     * Click  Disable  next to  SQL Firewall status  to disable SQL Firewall. This will stop any ongoing collections and policies will no longer be enforced. 
     * Click  Turn on  or  Turn off  next to  Auto-purge violation logs  to turn this on or off. This specifies whether Data Safe should automatically purge the violation logs from the database after collecting the violation logs and persisting them on Data Safe. 

> **note:** When this is turned on violation logs are automatically purged every seven days. 

     * Click  Include  or  Exclude  next to  Database jobs  to include or exclude database jobs for SQL Firewall enforcement. 
     * Click  Refresh  next to  Last refresh time  to refresh Data Safe's copy of the policies if you made a recent policy change within the database. 
     * Click  Move Resource  to move the Database Security Configuration to a different compartment. 



###  Purge a SQL Collection {#GUID-78C612E0-0397-4B03-9C53-D09F11409B9C} 

Purge helps clean the collection logs for the user. You typically need to purge the SQL Collection when you need to recapture an application SQL workload for the same database user following application updates. The SQL collection can be started again for the database user once it is purged. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL collections  . 
  6. Click on a database user name. 

This will take you to the SQL collection details page. 

  7. Click  Purge  to remove the SQL collection. This will not stop any SQL Firewall Policies that were generated from this collection. 



###  Drop a SQL Collection {#GUID-AEF0F083-8DB5-445A-95B5-D67C530EFCC3} 

Drop will remove the SQL Collection and collection logs for the selected database user. You typically have to drop the SQL Collection when you need to remove SQL Firewall protection for a database user who is no longer active or has changed responsibilities in the system. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL Collections  . 
  6. Click on a database user name. 

This will take you to the SQL collection details page. 

  7. Click on  More actions  and select  Drop  to delete the SQL collection. Dropping a SQL collection will not have an impact on already generated or enforced SQL Firewall policies. 



###  View and Manage SQL Firewall Policies {#GUID-8197BFFC-045A-464E-92A5-A5BD160A75CB} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL Firewall policies  . 
  6. Click on a database user name. 

This will take you to the Firewall policy details page. 

  7. (Optional) Update the allowed SQL session context values as desired. 
    1. Click  Update  for the respective row. 
    2. To remove a value, click the  X  at the end of the row in the panel. 
    3. To add a value, click  Add  and enter the new value in the empty field. 
    4. Click  Update client IP/client program/client OS user  , depending on which context information you selected. 
  8. (Optional) Download a PDF or XLS report of all Unique allowed SQL statements. 
    1. Click  Generate report  . 

A pop-up will appear. 

    2. Select which format you want the report in, PDF or XLS. 
    3. Enter a name for the report. 
    4. Optionally, enter a description for the report. 
    5. Click  Generate report  . 
    6. Download the report. You have two options: 
       * In the Generate report window, click the  here  link. The document will begin downloading. 
       * Click  Close  to close the Generate report window. Then, click the  Download report  button. A dialog box is displayed providing you options to open or save the document. 



###  Update SQL Firewall Policies {#GUID-EAEF3A85-9E02-4F17-8039-42F2B91ABFD7} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL collection  . 
  6. Click on a database user name. 

This will take you to the SQL collections details page. 

  7. Click on the associated SQL Firewall policy located in the SQL collection information tab. 

This will take you to the Firewall details page. 

  8. Temporarily disable the SQL Firewall policy by clicking  Disable  . Confirm disablement in the pop-up by clicking  Disable  . 
  9. Navigate back to the SQL collection by clicking  SQL collection details  in the page breadcrumbs. 
  10. Click  Start  to capture SQL statements. 
  11. Initiate the SQL statements you want to add on your target database. 
  12. Click  Stop  once you have collected the SQL statements. 
  13. Click  Update firewall policy  to append the new SQL statements to the associated policy. 
  14. Click on the associated SQL Firewall policy located in the SQL collection information tab. 

This will take you to the Firewall details page. 

  15. Click on  Deploy and Enforce  . 
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



###  Update the Enforcement of SQL Firewall Policies {#GUID-3BA8D0C2-41A6-4994-89D2-F8DA3FEAF927} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL Firewall policies. 
  6. Select a SQL Firewall policy from the list. 

This will take you to the Firewall policy details page. 

  7. Click on  Deploy and Enforce  . 
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



###  Disable or Enable SQL Firewall Policies {#GUID-68C0E38E-C315-41A4-B2F5-C2E39018EE9E} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources,  click  SQL Firewall policies. 
  6. Select a SQL Firewall policy from the list. 

This will take you to the Firewall policy details page. 

  7. Click  Disable  or  Enable  . Disabling will stop the SQL Firewall from evaluating any incoming SQL traffic against this SQL Firewall policy. However, this will not delete the policy and it can be enabled again later. 



###  Drop SQL Firewall Policies {#GUID-7AA232AB-B597-484C-98B0-09B85DFE946F} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. (Optional) Under  List scope  , select the compartment that contains your target database. Optionally select  Include child compartments  to include target database in the list from child compartments. 
  3. (Optional) Filter the list of results, under  Filters  , do the following: 
    1. (Optional) Select a time period from the  Time period  menu. 
    2. (Optional) Select a target database from the  Target database  menu. 
  4. Click on the name of a target database. 

This will take you to the Configuration details page. 

  5. Under  Resources  , click  SQL Firewall policies  . 
  6. Select a SQL Firewall policy from the list. 

This will take you to the Firewall policy details page. 

  7. Click  Drop  . This will delete the SQL Firewall policy and a SQL Collection will have to be initiated again to re-create this policy. 


