##  DBA_SQL_FIREWALL_ALLOW_LISTS {#GUID-FE780B16-A46E-4BEA-9AC9-1B5B8875B202} 

` DBA_SQL_FIREWALL_ALLOW_LISTS ` displays information about SQL Firewall allow-lists. 

Column  |  Datatype  |  NULL  |  Description   
---|---|---|---  
` USERNAME ` |  ` VARCHAR2(128) ` |  ` ` |  Name of the target user   
` GENERATED_ON ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` NOT NULL ` |  Date and time of allow-list generation   
` STATUS ` |  ` VARCHAR2(8) ` |  ` ` |  Allow-list status ( ` ENABLED ` or ` DISABLED ` )   
` STATUS_UPDATED_ON ` |  ` TIMESTAMP(6) WITH TIME ZONE ` |  ` NOT NULL ` |  Date and time of the most recent allow-list status change   
` TOP_LEVEL_ONLY ` |  ` VARCHAR2(14) ` |  ` ` |  Indicates whether the allow-list should be enforced on only top-level SQL commands, that is, SQL commands issued directly from the user ( ` Y ` ) or on all SQL commands, including top-level SQL commands and SQL commands from PL/SQL units ( ` N ` )   
` ENFORCE ` |  ` VARCHAR2(15) ` |  ` ` |  Option of the allow-list enforcement:  <ul>

<li>
  * ` ENFORCE_CONTEXT ` \- Allowed contexts will be checked and enforced during database connection  </li> <li>
  * ` ENFORCE_SQL ` \- Allowed SQLs will be checked and enforced for every SQL statement execution  </li> <li>
  * ` ENFORCE_ALL ` \- Both allowed contexts and allowed SQLs will be checked and enforced  </li> </ul>  
` BLOCK ` |  ` VARCHAR2(14) ` |  ` ` |  If the allow-list is enabled, indicates whether the allow-list is enabled in blocking mode ( ` Y ` ) or non-blocking mode ( ` N ` )   
  
> **note:** 

This view is available starting with Oracle Database 23ai. 
