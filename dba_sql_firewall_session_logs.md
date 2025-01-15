##  DBA_SQL_FIREWALL_SESSION_LOGS {#GUID-A45D4599-8761-47E1-83B1-F0782FA5A430} 

` DBA_SQL_FIREWALL_SESSION_LOGS ` displays SQL Firewall session logs. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` SESSION_ID ` |  ` NUMBER ` |  ` NOT NULL ` |  SQL Firewall session ID   
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` LOGIN_TIME ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` ` |  Date and time at which the target user logged in to the database   
` IP_ADDRESS ` |  ` VARCHAR2(48) ` |  ` ` |  Client IP address   
` CLIENT_PROGRAM ` |  ` VARCHAR2(84) ` |  ` ` |  Name of the client program   
` OS_USER ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the OS user of the client process   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
