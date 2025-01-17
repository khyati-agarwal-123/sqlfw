##  Query to Find a User's Allowed SQL and Accessed Objects {#GUID-047332CE-6F79-44F0-BF7D-9C2E78F73525} 

The ` DBA_SQL_FIREWALL_ALLOWED_SQL ` data dictionary view shows the SQL that a user is allowed to use. 

For example: 
    
    
```
SELECT SQL_TEXT, ACCESSED_OBJECTS FROM DBA_SQL_FIREWALL_ALLOWED_SQL WHERE USERNAME = 'HR';
 
SQL_TEXT                            ACCESSED_OBJECTS  
----------------------------------- ------------------
SELECT COUNT(*) FROM HR.EMPLOYEES   "HR"."EMPLOYEES'        
```

**Related Topics**

  * [ *Oracle Database Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=REFRN-GUID-8C10138B-15B6-49F9-B6EF-5E6D11CA0868)


