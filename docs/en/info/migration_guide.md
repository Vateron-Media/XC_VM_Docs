<h1 align="center">🧭 XC_VM Migration Guide</h1>

<p align="center">
  Easily migrate from compatible IPTV systems using the built-in XC_VM migration tool.
</p>

---

## 📚 Navigation

* [⚙️ Before You Start](#before-you-start)
* [🚀 Migration Steps](#migration-steps)
* [🔑 Restoring Access After Migration](#restoring-access-after-migration)
* [🧩 Post-Migration](#post-migration)
* [🖥️ Load Balancer Preparation](#load-balancer-preparation)

---

## ⚙️ Before You Start

> 💡 **Recommendation:**
> It’s best to perform migration on a **fresh XC_VM installation**.

> ⚠️ **Important:**
> **System and panel settings are NOT migrated.**
> Only database data supported by the migration process is transferred.
> You must reconfigure all settings manually after migration.

If you decide to use an **existing installation**, note the following:

* XC_VM **will delete all tables** in your main database that match the data found in your migration database.
* Always **create backups** before performing migration.

---

## 🚀 Migration Steps

### 1. Upload Backup

Upload your existing database backup to the XC_VM server via **SFTP**.
In this example, it is located at:

```
/tmp/backup.sql
```

### 2. Restore Backup to Migration Database

Use the tools script to clear the existing migration database and restore the backup:

```bash
/home/xc_vm/tools migration "/tmp/backup.sql"
```

### 3. Start Migration

If the restoration completed without errors, you can start the migration using one of two methods:

#### 🧩 Option 1 — Command Line (Recommended)

Run the migration manually:

```bash
/home/xc_vm/bin/php/bin/php /home/xc_vm/includes/cli/migrate.php
```

#### 🌐 Option 2 — Web Installer

If you prefer not to use the command line, you can return to the **web installer** via the link provided during panel setup.
Select the **“Migration”** option and follow the on-screen instructions to complete the process interactively.

You will see real-time progress updates while XC_VM migrates your data.
Once complete, you will be able to log in to your system.

---

## 🔑 Restoring Access After Migration

If you cannot log in (e.g., due to missing username/password or invalid access code), you can use **rescue tools**:

### Create a Rescue Access Code

```bash
/home/xc_vm/tools access
```

### Create an Administrator to Restore Access

```bash
/home/xc_vm/tools user
```

> ⚠️ After logging in, immediately **change the access code and administrator credentials**.

---

## 🖥️ Load Balancer Preparation

You will need to reinstall the OS on the load balancers.

---

> **Warning:**  
> After migration, certain configuration values are **not automatically migrated** and must be manually reconfigured.  
> This includes **providers** and **API keys (e.g., TMDb)**. If metadata fetching or stream title syncing does not work after migration, please follow the post-migration steps to restore full functionality.  
> Failure to reconfigure these settings may lead to unexpected behavior.

## 🧩 Post-Migration Steps

After completing a migration, additional manual steps are required to restore full functionality.  
Not all configuration values, providers, secrets, or runtime state are migrated automatically.

Skipping these steps may result in missing features or behavior that appears broken but is expected.

---

### 1. Reinstall Load Balancers and Restart Streams

- Reinstall or reconfigure load balancers as required for your environment.
- Manually start all streams once the migration has completed.
- Verify that streams are accessible and operating normally.

> Stream runtime state is not preserved during migration and must be reinitialized manually.

---

### 2. Review and Update `XC_VM` Default Settings

- Review all `XC_VM` default configuration values.
- Update any environment-specific settings (paths, limits, networking, performance tuning, etc.).
- **Do not assume defaults will match your pre-migration setup, as these settings are not migrated.**

---

### 3. Verify Main Server Configuration

Review the main server configuration to ensure it matches your environment, including:

- Domains and hostnames  
- SSL / TLS configuration  
- Reverse proxy or networking settings  

#### Providers and API Keys Are Not Migrated

The following are not migrated and must be reconfigured manually after migration:

- **Providers**
- **TMDb API key**

This is expected behavior.

> **Important:**  
> If metadata fetching (e.g., TMDb) does not work after migration, verify that the API key has been re-added and the relevant provider has been configured.  
> This does not indicate a migration bug.

> Providers are not migrated at this time. This may become a feature enhancement in the future but is expected behavior for now.

---

### 4. Common Post-Migration Issues

#### Metadata Is Not Fetching (TMDb)

**Cause:**  
TMDb API key and provider configuration are not migrated.

**Resolution:**  
Reconfigure the TMDb provider and re-add the API key in the main server settings.

---

#### Providers Are Missing or Disabled

**Cause:**  
Providers are **not migrated** as part of the migration process.

**Resolution:**  
Manually reconfigure all required providers after migration.

---

#### Stream Title Sync Is Not Working

**Cause:**  
Since providers are not migrated, the stream title sync feature will not function properly. The UI may show the "sync'd" icon, but there is no active provider to sync to.

**Resolution:**  
After configuring your providers, edit the streams and re-sync them to the relevant provider. This will restore proper title syncing.

---

### Summary

Migration transfers core application data only.  
Environment-specific configuration, providers, and API keys must be manually reconfigured after migration.

---
