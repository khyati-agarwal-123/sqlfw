##  Managing Performance for Capture Logs {#GUID-229866B6-7CE6-4C32-AD7C-B5448FF9F72A} 

Depending on application workloads, Oracle SQL Firewall may generate a large volume of capture logs. 

To minimize the adverse impact on database performance, Oracle SQL Firewall relies internally on Fast Ingest for better write performance if sufficient memory is available. To make full use of SQL Firewall, Oracle recommends that you do the following: 

  * Allocate at least an additional 2G to the ` LARGE_POOL_SIZE ` parameter setting, on top of the existing ` LARGE_POOL_SIZE ` requirement. 
  * Resize the ` SGA_TARGET ` parameter setting to include this additional requirement. Ensure that the final size is 8G or more. 



**Related Topics**

  * [ *Oracle Database Performance Tuning Guide*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=TGDBA-GUID-CFADC9EA-2E2F-4EBB-BA2C-3663291DCC25)


