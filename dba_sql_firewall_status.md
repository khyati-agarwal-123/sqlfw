##  DBA_SQL_FIREWALL_STATUS {#GUID-B43F5774-EF75-4C12-9C75-090DE5DA9FC2} 

` DBA_SQL_FIREWALL_STATUS ` displays the status of SQL Firewall. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` STATUS ` |  ` VARCHAR2(8) ` |  ` ` |  SQL Firewall status ( ` ENABLED ` or ` DISABLED ` )   
` STATUS_UPDATED_ON ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` NOT NULL ` |  Date and time of the most recent SQL Firewall status change   
` EXCLUDE_JOBS ` |  ` VARCHAR2(12) ` |  ` ` |  Indicates whether the SQL Firewall will capture or enforce allow-lists for database connections and SQL executions of Oracle scheduler job sessions ( ` Y ` ) or not ( ` N ` )   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
