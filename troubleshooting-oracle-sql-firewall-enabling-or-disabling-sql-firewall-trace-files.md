##  Troubleshooting Oracle SQL Firewall by Enabling or Disabling SQL Firewall Trace Files {#GUID-330A744E-B550-4919-9892-A902630B1521} 

As a user who has been granted the ` ALTER SESSION ` or ` ALTER SYSTEM ` system privilege, you can generate trace files within the PDB in which you are using Oracle SQL Firewall. 

You can set SQL Firewall trace events in both the CDB and in individual PDBs. 

  * To enable tracing for SQL Firewall, use one of the following statements: 
    
```
ALTER SESSION SET EVENTS 'TRACE[SQL_FIREWALL] DISK=trace_level';
ALTER SYSTEM SET EVENTS 'TRACE[SQL_FIREWALL] DISK=trace_level';
```

In this specification, replace ` trace_level  ` with one of the following values: 

    * ` LOW ` shows the minimum tracing information. 
    * ` HIGH ` shows more detailed tracing information, plus the information returned by ` LOW ` . 
    * ` HIGHEST ` shows the most detailed tracing information, plus the information returned by ` HIGH ` and ` LOW ` . 
  * To disable tracking for SQL Firewall, use one of the following statements: 
    
```
ALTER SESSION SET EVENTS 'TRACE[SQL_FIREWALL] OFF';
ALTER SYSTEM SET EVENTS 'TRACE[SQL_FIREWALL] OFF';
```



