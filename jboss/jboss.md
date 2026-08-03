# Jboss
## Common Commands

**Connect to jboss**

```bash
./jboss-cli.sh --connect
```

**Deploy a war file**

```bash
deploy /home/thirumal/jboss/standalone/deployments/demo.war
```
If it's failed & want to `force` with new war

```bash
deploy /home/thirumal/jboss/standalone/deployments/demo.war --force
```

**Redeploy**

```bash
 /deployment=demo.war:redeploy
```


**Remove a context root**

```bash
deploy --undeploy demo.war
```

**List all deployed wars**

```bash
ls $JBOSS_HOME/standalone/deployments | grep -i .war
```

**List all undeployed wars**

```bash
ls $JBOSS_HOME/standalone/deployments | grep -i .war.undeployed
```

**CPU Usage**

```bash
ps aux | grep jboss
```

**Find process id of jboss**

```bash
ps -ef | grep jboss
```

**Kill the process**

```bash
kill -9 $(ps -ef | grep jboss | awk '{print $2}')
```
**Check jboss port 8080 used by which process**

```bash
ps aux | grep 8080
```
## Create jboss user

Check the java version

```bash
java -version

or 

echo $JAVA_HOME
```

## Create jboss user

```bash
./add-user.sh -a
```
Access the console using the URL [http://localhost:9990](http://localhost:9990)
