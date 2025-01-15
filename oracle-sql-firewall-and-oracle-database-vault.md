##  Oracle SQL Firewall and Oracle Database Vault {#GUID-AF15C633-12DC-465F-8A7B-D45F9CAEDCFD} 

Oracle Database Vault requires special authorization before you can use Oracle SQL Firewall in a Database Vault environment. 

###  Using SQL Firewall in an Oracle Database Vault Environment {#GUID-04EDF2F3-16D1-4EFB-A13D-A2416BC80939} 

Depending on the type of protection that you want to configure, you can use either or both Oracle Database Vault and SQL Firewall. 

Database Vault enables you to use realms and command rules to block access to sensitive objects, the execution of critical commands, and SQL connections from untrusted factors such as the time of the day, IP address, host name, program name, or any number of identifiable attributes that are associated with the user. In a Database Vault environment, you can extend this protection by using SQL Firewall to capture an allow-list of SQL commands with an associated trusted database connection paths for a database account. Then you can log (and optionally block) the unseen SQL traffic. SQL Firewall enforcement can distinguish approved SQL statements and connections from the unauthorized SQL traffic, which adds to the protection layer that realms and command rules provide to prevent access to sensitive objects unless they have been explicitly authorized. 

The following table shows a comparison of how you can enforce protections using Database Vault realms and command rules, and SQL Firewall. 

**Table: Comparison of Oracle Database Vault and SQL Firewall Protections** 

Use Case  |  Realms  |  Command Rules  |  SQL Firewall   
---|---|---|---  
Protect database schemas  |  Yes, traditional or mandatory realms can limit access to your data.  <ul>

<li>
  * Entire schema or schemas </li> <li>
  * Object types </li> <li>
  * Specific objects by name </li> </ul> |  Yes, DML or DDL statements against schema objects  |  No   
Protect database roles  |  Yes, traditional or mandatory realms can protect your roles.  |  Yes, create a command rule with ` GRANT ` or ` REVOKE ` statements for specific roles.  |  No   
Protect database objects  |  Yes, traditional or mandatory realms can limit access to your data.  <ul> <li>
    * Entire shema or schemas </li> <li>
    * Object types </li> <li>
    * Specific objects by name </li> </ul> |  Yes, DML or DDL statements against schema objects  <ul> <li>
      * Entire schema or schemas </li> <li>
      * Object types </li> <li>
      * Specific objects by name </li> </ul> |  No   
Protect individual SQL statements  |  No  |  Yes, control statements against schema or individual schema objects.  |  Yes, block all but explicitly allowed SQL statements.   
Allow-list and protect application SQL traffic  |  No  |  No  |  Yes, block all but explicitly allowed SQL statements.   
Protect against risks of compromised accounts  |  Yes, establish trusted path conditions based on any factors that can be checked programmatically.  |  Yes, protect ` CONNECT ` command usage.  |  Yes, block sessions from untrusted client IP, program and OS user name   
Protect database users against SQL Injection risks  |  No  |  No  |  Yes, create an allow-list SQL Firewall policy for each database user and enforce it.   
  
###  Authorization for Using SQL Firewall in an Oracle Database Vault Environment {#GUID-8E826561-CA02-415D-88E6-7D98A9D56AE2} 

In an Oracle Database Vault environment, users who want to configure SQL Firewall must have Oracle Database Vault-specific authorization. 

When Database Vault is enabled, the management of SQL Firewall (that is, the invocation of the ` DBMS_SQL_FIREWALL ` package) requires SQL Firewall administrators to have Database Vault-specific authorization in addition to the ` ADMINISTER SQL FIREWALL ` system privilege. This requirement is to ensure that only trusted users will be able to manage SQL Firewall in a Database Vault environment. 

You can authorize SQL Firewall administrators to allow or not allow captures on users who have the ` DV_OWNER ` , ` DV_ADMIN ` , or ` DV_ACCTMGR ` roles in a Database Vault environment. When Database Vault operations control is enabled, common users will be blocked from using SQL Firewall (that is, the ` DBMS_SQL_FIREWALL ` procedures for managing captures and allow-lists) on local users unless the common users are included in the exception list. 

**Related Topics**

        * [ *Oracle Database Vault Administrator’s Guide*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=DVADM-GUID-283F7DEA-8580-4858-8027-2B1EF082FF44)
