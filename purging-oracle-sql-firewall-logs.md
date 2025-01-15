##  Purging Oracle SQL Firewall Logs {#GUID-3D110166-7621-4D2C-AD10-731B989F153E} 

Periodically, you should purge the logs that Oracle SQL Firewall generates by using the ` DBMS_SQL_FIREWALL.PURGE_LOG ` procedure. 

SQL Firewall generates and stores the violation logs in a log table. In an ideal SQL Firewall trained environment, the violation log is not expected to be large. Oracle recommends that you periodically purge these logs. After you verify that the generated allow-list is valid, you should purge unnecessary logs to reclaim the disk space that the logs are using. 

  1. Log in to the root or the pluggable database (PDB) where SQL Firewall is configured as a user who has been granted the ` SQL_FIREWALL_ADMIN ` role. 
  2. Optionally, as a user who has the ` SELECT ANY DICTIONARY ` system privilege, query the following data dictionary views to check the logs that you plan to purge: 

     * ` DBA_SQL_FIREWALL_CAPTURE_LOGS `
     * ` DBA_SQL_FIREWALL_VIOLATIONS `

  3. Connect to the PDB a user who has been granted the ` SQL_FIREWALL_ADMIN ` role. 
  4. Run the ` DBMS_SQL_FIREWALL.PURGE_LOG ` procedure. 

For example: 
    
        ```
    BEGIN
      DBMS_SQL_FIREWALL.PURGE_LOG (
        username    => 'APP',
        purge_time  => '2023-02-01 00:00:00.00 -08:00',
        log_type    => 'DBMS_SQL_FIREWALL.ALL_LOGS'
       );
     END;
    /
    ```

In this specification: 

     * ` username ` is the target user for which this SQL Firewall configuration was created. If you omit this value, then Oracle Database purges all logs that match the ` purge_time ` and ` log_type ` settings. 
     * ` purge_time ` is the timestamp (in ` TIMESTAMP ` format) that you can specify to purge only logs that were generated before a certain time. If you omit this value, then Oracle Database purges all logs, regardless of the time when they were generated. 
     * ` log_type ` is the type of the logs to be purged. If you do not specify a value, then the default is ` DBMS_SQL_FIREWALL.ALL_LOGS ` . Specify one of the following constants: 
       * ` DBMS_SQL_FIREWALL.CAPTURE_LOG `
       * ` DBMS_SQL_FIREWALL.VIOLATION_LOG `
       * ` DBMS_SQL_FIREWALL.ALL_LOGS ` (default) 




**Related Topics**

  * [ *Oracle Database Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=REFRN-GUID-B7CE1C02-2FD4-47D6-80AA-CF74A60CDD1D)


