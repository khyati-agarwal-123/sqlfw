##  Oracle SQL Firewall in a Multitenant Environment {#GUID-0718FE20-4385-4889-8DAF-0D07D15DFEF9} 

Oracle SQL Firewall is affected at both the CDB root level and the individual PDB level. 

You can run the SQL Firewall processes and set SQL Firewall trace events in both the CDB and individual PDBs. 

In the CDB root: 

  * You can enable SQL Firewall in the CDB root container, and then create SQL Firewall policies, enable or disable SQL Firewall, start or stop captures, and enable or disable allow-lists. These settings apply to the CDB root only. 
  * In an Oracle Database Vault operations control environment, there are no restrictions in using SQL Firewall. 



In individual PDBs: 

  * You can enable SQL Firewall in an individual PDB, and then create SQL Firewall policies, enable or disable SQL Firewall, start or stop captures, and enable or disable allow-lists. These settings apply to the current PDB only. 
  * In a Database Vault operations control environment, common users cannot start or stop captures on local users, nor can they enable or disable allow-lists on local users. 


