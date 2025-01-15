##  DBA_SQL_FIREWALL_ALLOWED_OS_PROG {#GUID-557A04BB-6D1F-4042-9265-4DDAF607875B} 

` DBA_SQL_FIREWALL_ALLOWED_OS_PROG ` lists the OS programs that SQL Firewall target users are allowed to use to connect to the database. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` OS_PROGRAM ` |  ` VARCHAR2(128) ` |  ` NOT NULL ` |  Allowed OS program name   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
