##  DBA_SQL_FIREWALL_ALLOWED_IP_ADDR {#GUID-D45DEF6E-8020-4368-AB8A-B611C425AEBB} 

` DBA_SQL_FIREWALL_ALLOWED_IP_ADDR ` lists the IP addresses that SQL Firewall target users are allowed to use to connect to the database. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` IP_ADDRESS ` |  ` VARCHAR2(128) ` |  ` NOT NULL ` |  Allowed client IP address   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
