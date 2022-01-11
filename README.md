# PL-SQL_Scripts
Collection of PL/SQL scripts that I have written that I use for Oracle database management 

These are various PL/SQL scripts I have written to help me manage Oracle 11g, 12c, and 19c databases on AIX and Linux systems.

1. [truncate_permitting_trigger.sql](/triggers/truncate_permitting_trigger/truncate_permitting_trigger.sql) : A user was required to be able to truncate certain application tables not owned by them, so the user was granted the "DROP ANY TABLE" system privilege (to truncate a table in Oracle, the table must be in your own schema or you must have the "DROP ANY TABLE" system privilege. But this privilege allows you to then truncate or drop every single table in the database). This trigger was written so that the user could only truncate the pre-approved application tables (the owner and names of which are stored in a table created by me: [ALL_TRUNC8_PERMS](/triggers/truncate_permitting_trigger/ALL_TRUNC8_PERMS.sql)) and would be prevented from being able to truncate every table in the database. If the user attempts to truncate a non-approved table, the trigger will prevent the truncate, cause the user to receive an error, the occurrence will be recorded in an Oracle table for record-keeping and auditing purposes (a table called [CAPTURED_TRUNC8_ERRS](/triggers/truncate_permitting_trigger/CAPTURED_TRUNC8_ERRS.sql)), and an email will be sent to notify the DBA's.     
