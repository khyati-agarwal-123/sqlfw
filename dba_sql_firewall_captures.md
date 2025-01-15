##  DBA_SQL_FIREWALL_CAPTURES {#GUID-D0288456-A3AC-4E54-A1C0-3A7933D9D71D} 

` DBA_SQL_FIREWALL_CAPTURES ` displays information about SQL Firewall captures. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` TOP_LEVEL_ONLY ` |  ` VARCHAR2(14) ` |  ` ` |  Indicates whether SQL Firewall should capture only top-level SQL commands, that is, SQL commands issued directly from the user ( ` Y ` ) or all SQL commands, including top-level SQL commands and SQL commands from PL/SQL units ( ` N ` )   
` STATUS ` |  ` VARCHAR2(8) ` |  ` ` |  Capture status ( ` ENABLED ` or ` DISABLED ` )   
` LAST_STARTED_ON ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` ` |  Date and time at which the capture was last started   
` LAST_STOPPED_ON ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` ` |  Date and time at which the capture was last stopped   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
