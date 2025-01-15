##  SQL Firewall Overview {#GUID-C778020E-CEC5-4347-B77F-4350195F1AC5} 

The SQL Firewall feature in Oracle Data Safe lets you administer and monitor SQL Firewall across your fleet of Oracle Database 23ai targets. 

###  About SQL Firewall {#GUID-F53CA853-10B0-4505-B748-4FE58C4D8393} 

The SQL Firewall feature in  Oracle Data Safe  lets you administer and monitor SQL Firewall across your fleet of Oracle Database targets. SQL Firewall is a new security feature built into the Oracle Database 23ai kernel and offers protection against risks such as SQL injection attacks and compromised accounts. SQL Firewall inspects all incoming database connections and SQL statements, including the ones from PL/SQL units, whether local or over the network, encrypted or clear text. It only allows explicitly authorized SQL and can log or block SQL statements and connections that do not fall within the SQL Firewall allowlists. 

SQL Firewall uses allowlists of authorized SQL statements and trusted database connection paths to determine which SQL statements and connection paths are authorized and which ones should be either logged or blocked. SQL Firewall allowlist policies work at a database account level. You create an SQL Firewall allowlist for a database account by capturing or collecting the expected application SQL workload from expected database connections. Subsequently, the firewall detects and prevents unauthorized SQL and potential SQL injection attacks. 

To learn more about SQL Firewall in Oracle Database see the [ *Oracle Database Oracle SQL Firewall User's Guide*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23&id=SQLFW)

SQL Firewall can be managed in multiple ways. The PL/SQL procedures in ` SYS.DBMS_SQL_FIREWALL ` package lets you manage SQL Firewall directly in an Oracle Database (23ai or above). Consider  Oracle Data Safe  if you are looking forward to leveraging the convenience of the Oracle Cloud Infrastructure (OCI) ecosystem and want to manage and monitor SQL Firewall for a fleet of Oracle Database targets. 

Administrators can use Data Safe to collect SQL activities of database accounts, monitor the collection progress, create SQL Firewall policies with allowlist rules (allowed contexts and allowed SQL statements) from the collected SQL activities, and enable SQL Firewall policies. Once a SQL Firewall policy is enabled, Data Safe automatically collects the firewall violation logs from the database and stores them in Data Safe. Those logs are then available for online analysis and reporting across your database fleet as shown in [ Figure 2-2 ](sql-firewall-overview.md#GUID-F53CA853-10B0-4505-B748-4FE58C4D8393__FIG_BMV_BT2_WYB) . You can leverage the Data Safe REST APIs, SDKs, CLI, and Terraform for further automation and integration. You can also leverage the larger OCI ecosystem for integrating SQL Firewall violations with its alerts and notifications. 

Figure 2-2 SQL Firewall dashboard in Data Safe 

  


![Shows the SQL Firewall dashboard in Data Safe. This includes a bar chart of violations over one week, the number of SQL Firewalls in each enforcement mode, and the status of SQL collections](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlfw/img/sql_dashboard.png)###  Terms in SQL Firewall {#GUID-7C3CC797-EE1A-4CA6-882F-567D00745395} 

The following terms are used throughout  Oracle Data Safe  's SQL Firewall feature. 

  * Database security configuration - This resource represents the target database configurations. Included in the Database security configurations are the SQL Firewall configurations such as the status of the firewall, the time that the firewall status was last updated, violation log auto purge settings, and so on. 
  * Session context - This represents client information initiating SQL traffic: client IP address, OS program name, and OS username. 
  * SQL collection - This resource represents the SQL collection for a specific database user in a target database. SQL collection encapsulates the SQL commands issued in the user’s database sessions and their session context. 
  * SQL Firewall policy - An allowlist policy specific to a database user through which incoming SQL statements will be evaluated to determine if they can take action on the target database. SQL statements can be allowed or, if they're not part of the allowlist, allowed and logged or blocked and logged. The policy can consist only of session context information, only of specific SQL statements, or both. 
  * SQL violations - This represents SQL statements that were initiated on the target database that are not included in the allowlist in the SQL Firewall policy. 
  * Context violations - This represents session context from which SQL statements were initiated on the target database that are not included in the allowlist in the SQL Firewall policy. 
  * Observe and log violations - A SQL Firewall policy enforcement option where initiated SQL statements that are either SQL or context violations are allowed to execute on the target database and the statements and context are logged for later reference. 
  * Block and log violations - A SQL Firewall policy enforcement option where initiated SQL statements that are either SQL or context violations are blocked and can't execute on the target database. The statements and context are logged for later reference. 



###  Prerequisites for SQL Firewall {#GUID-3ECFE635-B4A2-485A-8246-43945E1950C9} 

SQL Firewall requires you to register an Oracle Database 23ai target database in Data Safe. Users must be granted specific permissions in IAM. 

These are the prerequisites for using the SQL Firewall feature in Data Safe: 

  * Register an Oracle Database 23ai or later. For more information see, [ Target Registration ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=ADMDS-GUID-B5F255A7-07DD-4731-9FA5-668F7DD51AA6) in the *Administering Oracle Data Safe* guide. 
  * Grant the SQL Firewall role to the Data Safe service account on the target database. For more information, see [ Roles for the Oracle Data Safe Service Account ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=ADMDS-GUID-6E55095B-4963-4568-A7B6-74508B30A25E) in the *Administering Oracle Data Safe* guide. 
  * Obtain the required IAM permissions which can be granted by a tenancy administrator: 

To use the full functionality of SQL Firewall it is recommended to be granted ` manage ` permissions on ` data-safe-sql-firewall-family ` in the relevant compartments. 
    
        ```
    Allow group  to manage data-safe-sql-firewall-family in compartment
            
    ```

Alternatively, administrators may grant more selective permissions by granting permissions to specific resources within ` data-safe-sql-firewall-family ` . For more information on the resources contained within ` data-safe-sql-firewall-family ` , see [ ` data-safe-sql-firewall-family ` Resource ](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/data-safe&id=ADMDS-GUID-13D2E74D-6FED-418C-A1B6-99289CADAD45) . 



