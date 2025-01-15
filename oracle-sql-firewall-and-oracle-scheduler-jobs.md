##  Oracle SQL Firewall and Oracle Scheduler Jobs {#GUID-8E218675-DE40-4517-B980-96EC0E166480} 

In most scenarios, you may want to exclude Oracle Scheduler jobs from Oracle SQL Firewall enforcement because these are not typically run by users. 

By default the Oracle Scheduler jobs are excluded. You can enable or disable the enforcement of SQL Firewall during Oracle Scheduler operations by setting the ` FEATURE ` parameter to the ` DBMS_SQL_FIREWALL.SCHEDULER_JOB ` constant, using the following procedures: 

  * ` DBMS_SQL_FIREWALL.INCLUDE ` permits SQL Firewall to capture any SQL or enforce any allow-lists during Oracle Scheduler operations. 
  * ` DBMS_SQL_FIREWALL.EXCLUDE ` prevents SQL Firewall from capturing any SQL or enforcing any allow-lists during Oracle Scheduler operations. 



For example: 
    
    
    ```
    EXEC DBMS_SQL_FIREWALL.EXCLUDE (DBMS_SQL_FIREWALL.SCHEDULER_JOB);
    ```

**Related Topics**

  * [ *Oracle Database PL/SQL Packages and Types Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=ARPLS-GUID-9DFE7C7F-32A7-4D3A-98C1-E90D8D0475D8)
  * [ Oracle SQL Firewall Data Dictionary Views ](oracle-sql-firewall-data-dictionary-views.md#GUID-A0C5F3D8-3F64-4493-B3A6-223F974C8786)


