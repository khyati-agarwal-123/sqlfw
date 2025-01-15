##  Query to Find a User's Oracle SQL Firewall Violations {#GUID-0A9387E6-FD20-4787-AFE2-804669C39EAD} 

The ` DBA_SQL_FIREWALL_VIOLATIONS ` data dictionary view shows the Oracle SQL Firewall violations that a user has committed. 

For example: 
    
    
    ```
    SELECT SQL_TEXT, OCCURRED_AT, FIREWALL_ACTION FROM DBA_SQL_FIREWALL_VIOLATIONS WHERE USERNAME = 'HR';
     
    SQL_TEXT                           OCCURRED_AT                         FIREWALL_ACTION
    ---------------------------------- ----------------------------------  –--------------
    SELECT COUNT(*) FROM HR.EMPLOYEES  12-OCT-23 10.30.02.238383 AM +00:00 BLOCKED
    ```

**Related Topics**

  * [ *Oracle Database Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=REFRN-GUID-855FF31F-7F89-4667-B790-4AD157EA00B5)


