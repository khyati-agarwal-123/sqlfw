##  DBA_SQL_FIREWALL_ALLOWED_SQL {#GUID-8C10138B-15B6-49F9-B6EF-5E6D11CA0868} 

` DBA_SQL_FIREWALL_ALLOWED_SQL ` displays information about allowed SQL for SQL Firewall allow-lists. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` ALLOWED_SQL_ID ` |  ` NUMBER ` |  ` NOT NULL ` |  Unique ID of allowed SQL entry for the target user   
` SQL_SIGNATURE ` |  ` VARCHAR2(64) ` |  ` NOT NULL ` |  Allowed SQL signature   
` SQL_TEXT ` |  ` VARCHAR2(4000) ` |  ` ` |  SQL text (up to 1000 characters)  To view the full SQL text, query the ` SQL_TEXT ` column of the ` DBA_SQL_FIREWALL_SQL_LOGS ` view.   
` ACCESSED_OBJECTS ` |  ` VARCHAR2(4000) ` |  ` ` |  List of accessed objects (up to 1000 characters)  To view the full list of accessed objects, query the ` ACCESSED_OBJECTS ` column of the ` DBA_SQL_FIREWALL_SQL_LOGS ` view.   
` CURRENT_USER ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the user who invoked the SQL command   
` TOP_LEVEL ` |  ` VARCHAR2(9) ` |  ` ` |  Indicates whether the allowed SQL entry is a top-level SQL command, that is, a SQL command issued directly from the user ( ` Y ` ) or a SQL command from a PL/SQL unit ( ` N ` )   
` VERSION ` |  ` NUMBER ` |  ` NOT NULL ` |  Version number for the allow-list when the allowed SQL was added  You can use this value to determine whether specific allowed SQLs were added to the allow-list in the same batch.   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 

> **note:** See Also: 

" [ DBA_SQL_FIREWALL_SQL_LOGS ](dba_sql_firewall_sql_logs.md) " 
