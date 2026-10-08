# Credential Store

Open your terminal, navigate to your JBoss bin directory and start the 

JBoss CLI:

```bash
jboss-cli.sh --connect
```

Once connected, run these two commands to create a `secure store` and `save your password`:

jboss-cli

# 1. Create a credential store (this creates an encrypted file on disk)

```bash
/subsystem=elytron/credential-store=db-cred-store:add(relative-to=jboss.home.dir, location=credstore/db-cred-store.cs, create=true, credential-reference={clear-text="Thirumal"})
```

This command tells JBoss to create a highly secure, encrypted file on your hard drive (a "credential store") where it can safely hold all your application passwords.

* `/subsystem=elytron/credential-store=db-cred-store` This is the "path". It tells JBoss that you are modifying the `Elytron` security subsystem, and you want to manage a credential store which you are naming `db-cred-store`.

  
* `:add(...)` This is the action. It tells JBoss to add (create) this new credential store.

  
`relative-to=jboss.home.dir` This tells JBoss where to save the encrypted file. `jboss.home.dir` is an internal JBoss variable that normally points to the `JBOSS_HOME/` folder.

  
`location=credstore/db-cred-store.cs` This is the actual name of the file it will create. Combined with the step above, JBoss will create a file located at `{JBOSS_HOME}\jboss-eap-8.1\credstore\db-cred-store.cs`.

  
`create=true` This tells JBoss to generate the physical `.cs` file on the disk if it doesn't already exist.

  
`clear-text="Thirumal"` Think of this as the master password for a password manager. This is not your database password; it is the password used to encrypt and lock the `db-cred-store.cs` file itself.

# 2. Add your actual database password to it under an alias (e.g., "db-password")

```bash
/subsystem=elytron/credential-store=db-cred-store:add-alias(alias=db-password, secret-value="Thirumal")
```

Step 2: Update `standalone.xml` to use the Credential Store

Now that your password is encrypted and stored safely by JBoss, you can remove the plain text password from your `standalone.xml`

Instead, update your datasources to reference the secure alias. Change this:

```xml
<security user-name="${db.user}" password="${db.password}"/>
```

To this:

```xml
<security user-name="${db.user}">
    <credential-reference store="db-cred-store" alias="db-password"/>
</security>
```