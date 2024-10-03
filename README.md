These tasks guide you through creating, managing, and deleting PDBs in an Oracle CDB, along with configuring Oracle Enterprise Manager for monitoring and administration. 
This approach showcases the flexibility and ease of use of the multitenant architecture in Oracle databases.bellow are some of the queries to consider while perfoming out this task of oracle enterprise with CDB and PDB

ALTER SESSION SET CONTAINER=cdb$root;

This command sets the current session to the root container of the CDB. 
All subsequent commands will be executed in this context, which is necessary for managing PDBs.

CREATE PLUGGABLE DATABASE plsql_class2024db 
ADMIN USER chris_birasa IDENTIFIED BY 'password123' 
FILE_NAME_CONVERT=('D:\oracle19c\admin\orcl\pdbseed','D:\oracle19c\admin\orcl\plsql_class2024db');

This command creates a new PDB named plsql_class2024db with an administrative user

CREATE PLUGGABLE DATABASE plsql_class2024db ADMIN USER ch_plsqlauca IDENTIFIED BY 'your_password' FILE_NAME_CONVERT=('D:\oracle19c\admin\orcl\pdbseed','D:\oracle19c\admin\orcl\plsql_class2024db');

ALTER PLUGGABLE DATABASE plsql_class2024db OPEN;
This command opens the newly created PDB, making it available for connections and operations.

ALTER PLUGGABLE DATABASE plsql_class2024db SAVE STATE;
This command saves the state of the PDB so that it will automatically open when the CDB is restarted. 
It simplifies management by maintaining the preferred state.

CREATE PLUGGABLE DATABASE ch_to_delete_pdb ADMIN USER ch_plsqlauca IDENTIFIED BY 'password123' FILE_NAME_CONVERT=('D:\oracle19c\admin\orcl\pdbseed','D:\oracle19c\admin\orcl\er_to_delete_pdb');

ALTER PLUGGABLE DATABASE ch_to_delete_pdb OPEN;
This command opens the newly created PDB  making it available for use.

ALTER PLUGGABLE DATABASE er_to_delete_pdb CLOSE IMMEDIATE;
This command immediately closes the specified PDB, terminating any active connections.

DROP PLUGGABLE DATABASE er_to_delete_pdb INCLUDING DATAFILES;
this command permanently deletes the PDB from the CDB, including its data files. It ensures that all resources associated with the PDB are released.




