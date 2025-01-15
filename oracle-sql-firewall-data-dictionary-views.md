##  Oracle SQL Firewall Data Dictionary Views {#GUID-A0C5F3D8-3F64-4493-B3A6-223F974C8786} 

Oracle Database provides a set of data dictionary views that provide information about Oracle SQL Firewall configurations. 

[ Table 4-1 ](oracle-sql-firewall-data-dictionary-views.md#GUID-A0C5F3D8-3F64-4493-B3A6-223F974C8786__CACIIEGE) lists these data dictionary views. 

**Table: Data Dictionary Views That Display Oracle SQL Firewall Information** 

View  |  Description   
---|---  
` DBA_SQL_FIREWALL_ALLOW_LISTS ` |  Lists the status and generation date of the user's allow-lists   
` DBA_SQL_FIREWALL_ALLOWED_IP_ADDR ` |  Lists the allowed IP addresses for a user   
` DBA_SQL_FIREWALL_ALLOWED_OS_PROG ` |  Lists the allowed operating system programs for a user   
` DBA_SQL_FIREWALL_ALLOWED_OS_USER ` |  Lists the allowed operating system users for a user   
` DBA_SQL_FIREWALL_ALLOWED_SQL ` |  Lists information about the allowed SQL statements for a user, including the allowed SQL ID and the allow-list version of the allowed SQL   
` DBA_SQL_FIREWALL_CAPTURE_LOGS ` |  Lists log information for a user's SQL Firewall configuration, such as the database user name, SQL text, accessed objects, and the SQL Firewall session ID   
` DBA_SQL_FIREWALL_CAPTURES ` |  Lists the status SQL Firewall captures, such as whether they are enabled   
` DBA_SQL_FIREWALL_SESSION_LOGS ` |  Lists information about the SQL Firewall session, such as the session ID, database user name, and client program   
` DBA_SQL_FIREWALL_SQL_LOGS ` |  Lists information about the SQL logs, such as the SQL text, the command type, the SQL signature, accessed objects, and the character set   
` DBA_SQL_FIREWALL_STATUS ` |  Lists the status of an SQL Firewall configuration, such as whether it is enabled and what its timestamp is   
` DBA_SQL_FIREWALL_VIOLATIONS ` |  Provides a detailed report on SQL Firewall violations, including information such as the objects that were accessed, the user the SQL was run on, and whether the action was blocked or allowed   
  
**Related Topics**

  * [ *Oracle Database Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=REFRN-GUID-8865F65B-EF6D-44A5-B0A1-3179EFF0C36A)


