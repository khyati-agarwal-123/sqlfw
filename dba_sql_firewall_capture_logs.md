##  DBA_SQL_FIREWALL_CAPTURE_LOGS {#GUID-A362742D-18BD-4E18-A954-A1D29F1221EA} 

` DBA_SQL_FIREWALL_CAPTURE_LOGS ` displays SQL Firewall capture logs. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` SESSION_ID ` |  ` NUMBER ` |  ` NOT NULL ` |  SQL Firewall session ID   
` COMMAND_TYPE ` |  ` VARCHAR2(64) ` |  ` ` |  Type of SQL command   
` SQL_SIGNATURE ` |  ` VARCHAR2(64) ` |  ` ` |  SQL signature   
` SQL_TEXT ` |  ` VARCHAR2(4000) ` |  ` ` |  SQL text (up to 1000 characters)  To view the full SQL text, query the ` SQL_TEXT ` column of the ` DBA_SQL_FIREWALL_SQL_LOGS ` view.   
` ACCESSED_OBJECTS ` |  ` VARCHAR2(4000) ` |  ` ` |  List of accessed objects (up to 1000 characters)  To view the full list of accessed objects, query the ` ACCESSED_OBJECTS ` column of the ` DBA_SQL_FIREWALL_SQL_LOGS ` view.   
` CURRENT_USER ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the user who invoked the SQL command   
` TOP_LEVEL ` |  ` VARCHAR2(9) ` |  ` ` |  Indicates whether the SQL command is a top-level SQL command, that is, a SQL command issued directly from the user ( ` Y ` ) or a SQL command from a PL/SQL unit ( ` N ` )   
` CLIENT_PROGRAM ` |  ` VARCHAR2(84) ` |  ` ` |  Name of the client program   
` OS_USER ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the OS user of the client process   
` IP_ADDRESS ` |  ` VARCHAR2(48) ` |  ` ` |  Client IP address   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 

> **note:** See Also: 

" [ DBA_SQL_FIREWALL_SQL_LOGS ](dba_sql_firewall_sql_logs.md) " 
