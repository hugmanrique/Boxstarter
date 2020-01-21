# Setting up Java

The `wslScripts/installApps.sh` script installs the OpenJDK, but we still need to manually set the `JAVA_HOME` env variable.

First, open `~/.bashrc`. Then, add the following at the end of file:

```bash
export JAVA_HOME=/usr/lib/jvm/open-jdk
```

Save your changes and run `source ~/.bashrc`. Check the `JAVA_HOME` env variable has been set correctly by running `echo $JAVA_HOME`.

## Shared Maven local repository

Maven local repository defaults to `~/.m2/repository` on Linux, and `%USER_PROFILE%/.m2/repository` on Windows. In order to reduce duplicated dependencies and speed up future builds, open `~/.m2/settings.xml` on Linux and add the following config:

```xml
<localRepository>/mnt/d/Users/Hugo/.m2/repository</localRepository>
```

_(See [http://maven.apache.org/settings.html] for a default `settings.xml` file)_

Maven will now save all the locally cached dependencies to `%USER_PROFILE/.m2/repository` independently of the running OS.