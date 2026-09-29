# Notification Exception Upgrade Skill

Upgrade Java exception handling for `com.acme.Notification#sendNotification` API change from `IOException` to `AcmeNotificationException`.

## What this skill does

This skill helps identify and upgrade all Java catch clauses in the codebase that need to be updated to handle the new exception type:
- **Old behavior**: `Notification#sendNotification` threw `IOException`
- **New behavior**: `Notification#sendNotification` throws `AcmeNotificationException`

The skill will:
1. Scan the project for all Java files that invoke `Notification#sendNotification` (directly or indirectly)
2. Identify catch clauses that catch `IOException` and may need updating
3. Guide you through updating the exception handling to use `AcmeNotificationException`
4. Ensure proper import statements are added where needed

## How to use

```
/notification-exception-upgrade [target-directory]
```

**Parameters:**
- `target-directory` (optional): The directory to scan. Defaults to the current working directory.

## What to expect

The skill will:
1. Search for Java files containing calls to `Notification.sendNotification()`
2. List all classes and methods that need updating
3. For each location, show the current catch clause and suggest the upgrade
4. Apply the changes to your files
5. Add necessary imports for `AcmeNotificationException` if not already present

## Example workflow

```bash
# Scan current project
/notification-exception-upgrade .

# Scan specific directory
/notification-exception-upgrade ./src/main/java
```

## What gets updated

- `catch (IOException e)` → `catch (AcmeNotificationException e)` in methods calling `Notification#sendNotification`
- Removes `IOException` from throws clauses where it's only needed for this method
- Adds import for `com.acme.AcmeNotificationException` where needed
- Updates JavaDoc `@throws` tags accordingly

## Important notes

- The skill preserves catch block logic - only the exception type and throws declarations change
- If a method catches `IOException` for other reasons, the skill will flag this for manual review
- Make sure to test your code after running this upgrade
