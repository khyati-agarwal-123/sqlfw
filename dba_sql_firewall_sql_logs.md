##  DBA_SQL_FIREWALL_SQL_LOGS {#GUID-B246C8B2-659B-4A5F-8773-4D5DDC8E5EAA} 

` DBA_SQL_FIREWALL_SQL_LOGS ` displays information about SQL logs for SQL Firewall. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` COMMAND_TYPE ` |  ` VARCHAR2(64) ` |  ` ` |  Type of SQL command   
` SQL_SIGNATURE ` |  ` VARCHAR2(64) ` |  ` ` |  SQL signature   
` SQL_TEXT ` |  ` CLOB ` |  ` ` |  SQL text   
` ACCESSED_OBJECTS ` |  ` CLOB ` |  ` ` |  List of accessed objects   
` CHARSET ` |  ` VARCHAR2(64) ` |  ` ` |  Character set of the SQL text   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
