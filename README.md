## Script: Add Database to AG with Automatic Seeding (SQLCMD Mode)

**Description**:
This script adds a database to an existing Always On Availability Group and enables **automatic seeding** on the secondary replicas. It modifies the seeding mode on each replica, adds the database from the primary, and grants necessary permissions for automatic database creation on the secondaries.

**Steps Performed**:
1. Sets `SEEDING_MODE = AUTOMATIC` on each secondary replica.
2. Adds the database to the AG from the Primary.
3. Grants `CREATE ANY DATABASE` on the secondaries to enable automatic seeding.

**Notes**:
- Must be executed in **SQLCMD Mode**.
- Replace the following placeholders before executing:
  - `[AG_Name]`
  - `[Database_Name]`
  - `Seconary-1`, `Seconary-2`
- Ensure the database already exists and is synchronized on the **Primary**.

**Requirements**:
- SQL Server 2016 or later.
- Always On AG must be configured and healthy.
- Replica endpoints must be active.
- Run with `sysadmin` privileges.

**Important**:
Ensure that the secondaries have enough disk space to accept the automatic seed of the database being added.
