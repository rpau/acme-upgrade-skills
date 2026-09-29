# acme-upgrade-skills

A repository example for custom Claude Code skills to automate code upgrades and migrations.

## Skills Included

- **notification-exception-upgrade**: Upgrade Java exception handling for `com.acme.Notification#sendNotification` API change from `IOException` to `AcmeNotificationException`

## Installation

### Prerequisites

- Maven 3.6+
- Java 8+

### Building and Installing to Local Maven Repository

1. **Clone or navigate to this repository:**
   ```bash
   cd acme-upgrade-skills
   ```

2. **Build and install to local .m2 repository:**
   ```bash
   mvn clean install
   ```

   This will:
   - Package all skills into a zip file
   - Install the artifact to your local Maven repository

3. **Verify the installation:**
   ```bash
   ls -la ~/.m2/repository/com/acme/skills/acme-upgrade-skills/1.0.0/
   ```

   You should see:
   - `acme-upgrade-skills-1.0.0.zip` (the skills package)
   - `acme-upgrade-skills-1.0.0.pom` (Maven metadata)

### Using the Skills

Once installed in your local Maven repository, the skills are available as:

**Maven Coordinates:**
- **GroupId:** `com.acme.skills`
- **ArtifactId:** `acme-upgrade-skills`
- **Version:** `1.0.0`
- **Type:** `zip`

#### In Claude Code

The skills can be integrated into Claude Code projects by:

1. Extracting the zip from the Maven repository
2. Copying the skill folders to your project's `skills/` directory
3. Invoking them via slash commands (e.g., `/notification-exception-upgrade`)

### Development

To add new skills:

1. Create a new folder under `skills/` with your skill name
2. Create a `SKILL.md` file with your skill documentation and implementation
3. Rebuild and reinstall:
   ```bash
   mvn clean install
   ```

### Maven Repository Structure

After installation, the artifact is stored at:
```
~/.m2/repository/com/acme/skills/acme-upgrade-skills/1.0.0/acme-upgrade-skills-1.0.0.zip
```

The zip file contains only the skill folders (no root wrapper), making it easy to extract and deploy.
