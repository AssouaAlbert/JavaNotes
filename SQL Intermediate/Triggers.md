# Triggers

In SQL, a trigger is a database object that is associated with a table and is automatically executed in response to certain events or actions on the table. Triggers are used to enforce referential integrity, implement business rules, and automate actions when data is modified in a table. There are two main types of triggers: `AFTER` triggers and `INSTEAD OF` triggers.

1. **AFTER Triggers:** These triggers are executed automatically after an event, such as an `INSERT`, `UPDATE`, or `DELETE` operation, has taken place on the associated table. They are commonly used to log changes, enforce data consistency, or trigger additional actions.

2. **INSTEAD OF Triggers:** These triggers are executed before an event and allow you to replace the default operation with custom logic. They are often used with views and are useful for implementing complex data modification rules.

Here's a basic overview of SQL triggers and their usage:

**Creating an AFTER Trigger:**

```sql
CREATE TRIGGER trigger_name
AFTER INSERT ON table_name
FOR EACH ROW
BEGIN
  -- Trigger logic here
  -- This trigger is executed after an INSERT operation on the table
END;
```

**Creating an INSTEAD OF Trigger:**

```sql
CREATE TRIGGER trigger_name
INSTEAD OF INSERT ON view_name
BEGIN
  -- Trigger logic here
  -- This trigger is executed instead of an INSERT operation on the view
END;
```

Here are a few common use cases for SQL triggers:

1. **Auditing Changes:** You can use AFTER triggers to log changes made to a table, maintaining an audit trail of who, when, and what data was modified.

2. **Enforcing Data Integrity:** Triggers can enforce referential integrity by preventing INSERT, UPDATE, or DELETE operations that would violate defined constraints.

3. **Automating Actions:** You can use triggers to automatically update related data or perform actions in response to changes in a table. For example, updating denormalized data in another table when data in the original table changes.

4. **Complex View Manipulation:** INSTEAD OF triggers can be used with views to allow custom data manipulation that would not be possible with standard views.

It's important to use triggers judiciously, as they can add complexity to a database and, if poorly designed, lead to performance issues. When implementing triggers, consider the potential impact on data consistency, database performance, and the maintenance of trigger logic. Additionally, ensure that triggers are documented and tested thoroughly.

# Syntax to create a trigger

```sql
create trigger [trigger_name] [before | after]
{insert | update | delete}
on [table_name]
[for each row]
[trigger_body]

```
