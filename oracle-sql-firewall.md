##  About Oracle SQL Firewall {#GUID-B268CC0A-4FE5-4A50-9C20-FABC99B5C4AD} 

Oracle SQL Firewall provides real-time protection against common database attacks by restricting database access to only authorized SQL statements or connections for a designated user. 

It mitigates risks from SQL injection attacks, anomalous access, and credential theft or abuse, preventing or detecting potential SQL injection attacks. 

You can use SQL Firewall to control which SQL statements are allowed to be processed by the database. In addition, SQL Firewall can use session context data such as IP address to restrict database connections. Unauthorized SQL and database connection can be logged and blocked. 

SQL Firewall helps to address the following three  use cases  : 

  * Provide real-time protection by restricting database access to only authorized SQL statements and database connections. 
  * Mitigate SQL injection attacks, anomalous access, and credential theft/abuse risks. 
  * Enforce trusted database connection paths. 



SQL Firewall offers the following  benefits  : 

  * SQL Firewall inspects all incoming database connections and SQL statements, including those from PL/SQL, whether local or over the network, encrypted or clear text. It cannot be bypassed. It only allows explicitly authorized SQL. For all other SQL, it logs the offending statements and raises violations. This statement could have been a SQL injection attack or a new SQL statement that the authorized user has not run before. 
  * You can decide whether you want to block unauthorized SQL or only log it. This gives you the flexibility on how to handle attacks. 
  * SQL Firewall evaluates the complete SQL and the processing context. By running inside the Oracle database server, the firewall easily handles encoding of the SQL statement, synonyms, dynamically generated object names, and any SQL statements that are dynamically generated in PL/SQL units. 
  * SQL Firewall relies on the allow-listing (an allow-list is a set of permitted actions) of the authorized SQL statements and associated trusted database connection paths while blocking the rest. You train the SQL Firewall by simply capturing authorized SQL statements for a database account. Subsequently, the firewall detects and prevents unauthorized SQL and potential SQL injection attacks. A typical use case with allow-listed SQL statements is for application SQL workloads issued by application service account. 
  * SQL Firewall can also block connections that do not come from trusted IP addresses, operating system user names, or program names. This function is useful when you want to put some protection in place immediately, while you create the allow-list of SQL statements for your applications. This feature ensures that any direct access to your databases is coming exclusively from trusted endpoints. This also helps mitigate the risk of stolen or misused application service account credentials. 



SQL Firewall enables you to build an allow-list policy for each database user of SQL statements that a typical database user performs, and then detects, blocks, and logs any unexpected SQL. 

SQL Firewall policies work at a database account level, whether of an application service account or a direct database user, such as a reporting user or a database administrator. In other words, you might have one SQL Firewall policy for the database user ` HR ` and another for the database user ` pfitch ` . This flexibility allows you to gradually build up the protection level of the database, starting from either the database administrators or the application service accounts. 

You can use SQL Firewall in both the root and a pluggable database (PDB). SQL Firewall is a simple and easy-to-use firewall solution for all Oracle Database deployments, such as on-premises, cloud, multitenant, Oracle Data Guard, or Oracle Real Application Clusters. SQL Firewall works in conjunction with other Oracle Database security features such as Transparent Data Encryption (TDE), database auditing, and Oracle Database Vault. 

SQL Firewall supports (that is, it captures and enforces on) all SQL commands except transaction control commands ( ` SAVEPOINT ` , ` COMMIT ` , and ` ROLLBACK ` ). Additionally, SQL Firewall supports the SQL*Plus commands ` PASSWORD ` and ` DESCRIBE ` , and remote procedure calls (RPC) through database links. 

The following diagram explains how SQL Firewall operates inline within the Oracle Database kernel. 

Figure 1-1 SQL Firewall Process 

![Description of Figure 1-1 follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlfw/img/sql_firewall_inbound.png)[ Description of "Figure 1-1 SQL Firewall Process" ](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlfw/img_text/sql_firewall_inbound.md)

  1. A user logs in to the Oracle database through a web application. 
  2. The user runs SQL statements, creating inbound traffic to the Oracle database. 
  3. SQL Firewall inspects the incoming database connections and SQL statements, and enforces it against the permitted SQL statements and trusted connection paths in the allow-list policy for the user. SQL Firewall’s processing outcome is one of the following options: 
     * Allow the SQL for its subsequent execution. 
     * Allow the SQL and log it. 
     * Log and optionally block unauthorized SQL. 


