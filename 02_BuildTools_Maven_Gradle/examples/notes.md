# 02_BuildTools_Maven_Gradle Notes

Maven is a Java build automation & dependency management tool.

Key Concepts:
POM.xml (Project Object Model)

The heart of Maven project.

Defines dependencies, plugins, build lifecycle, etc.
Example:

xml
Copy
Edit
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>myapp</artifactId>
  <version>1.0.0</version>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
Maven Lifecycle
Maven defines a standard set of build phases:

validate → check project is correct

compile → compile source code

test → run unit tests

package → package compiled code into JAR/WAR

verify → run integration tests

install → copy to local repository

deploy → push to remote repo (e.g., Nexus, Artifactory)

👉 Example:

bash
Copy
Edit
mvn clean install
Runs clean (delete old build) + install (package + copy artifact to local repo).

Dependency Management
Maven downloads dependencies from Maven Central or private repos (like Nexus).

Local repo: ~/.m2/repository

Remote repo: Maven Central or your company Nexus

If a dependency is not found locally, Maven downloads it → caches for next builds.

Plugins
Extend Maven functionality. Common ones:

maven-compiler-plugin → compiles Java code

maven-surefire-plugin → runs unit tests

maven-assembly-plugin → creates distributions (ZIP/TAR)

maven-deploy-plugin → deploys artifacts to repo

Example:

xml
Copy
Edit
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.8.1</version>
      <configuration>
        <source>1.8</source>
        <target>1.8</target>
      </configuration>
    </plugin>
  </plugins>
</build>
🔹 Common Maven Commands
Command	Purpose
mvn clean	Deletes target folder (old build files).
mvn compile	Compiles source code.
mvn test	Runs unit tests.
mvn package	Creates JAR/WAR.
mvn install	Puts artifact in local repo.
mvn deploy	Pushes artifact to Nexus/Artifactory.
mvn dependency:tree	Shows dependency hierarchy.

🔹 Maven in CI/CD
In Bamboo, you add a build task like:

Executable: Maven 3.x

Goal: clean install

Bamboo picks pom.xml → runs build.

Output artifact (JAR/WAR) → uploaded to Nexus.

Next stage (like XLD deployment) picks artifact.
