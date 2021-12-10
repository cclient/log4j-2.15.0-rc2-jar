# log4j-2.15.0-rc2-jar

[Release log4j-2.15.0-rc2 · apache/logging-log4j2 (github.com)](https://github.com/apache/logging-log4j2/releases/tag/log4j-2.15.0-rc2)

build jar by docker openjdk11

```bash
## source code
wget https://github.com/apache/logging-log4j2/archive/refs/tags/log4j-2.15.0-rc2.tar.gz
tar -zxf log4j-2.15.0-rc2.tar.gz
cp pom.xml logging-log4j2-log4j-2.15.0-rc2/pom.xml
rm logging-log4j2-log4j-2.15.0-rc2/log4j-api/src/test/java/org/apache/logging/log4j/util/StackLocatorUtilTest.java

## docker build
docker run -d --name mvn11 -v ${PWD}/toolchains.xml:/root/.m2/toolchains.xml -v ${PWD}/logging-log4j2-log4j-2.15.0-rc2:/tmp/logging-log4j2-log4j-2.15.0-rc2  maven:3.8-openjdk-11-slim tail -f /dev/null 
docker exec -it mvn11 bash
cd /tmp/logging-log4j2-log4j-2.15.0-rc2/
mvn package -DskipTests=true

### jar
root@8b60f3863aaf:/# md5sum /tmp/logging-log4j2-log4j-2.15.0-rc2/log4j-core/target/log4j-core-2.15.0.jar
1322cc8f2f8f919265c628fb60bc790d  /tmp/logging-log4j2-log4j-2.15.0-rc2/log4j-core/target/log4j-core-2.15.0.jar
root@8b60f3863aaf:/# md5sum /tmp/logging-log4j2-log4j-2.15.0-rc2/log4j-api/target/log4j-api-2.15.0.jar
e820bc3af209205d770e978e412fdb61  /tmp/logging-log4j2-log4j-2.15.0-rc2/log4j-api/target/log4j-api-2.15.0.jar

```

package log
```bash
[INFO] --- maven-site-plugin:3.8.2:attach-descriptor (attach-descriptor) @ log4j-slf4j18-impl ---
[INFO] Skipping because packaging 'jar' is not pom.
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for Apache Log4j 2 2.15.0:
[INFO]
[INFO] Apache Log4j 2 ..................................... SUCCESS [  1.492 s]
[INFO] Apache Log4j API Java 9 support .................... SUCCESS [  3.314 s]
[INFO] Apache Log4j API ................................... SUCCESS [ 10.589 s]
[INFO] Apache Log4j Implementation Java 9 support ......... SUCCESS [  1.364 s]
[INFO] Apache Log4j Core .................................. SUCCESS [ 21.850 s]
[INFO] Apache Log4j Core Integration Tests ................ SUCCESS [  3.240 s]
[INFO] Apache Log4j 1.x Compatibility API ................. SUCCESS [  5.063 s]
[INFO] Apache Log4j to SLF4J Adapter ...................... SUCCESS [  2.431 s]
[INFO] Apache Log4j SLF4J Binding ......................... SUCCESS [  2.638 s]
[INFO] Apache Log4j SLF4J 1.8+ Binding .................... SUCCESS [  2.527 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  55.575 s
[INFO] Finished at: 2021-12-10T14:51:17Z
[INFO] ------------------------------------------------------------------------
```

