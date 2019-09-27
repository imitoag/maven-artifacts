### What is this?

This is a repository holding some Maven dependencies that are used in the development process, but are no longer available in the public Maven repositories.

### How to add new artifacts?

* find the JAR that needs to be added
* create a pom file:

```
$ mvn org.apache.maven.plugins:maven-install-plugin:3.0.0-M1:install-file -Dfile=path-to-file-1.2.3.jar -DgroupId=<groupId> -DartifactId=<artifactId> -Dversion=<version> -Dpackaging=jar -DgeneratePom=true -DcreateChecksum=true
```

* copy it from your local maven repository (with the directory structure) from your local maven repository (usually ~/.m2/repository)
* add it to this repo with appropriate comment

```
$ cp ~/.m2/repository/<groupId>/<artifactId>/* ./<groupId>/<artifactId>/
git add -A
git commit -m "Add library X"
```

### Using this repository

Add those lines to the pom.xml:

```
<repositories>
    <repository>
        <id>mvn-repo</id>
        <url>https://raw.githubusercontent.com/imitoag/maven-artifacts/master</url>
        <releases>
            <enabled>true</enabled>
        </releases>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </repository>
</repositories>
```