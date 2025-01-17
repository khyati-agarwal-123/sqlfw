##  Oracle SQL Firewall and Oracle Data Pump {#GUID-73801BA5-B450-48ED-8913-564E2A66E6DA} 

You can use Oracle Data Pump to export and import Oracle SQL Firewall captures and allow-list metadata. 

###  About Oracle Data Pump Export and Import Operations on Oracle SQL Firewall Metadata {#GUID-1EB62A08-8B88-464A-AB43-891566FEC66B} 

Oracle SQL Firewall integrates with Oracle Data Pump to support the export and import of the SQL Firewall metadata, including the metadata for captures and allow-lists. 

This is typically required in scenarios where the training can be done once on a non-production database, and then SQL Firewall can be enabled on multiple production databases using the allow-list that was generated during the non-production training stage. 

Oracle Database maintains the status of captures and allow-lists during the export and import operations, unless you are merging an allow-list from the source database into an existing allow-list in the target database. For example, if a capture is enabled in the source database at the export time, it will be enabled in the target database after the import operation completes. This is similar if you are importing an allow-list when there is no allow-list for the same user in the target database before the import operation. 

If you are merging an allow-list from the source database into an existing allow-list in the target database, the settings (such as ` status ` , ` top_level_only ` , ` enforce ` , and ` block ` ) of the allow-list in the target database remain the same as before the import operation. Only the allowed SQL and contexts are merged. 

For Oracle Data Pump, Oracle supports the export or import of all the existing SQL Firewall metadata (that is, captures and allow-lists) as a whole. Oracle does not support the export or import of a specific capture or a specific allow-list through Oracle Data Pump. 

If you only want to export or import the allow-list for one user, from one specific database to another, then use the ` DBMS_SQL_FIREWALL.EXPORT_ALLOW_LIST ` or ` DBMS_SQL_FIREWALL.IMPORT_ALLOW_LIST ` procedure. (These two procedures do not rely on Oracle Data Pump and can be used independently.) Oracle does not support the export and import of SQL Firewall logs (that is, capture and violation logs). 

###  Cases Where Oracle Data Pump Skips the Import for an Oracle SQL Firewall Capture or Allow-List {#GUID-9C68566D-0682-404C-8679-D5D13F473F97} 

During an import operation, Oracle Data Pump will skip a particular Oracle SQL Firewall capture or allow-list and continue to import other captures or allow-lists for certain cases. 

These cases are as follows: 

  * If the target users do not exist in the target database, then the captures and allow-lists for those non-existing users are not imported. 

  * If an allow-list refers to one or more current users that do not exist in the target database, then this allow-list is not imported. 

  * For an allow-list to be imported, if an allow-list for the same user already exists in the target database and its ` top_level_only ` setting is different than the allow-list to be imported, then the allow-list is not imported. 

  * For an allow-list to be imported, if a capture for the same user already exists in the target database and its ` top_level_only ` setting is different than the allow-list to be imported, then the allow-list is not imported. 

  * If an allow-list to be imported is enabled, and in the target database, there is an enabled capture for the same user but there is no disabled allow-list for the same user, then the allow-list is not imported to avoid having an enabled capture and an enabled allow-list for the same user at the same time. 

  * If a capture to be imported already exists for the same user in the target database, then the capture is not imported. 

  * If a capture to be imported is enabled, and there is an enabled allow-list for the same user in the target database, then the capture is not imported to avoid having an enabled capture and an enabled allow-list for the same user at the same time. 

  * For a capture to be imported, if an allow-list for the same user already exists in the target database and its ` top_level_only ` setting is different than the capture to be imported, then the capture is not imported. 




###  Using Oracle Data Pump with Oracle SQL Firewall {#GUID-5DA46FBB-6223-4312-8689-521DC2880422} 

You can use the ` expdp ` and ` impdp ` commands to export and import Oracle SQL Firewall captures and allow-lists metadata. 

  1. Log in to the server where SQL Firewall is used. 
  2. At the command line, perform the Oracle Data Pump export or import operation. 
     * To export SQL Firewall metadata, use the following syntax: 
        
```
expdp user_name@pdb_name FULL=Y DIRECTORY=dumpfile_dir INCLUDE=SQL_FIREWALL dumpfile=dumpfile_name.dmp LOGFILE=filename.log
```

In this specification: 

       * ` FULL=Y ` , which enables full export mode. SQL Firewall metadata will be exported only with the full export mode. 
       * ` INCLUDE=SQL_FIREWALL ` can be used in the ` INCLUDE ` or ` EXCLUDE ` filter. This tag is optional. It enables you to export and import just the SQL Firewall metadata from one database to another. 

For example: 
        
```
expdp "hr@hr_pdb" FULL=Y DIRECTORY=sql_fw_dumpfiles INCLUDE=SQL_FIREWALL DUMPFILE=sql_fw_app.dmp LOGFILE=sql_fw_app.log
Enter password: password
```

     * To import SQL Firewall metadata: 
        
```
impdp user_name@pdb_name FULL=Y DIRECTORY=dumpfile_dir INCLUDE=SQL_FIREWALL dumpfile=dumpfile_name.dmp LOGFILE=filename.log 
```

For example: 
        
```
impdp "hr@hr_pdb" FULL=Y DIRECTORY=dumpfile_dir INCLUDE=SQL_FIREWALL dumpfile=sql_fw_app.dmp LOGFILE=sql_fw_app.log
Enter password: password
```




**Related Topics**

  * [ *Oracle Database Utilities*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=SUTIL-GUID-33880357-06B1-4CA2-8665-9D41347C6705)


