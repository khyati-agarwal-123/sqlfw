##  Auditing Oracle SQL Firewall Violations by Using Unified Audit Policies {#GUID-5B3BB2A3-B348-46C6-9146-C3E2C67C49C2} 

Oracle recommends that you audit SQL Firewall violations as violations indicate the occurrence of potential abnormal database access patterns. 

Auditing SQL Firewall violations with unified auditing records the violation in the database audit trail, ` UNIFIED_AUDIT_TRAIL ` data dictionary view. It is important that you turn on violation auditing after SQL Firewall is fully trained and the allow-lists of the user is complete, to avoid false positives and reduce unnecessary audit volume. 

You can create unified audit policies that are specific to SQL Firewall by specifying the ` SQL_FIREWALL ` component when you create the unified audit policy. When you query the ` UNIFIED_AUDIT_TRAIL ` , you can query the ` FW_ACTION_NAME ` and ` FW_RETURN_CODE ` columns. 

> **note:** Oracle Database mandatorily audits all invocations of the SQL Firewall ` DBMS_SQL_FIREWALL ` PL/SQL administrative procedures. 
