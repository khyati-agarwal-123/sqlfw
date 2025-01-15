##  Configuring Oracle SQL Firewall Using the DBMS_SQL_FIREWALL Package {#GUID-42527A25-6C70-4662-96BC-7CD5705E412A} 

A user who has the ` SQL_FIREWALL_ADMIN ` role can use the ` DBMS_SQL_FIREWALL ` PL/SQL package to configure Oracle SQL Firewall in the root or a pluggable database (PDB). 

  1. Connect to the root or PDB as a user who has been granted the ` SQL_FIREWALL_ADMIN ` role. 
  2. Enable SQL Firewall. 
    
        ```
    EXEC DBMS_SQL_FIREWALL.ENABLE;
    ```

  3. For every database user to protect with SQL Firewall in the Oracle database, enable SQL Firewall to learn the normal SQL traffic of the database user by capturing all the authorized SQL statements over trusted database connection paths. 

The examples in this procedure assume the user is a PDB user named ` APP ` . For example: 
    
        ```
    BEGIN
      DBMS_SQL_FIREWALL.CREATE_CAPTURE (
        username         => 'APP',
        top_level_only   => TRUE,
        start_capture    => TRUE
      );
    END;
    /
    ```

In this specification: 

     * ` username ` is the name of the application user that SQL Firewall will monitor. You can only create one capture for each user. You cannot create SQL Firewall captures for the ` SYS ` , ` SYSDG ` , ` SYSBACKUP ` , ` SYSRAC ` , ` SYSKM ` , ` DVSYS ` , ` LBACSYS ` , or ` AUDSYS ` users. 
     * ` top_level_only ` controls the level of SQL statements that are captured. 
       * ` TRUE ` generates capture logs only for top-level SQL statements, that is, statements that the user directly runs. 
       * ` FALSE ` generates capture logs for both top-level SQL statements and SQL commands issued from PL/SQL units. The default is ` FALSE ` . 
     * ` start_capture ` controls when the capture will be effective. 
       * ` TRUE ` enables SQL Firewall to start capturing the target user's activities right away. The default is ` TRUE ` . 
       * ` FALSE ` creates a capture for the user, but does not start the capture right away. When you want to start the capture later on, you must run the ` DBMS_SQL_FIREWALL.START_CAPTURE ` procedure for the user. For example: 
            
                        ```
            EXEC DBMS_SQL_FIREWALL.START_CAPTURE ('APP');
            ```

As an application service account, run the normal application SQL workload from the trusted database connection paths when the capture is started for the application service account. In the event of a change in application in the SQL workload following application patching, you may want SQL Firewall to unlearn and learn, starting over. You can delete the current capture, and create a new one. Specifically, if you want to restart the capture process, then you must first stop this capture (if it is started), then either purge the capture logs and start this capture again, or, delete this capture and create (and start) the capture again. 

  4. Review the capture logs and sessions logs to determine the adequacy of the capture. 

For example: 
    
        ```
    SELECT SQL_TEXT FROM DBA_SQL_FIREWALL_CAPTURE_LOGS WHERE USERNAME = 'APP';
    ```

  5. Stop the capture. 

For example: 
    
        ```
    EXEC DBMS_SQL_FIREWALL.STOP_CAPTURE ('APP');
    ```

  6. Generate the SQL Firewall policy with allow-lists for the user: 

A SQL Firewall policy with allow-lists sets the baseline for allowed SQL statements and allowed contexts. Allowed SQL statements constitute the approved SQL statements. Allowed contexts represent trusted database connection paths. SQL Firewall creates the allow-list based on data collected from existing capture logs for the user. 

For example: 
    
        ```
    EXEC DBMS_SQL_FIREWALL.GENERATE_ALLOW_LIST ('APP');
    ```

  7. To find the permitted and allowed SQL statements that the user can run, query the ` DBA_SQL_FIREWALL_ALLOWED_ ` * data dictionary views. 

For example: 
    
        ```
    SELECT SQL_TEXT FROM DBA_SQL_FIREWALL_ALLOWED_SQL WHERE USERNAME = 'APP';
    ```

To find the trusted database connection paths for the user, perform the following queries: 
    
        ```
    SELECT OS_PROGRAM FROM DBA_SQL_FIREWALL_ALLOWED_OS_PROG WHERE USERNAME = 'APP';
    ```
    
        ```
    SELECT OS_USER FROM DBA_SQL_FIREWALL_ALLOWED_OS_USER WHERE USERNAME = 'APP';
    ```
    
        ```
    SELECT IP_ADDRESS FROM DBA_SQL_FIREWALL_ALLOWED_ALLOWED_IP_ADDR WHERE USERNAME = 'APP';
    ```

  8. Optionally, add or modify entries in the allowed contexts by running the ` DBMS_SQL_FIREWALL.ADD_ALLOWED_CONTEXT ` and ` DBMS_SQL_FIREWALL.DELETE_ALLOWED_CONTEXT ` procedures. 

You can only add a context after you have generated the allow-list. A context can specify the client IP address, names of operating system users, or the operating system program that can be used for database connections. You can add as many context values as you need. For example, if the user's allowed context list does not contain the IP address 192.0.2.1 but you want to allow the user to connect from this IP after the enablement of the allow-list: 
    
        ```
    BEGIN
      DBMS_SQL_FIREWALL.ADD_ALLOWED_CONTEXT (
        username       => 'APP',
        context_type   => DBMS_SQL_FIREWALL.IP_ADDRESS,
        value          => '192.0.2.1'
       );
    END;
    /
    ```

To specify all possibilities for a specific ` context_type ` , enter the ` % ` wildcard. 

The following three types of ` context_type ` settings are valid: 

     * ` DBMS_SQL_FIREWALL.IP_ADDRESS ` accepts IPv4 and IPv6 addresses and subnets in the CIDR notation. It accepts the value ` Local ` (case sensitive) for local connections when the IP address is not available. 
     * ` DBMS_SQL_FIREWALL.OS_USERNAME ` accepts any valid operating system user name, such as ` oracle ` . 
     * ` DBMS_SQL_FIREWALL.OS_PROGRAM ` accepts any valid operating system program name that the user uses to run SQL statements, such as ` sqlplus ` or ` SQL Developer ` . 

You can query the following data dictionary views to check the contexts: 

     * ` DBA_SQL_FIREWALL_ALLOWED_IP_ADDR `
     * ` DBA_SQL_FIREWALL_ALLOWED_OS_USER `
     * ` DBA_SQL_FIREWALL_ALLOWED_OS_PROG `

  9. Enable the generated SQL Firewall policy to protect the database user. 

The SQL Firewall enforces checks on the allow-lists when the user connects to the database and issues SQL statements. 

This enablement becomes effective immediately, even in the existing sessions of the target user. 

For example: 
    
        ```
    BEGIN
      DBMS_SQL_FIREWALL.ENABLE_ALLOW_LIST (
        username       => 'APP',
        enforce        => DBMS_SQL_FIREWALL.ENFORCE_SQL,
        block          => TRUE
       );
    END;
    /
    ```

In this specification: 

     * ` username ` can be a specific user whose allow-list has been generated, or it can be all users whose allow-list are not currently enabled. To specify all users, use ` NULL ` as the value. 
     * ` enforce ` specifies one of the following enforcement types: 
       * ` DBMS_SQL_FIREWALL.ENFORCE_CONTEXT ` enforces the allowed contexts that have been configured. 
       * ` DBMS_SQL_FIREWALL.ENFORCE_SQL ` enforces the allowed SQL that has been configured. 
       * ` DBMS_SQL_FIREWALL.ENFORCE_ALL ` enforces both allowed contexts and allowed SQL. This setting is the default. 
     * ` block ` specifies the following: 
       * ` TRUE ` blocks the user's database connection or the user's SQL execution whenever the user violates the allow-list definition. 
       * ` FALSE ` allows unmatched user database connections or SQL commands to proceed. This setting is the default. 

SQL Firewall always generates a violation log for any unmatched user database connection or SQL statement regardless of the enforcement option. 

At this stage, if the user attempts to perform a SQL query that violates the allow-list and you have specified SQL Firewall to block this SQL, then an ` ORA-47605: SQL Firewall violation ` error appears. 

  10. Monitor the violation log for abnormal SQL connection attempts or SQL queries that are reported if they are not in allow-list. 

For example: 
    
        ```
    SELECT SQL_TEXT, FIREWALL_ACTION, IP_ADDRESS, CAUSE, OCCURRED_AT
    FROM DBA_SQL_FIREWALL_VIOLATIONS WHERE USERNAME = 'APP';
    ```

Output similar to the following appears: 
    
        ```
    SQL_TEXT                                                  FIREWALL_ACTION  IP_ADDRESS   CAUSE            OCCURRED_AT
    –-------------------------------------------------------- –--------------- –----------  –---------------- –----------------------------------
    
    SELECT SALARY FROM HR.EMPLOYEES WHERE SALARY >:"SYS_B_0"  BLOCKED          192.0.2.146  Context violation 12-MAY-23 11.12.39.626053 PM +00:00
    ```




**Related Topics**

  * [ Configuring and Managing Oracle SQL Firewall with the DBMS_SQL_FIREWALL Package ](configuring-and-managing-oracle-sql-firewall-dbms_sql_firewall-package.md#GUID-1589CDC3-AA0C-4BBF-A6D7-266E0E1BA28E)
  * [ Oracle SQL Firewall Data Dictionary Views ](oracle-sql-firewall-data-dictionary-views.md#GUID-A0C5F3D8-3F64-4493-B3A6-223F974C8786)


