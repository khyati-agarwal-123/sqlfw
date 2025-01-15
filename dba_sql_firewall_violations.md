##  DBA_SQL_FIREWALL_VIOLATIONS {#GUID-855FF31F-7F89-4667-B790-4AD157EA00B5} 

` DBA_SQL_FIREWALL_VIOLATIONS ` lists SQL Firewall violations. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` COMMAND_TYPE ` |  ` VARCHAR2(64) ` |  ` ` |  Type of SQL command   
` SQL_SIGNATURE ` |  ` VARCHAR2(64) ` |  ` ` |  SQL signature   
` SQL_TEXT ` |  ` VARCHAR2(4000) ` |  ` ` |  SQL text (up to 1000 characters)  To view the full SQL text, query the ` SQL_TEXT ` column of the ` DBA_SQL_FIREWALL_SQL_LOGS ` view.   
` ACCESSED_OBJECTS ` |  ` VARCHAR2(4000) ` |  ` ` |  List of accessed objects (up to 1000 characters)  To view the full list of accessed objects, query the ` ACCESSED_OBJECTS ` column of the ` DBA_SQL_FIREWALL_SQL_LOGS ` view.   
` CURRENT_USER ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the user who invoked the SQL command   
` TOP_LEVEL ` |  ` VARCHAR2(9) ` |  ` ` |  Indicates whether the SQL command is a top-level SQL command, that is, a SQL command issued directly from the user ( ` Y ` ) or a SQL command from a PL/SQL unit ( ` N ` )   
` IP_ADDRESS ` |  ` VARCHAR2(48) ` |  ` ` |  Client IP address   
` CLIENT_PROGRAM ` |  ` VARCHAR2(84) ` |  ` ` |  Name of the client program   
` OS_USER ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the OS user of the client process   
` CAUSE ` |  ` VARCHAR2(17) ` |  ` ` |  Cause of the violation:  <ul>

<li>
  * ` Context ` ` violation ` </li> <li>
  * ` SQL ` ` violation ` </li> </ul>  
` FIREWALL_ACTION ` |  ` VARCHAR2(7) ` |  ` ` |  Indicates whether the SQL Firewall action was ` Allowed ` or ` Blocked `  
` OCCURRED_AT ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` ` |  Date and time of the violation   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 

> **note:** See Also: 

" [ DBA_SQL_FIREWALL_SQL_LOGS ](dba_sql_firewall_sql_logs.md) " 
