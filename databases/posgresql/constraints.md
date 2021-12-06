## Cascading deletes
Cascading deletes allow you to configure deletion behavior on relations (e.g. specify a rule like "when a user is deleted, all their posts should be automatically deleted too"). The database will then enforce this behavior when records are deleted.

There generally are five options for configuring deletion behavior in PostgreSQL (quoting from the PostgreSQL docs):

**NO ACTION (default)**: If any referencing rows still exist when the constraint is checked, an error is raised

**RESTRICT**: Prevents deletion of a referenced row. The essential difference between these two choices is that NO ACTION allows the check to be deferred until later in the transaction, whereas RESTRICT does not.

**CASCADE**: When a referenced row is deleted, row(s) referencing it should be automatically deleted as well.

**SET NULL**: Causes the referencing columns to be set to NULL when the referenced row is deleted.

**SET DEFAULT**: Causes the referencing columns to be set to their default values when the referenced row is deleted. Note that these do not excuse you from observing any constraints. For example, if an action specifies SET DEFAULT but the default value would not satisfy the foreign key, the operation will fail.