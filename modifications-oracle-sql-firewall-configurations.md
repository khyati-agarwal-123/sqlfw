##  Modifications to Oracle SQL Firewall Configurations {#GUID-AB298C9F-556A-4A7D-841C-84EABFE3D55B} 

After you create an Oracle SQL Firewall configuration for a user, you can modify the configuration as necessary. 

To find information about Oracle SQL Firewall configurations, you can query the ` DBA_SQL_FIREWALL_ ` * data dictionary views. 

[ Table 2-1 ](modifications-oracle-sql-firewall-configurations.md#GUID-AB298C9F-556A-4A7D-841C-84EABFE3D55B__TABLE_MLJ_SRD_GVB) lists operations that you can perform after you have configured SQL Firewall. 

**Table: Oracle SQL Firewall Modification Procedures** 

Operation  |  Procedure   
---|---  
Enable SQL Firewall  |  <ul>

<li>
  * To enable SQL Firewall in the database, use ` DBMS_SQL_FIREWALL.ENABLE ` . </li> </ul>  
Manage captures  |  <ul> <li>
    * To create a capture, use ` DBMS_SQL_FIREWALL.CREATE_CAPTURE ` . </li> <li>
    * To start a capture, use ` DBMS_SQL_FIREWALL.START_CAPTURE ` . </li> <li>
    * To modify a capture, delete the current one by using ` DBMS_SQL_FIREWALL.DROP_CAPTURE ` , and then create a new one by using ` DBMS_SQL_FIREWALL.CREATE_CAPTURE ` . </li> <li>
    * To stop the SQL Firewall capture for the specified user, use ` DBMS_SQL_FIREWALL.STOP_CAPTURE ` . </li> <li>
    * To delete the SQL Firewall capture for a specified user and delete all the existing capture logs for this user:  <li>
      1. Use ` DBMS_SQL_FIREWALL.STOP_CAPTURE ` to stop the capture process. </li> <li>
      2. Use ` DBMS_SQL_FIREWALL.DROP_CAPTURE ` to remove the capture. </li> </li> </ul>  
Manage allow-lists  |  <ul> <li>
      * To generate an allow-list for a given user, use ` DBMS_SQL_FIREWALL.GENERATE_ALLOW_LIST ` . </li> <li>
      * To enable an allow-list for a given user, use ` DBMS_SQL_FIREWALL.ENABLE_ALLOW_LIST ` . </li> <li>
      * To update an allow-list enforcement, use ` DBMS_SQL_FIREWALL.UPDATE_ALLOW_LIST_ENFORCEMENT ` . </li> <li>
      * To prevent SQL Firewall from capturing and enforcing allow-lists for database connections and SQL executions in Oracle Scheduler jobs, use ` DBMS_SQL_FIREWALL.EXCLUDE ` . </li> <li>
      * To append all the SQL from a capture log or violation log (or from both) to the allow-list, use the ` DBMS_SQL_FIREWALL.APPEND_ALLOW_LIST ` procedure. You can run this procedure when the allow-list is either enabled or disabled. The change takes place immediately. </li> <li>
      * To append a single SQL record from a capture log or violation log to the allow-list, use the ` DBMS_SQL_FIREWALL.APPEND_ALLOW_LIST_SINGLE_SQL ` procedure as follows:  <li>
        1. Query the ` DBA_SQL_FIREWALL_VIOLATIONS ` or the ` DBA_SQL_FIREWALL_CAPTURE_LOGS ` data dictionary view to find the target SQL record that you want to add to the allow-list. </li> <li>
        2. Enter the obtained ` USERNAME ` , ` SQL_SIGNATURE ` , ` CURRENT_USER ` , and ` TOP_LEVEL ` values of that record in the ` DBMS_SQL_FIREWALL.APPEND_ALLOW_LIST_SINGLE_SQL ` procedure to add the target SQL record to the allow-list. </li> You can run ` DBMS_SQL_FIREWALL.APPEND_ALLOW_LIST_SINGLE_SQL ` when the allow-list is either enabled or disabled. The change takes place immediately.  </li> <li>
      * To export the allow-list of a given user to JSON format into the specified CLOB, use ` DBMS_SQL_FIREWALL.EXPORT_ALLOW_LIST ` . </li> <li>
      * To import the allow-list for a given user into a target database, use ` DBMS_SQL_FIREWALL.IMPORT_ALLOW_LIST ` . </li> <li>
      * To disable an allow-list for a given user, use ` DBMS_SQL_FIREWALL.DISABLE_ALLOW_LIST ` . </li> <li>
      * To add or delete any context values from allowed context lists, use ` DBMS_SQL_FIREWALL.ADD_ALLOWED_CONTEXT ` or ` DBMS_SQL_FIREWALL.DELETE_ALLOWED_CONTEXT ` , respectively. </li> <li>
      * To delete any SQL statement from allowed SQL lists, use ` DBMS_SQL_FIREWALL.DELETE_ALLOWED_SQL ` . </li> <li>
      * To delete the allow-list for a specified user:  <li>
        1. Disable the allow-list by using ` DBMS_SQL_FIREWALL.DISABLE_ALLOW_LIST ` . </li> <li>
        2. Use ` DBMS_SQL_FIREWALL.DROP_ALLOW_LIST ` . </li> </li> </ul>  
Manage allowed contexts  |  <ul> <li>
        * To add a specified value to the allowed contexts of a specified user for the given context type, use ` DBMS_SQL_FIREWALL.ADD_ALLOWED_CONTEXT ` . </li> <li>
        * To modify an allowed context, delete the current one by using ` DBMS_SQL_FIREWALL.DELETE_ALLOWED_CONTEXT ` , and then create a new one by using ` DBMS_SQL_FIREWALL.ADD_ALLOWED_CONTEXT ` . </li> <li>
        * To delete the specified value from the allowed contexts of a specified user for the given context type, use ` DBMS_SQL_FIREWALL.DELETE_ALLOWED_CONTEXT ` . </li> </ul>  
Manage allowed SQL  |  <ul> <li>
          * To delete the specified entry from the allowed SQL of a specified user, use ` DBMS_SQL_FIREWALL.DELETE_ALLOWED_SQL ` . You can run this procedure when the allow-list is either enabled or disabled, and the change takes place immediately. </li> </ul>  
Manage SQL Firewall log tables  |  <ul> <li>
            * To move the SQL Firewall log tables to a different user-defined tablespace other than the default tablespace, ` SYSAUX ` :  <li>
              1. Disable SQL Firewall by using ` DBMS_SQL_FIREWALL.DISABLE ` . </li> <li>
              2. Use the ` MOVE ` clause of the ` ALTER TABLE ` statement to perform the move operation. </li> You can also use the ` DBMS_SQL_FIREWALL.MOVE_LOG_TABLE ` procedure to move the SQL Firewall log tables to another tablespace.  </li> <li>
            * To purge capture logs or violation logs for a user or all users, use ` DBMS_SQL_FIREWALL.PURGE_LOG ` . </li> <li>
            * To flush all the SQL Firewall logs that reside in the memory into the log tables, use ` DBMS_SQL_FIREWALL.FLUSH_LOGS ` . </li> </ul>  
Disable SQL Firewall  |  <ul> <li>
              * To disable SQL Firewall in the database and stop all the existing captures and allow-lists that are enabled, use ` DBMS_SQL_FIREWALL.DISABLE ` . </li> </ul>  
  
**Related Topics**

                * [ *Oracle Database PL/SQL Packages and Types Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=ARPLS-GUID-9DFE7C7F-32A7-4D3A-98C1-E90D8D0475D8)
                * [ Oracle SQL Firewall Data Dictionary Views ](oracle-sql-firewall-data-dictionary-views.md#GUID-A0C5F3D8-3F64-4493-B3A6-223F974C8786)
