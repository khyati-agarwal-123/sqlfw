##  Getting Started with Oracle SQL Firewall {#GUID-E16DAF38-B4D3-439D-8D01-A8B39AB76C62} 

To get started with Oracle SQL Firewall, you follow three steps: first, enable Oracle SQL Firewall; second, capture the user's normal SQL activities; and third, enable and enforce allow-lists. 

  1. Enable SQL Firewall.  As an administrator with appropriate privileges, enable SQL Firewall in the Oracle database. 
  2. Capture the normal SQL activities.  For every database user that you want to protect with SQL Firewall, you must enable SQL Firewall to learn the normal SQL traffic of the database user. It does this by capturing all the authorized SQL statements over trusted database connection paths. You can query SQL Firewall-specific data dictionary views to review this captured data to determine if the collected SQL statements and connection paths is adequate to constitute the allow-lists. 

     After you review the captured SQL statements, you can generate a SQL Firewall policy with allow-lists that set the baseline for allowed SQL statements and allowed contexts. Allowed SQL statements constitute the approved SQL statements. At run-time, when the policy is enforced, any incoming SQL queries that have a structure syntactically similar to the SQL signature in the policy allow-list will be passed for execution if the corresponding run-time execution context also meets the set of allowed contexts. Allowed contexts represent trusted database connection paths and consist of three distinct groups—client IP addresses, operating system program names, and operating system user names. When the user connects to the database, SQL Firewall checks the current session context attributes, and ensures that access to the database comes exclusively from trusted endpoints defined in the allow-lists. You can review the allow-list and make modifications by using the ` DBMS_SQL_FIREWALL ` procedures any time. 

  3. Enable and enforce the allow-lists.  Enabling the generated SQL Firewall policy protects the database user. SQL Firewall enforces and checks the allow-lists when the user connects to the database and issues SQL statements. You can let SQL Firewall know if you want to enforce checks on allowed contexts, allowed SQL statements, or both. If the database connection paths and SQL statements in the incoming SQL traffic do not match the entries in the enabled and enforced allow-lists, then a SQL Firewall violation is triggered and this incident is logged in the violation log. You can let SQL Firewall know how to respond to SQL Firewall violation incident: allow the traffic to proceed to the database or block. Blocking raises an ` ORA-47605: SQL Firewall violation ` error, which prevents anomalous database access, without disrupting client connections for SQL violations following a mismatch of SQL statements. However, blocking for context violations will disrupt and terminate client connections following a mismatch of contexts. 

     SQL Firewall raises and logs violations in real-time for every unmatched scenario of database connection or SQL command execution against the entries in the enabled allow-lists of the SQL Firewall policy. A security administrator can monitor the SQL Firewall violation log ` DBA_SQL_FIREWALL_VIOLATIONS ` to detect the presence of these abnormalities. You may want to audit SQL Firewall violations (especially the blocked ones); their occurrence potentially indicates abnormal database access attempts including SQL Injection and credential theft or abuse. Auditing violations places a record of the violation in the database audit trail, where it can be protected from tampering. 




Key points to consider are as follows: 

  * Oracle Database mandatorily audits all SQL Firewall administrative actions and writes these to the unified audit trail data dictionary view, ` UNIFIED_AUDIT_TRAIL ` . You can also create unified audit policies to monitor SQL Firewall violations. Another way to monitor and troubleshoot SQL Firewall is to use the ` SQL_FIREWALL ` trace file setting. 
  * You can export and import SQL Firewall metadata, including existing allow-lists, by using the Oracle Data Pump ` EXPDB ` and ` IMPDB ` utilities. 
  * Oracle recommends that you periodically monitor and purge violations logs by using the ` DBMS_SQL_FIREWALL.PURGE_LOG ` procedure as part of routine SQL Firewall management tasks. In a well trained environment, violation logs are not expected to be voluminous. 
  * SQL Firewall captures SQL statements that the user issues directly or from PL/SQL units that the user invokes in sessions of target users. 
  * SQL Firewall captures only SQL statements that are executed successfully. That is, if a SQL statement fails to execute due to any error, SQL Firewall does not capture the corresponding statement. 
  * SQL Firewall captures SQL statements before any internal query transformation (for example, views or macro expansions, or Oracle Virtual Private Database policy enforcement) is performed. 
  * SQL Firewall normalizes captured SQL statements and replaces literal values with special symbols before storing them in the log tables. 
  * The session context attributes (client IP address, operating system user name, and operating system program name) are checked only once during session creation. 
  * You can append to the existing allow-list anytime by using either the ` DBMS_SQL_FIREWALL.APPEND_ALLOW_LIST ` procedure or the ` DBMS_SQL_FIREWALL.APPEND_ALLOW_LIST_SINGLE_SQL ` procedure from the following two sources: 
    * Violation log: ` DBA_SQL_FIREWALL_VIOLATIONS ` data dictionary view 
    * Capture log: ` DBA_SQL_FIREWALL_CAPTURE_LOGS ` data dictionary view 
  * For existing sessions that were created before the allow-list is enabled, SQL Firewall also checks the allowed contexts, but does not terminate existing sessions even if they have unmatched session contexts. In this case, SQL Firewall does not log the violation. 


