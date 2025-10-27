##  <span style="background-color:#ffb84d; color:white; padding:2px 6px; border-radius:4px;">Medium</span> MAGIC TABLES
Magic Tables are special, virtual tables that SQL Server internally maintains during `INSERT, UPDATE, or DELETE` operations. They are not physical tables but can be used in triggers to access the data affected by these operations. These tables are called INSERTED and DELETED. 
**Scenarios Where Magic Tables Are Used**
- Triggers: Magic tables are most used in triggers to track changes in the data during `INSERT, UPDATE, or DELETE` operations
**Key Characteristics of Magic Tables**
1. Read-Only: Magic tables are read-only, meaning you cannot modify the data in these tables.
2. Scope: Magic tables are available only within the scope of a trigger. Once the trigger execution is complete, the magic tables are no longer available.
3. Temporary: These tables exist only for the duration of the trigger execution and are automatically managed by SQL Server. 
<br>

**Limitations of Magic Tables**
- Performance Impact: Using triggers that rely heavily on magic tables can introduce performance overhead for large-scale operations.
- No Direct Access: Magic tables are accessible only within triggers. You cannot query them directly outside the trigger.
