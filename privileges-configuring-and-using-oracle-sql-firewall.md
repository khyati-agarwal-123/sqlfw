##  Privileges for Configuring and Using Oracle SQL Firewall {#GUID-47339B36-F95A-4371-AC87-F8EF2C799455} 

You must be granted the appropriate role to administer Oracle SQL Firewall or to query the views that are associated with Oracle SQL Firewall. 

To administer Oracle SQL Firewall, you must be granted the ` SQL_FIREWALL_ADMIN ` role. This role provides the following privileges: 

  * The ` ADMINISTER SQL FIREWALL ` system privilege, which is required to run the PL/SQL procedures in the ` DBMS_SQL_FIREWALL ` package 
  * The ` EXECUTE ` privilege for the ` DBMS_SQL_FIREWALL ` PL/SQL package 
  * The ` READ ` privilege for the SQL Firewall ` DBA_SQL_FIREWALL_ ` * data dictionary views 



To be able to query the ` DBA_SQL_FIREWALL_ ` * data dictionary views (but not administer SQL Firewall), users must be granted the ` SQL_FIREWALL_VIEWER ` role. 

> **note:** The SQL Firewall ` SQL_FIREWALL_ADMIN ` and ` SQL_FIREWALL_VIEWER ` roles are powerful roles. Only grant these roles to trusted users. 

**Related Topics**

  * [ Oracle SQL Firewall Data Dictionary Views ](oracle-sql-firewall-data-dictionary-views.md#GUID-A0C5F3D8-3F64-4493-B3A6-223F974C8786)


