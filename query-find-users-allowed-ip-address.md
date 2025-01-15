##  Query to Find a User's Allowed IP Address {#GUID-F1EC8B78-0564-452E-835F-F7A02952D6CE} 

The ` DBA_SQL_FIREWALL_ALLOWED_IP_ADDR ` data dictionary view shows the IP address that a user is allowed to use. 

For example: 
    
    
    ```
    SELECT IP_ADDRESS FROM DBA_SQL_FIREWALL_ALLOWED_IP_ADDR WHERE USERNAME = 'HR';
     
    IP_ADDRESS
    ------------
    192.0.2.1
    ```

**Related Topics**

  * [ *Oracle Database Reference*  ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/sqlfw&id=REFRN-GUID-D45DEF6E-8020-4368-AB8A-B611C425AEBB)


