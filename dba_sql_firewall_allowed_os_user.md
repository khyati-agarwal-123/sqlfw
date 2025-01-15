##  DBA_SQL_FIREWALL_ALLOWED_OS_USER {#GUID-719CEA2C-7317-4B14-BD9E-C43DB5B91E0A} 

` DBA_SQL_FIREWALL_ALLOWED_OS_USER ` lists the OS user names that SQL Firewall target users are allowed to use to connect to the database. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` OS_USER ` |  ` VARCHAR2(128) ` |  ` NOT NULL ` |  Allowed OS user name   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
