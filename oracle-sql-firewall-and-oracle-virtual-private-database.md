##  Oracle SQL Firewall and Oracle Virtual Private Database {#GUID-7E98A867-47DA-40E8-B4E3-D91BDBD932C6} 

When Oracle Virtual Private Database policies are run, Oracle SQL Firewall captures SQL commands right after their executions. 

However, SQL Firewall does not consider any modification or transformation that is made by the database kernel (for example, views, synonyms, SQL macro expansion, Virtual Private Database enforcement, and so on). You should train SQL Firewall to capture all the expected incoming SQL statements to formulate the allow-list. 
