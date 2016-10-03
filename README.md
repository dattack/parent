[![][travis img]][travis]
[![][license img]][license]

Parent POM
==========

The _parent-POM_ provides common settings for all Dattack's projects.

Where can i get the latest release?
=========

You can pull it from the Dattack repository:

```xml
  <repositories>
    <repository>
      <id>public-dattack-releases</id>
      <name>Dattack Releases</name>
      <url>http://maven.dattack.com/release</url>
      <releases>
        <updatePolicy>never</updatePolicy>
        <checksumPolicy>fail</checksumPolicy>
      </releases>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
    </repository>
    <repository>
      <id>public-dattack-snapshots</id>
      <name>Dattack Snapshots</name>
      <url>http://maven.dattack.com/snapshot</url>
      <releases>
        <enabled>false</enabled>
      </releases>
      <snapshots>
        <updatePolicy>always</updatePolicy>
        <checksumPolicy>warn</checksumPolicy>
      </snapshots>
    </repository>
  </repositories>
```

Try it out
=========

_parent-POM_ is hosted into Dattack maven repository, so all you need to do to
use it in a maven project is set the parent:


```xml
    <parent>
        <groupId>com.dattack</groupId>
        <artifactId>parent</artifactId>
        <version>${dattack.parent.version}</version>
    </parent>
```

License
-------
Code is under the [Apache Licence v2](https://www.apache.org/licenses/LICENSE-2.0.txt).

[travis]:https://travis-ci.org/dattack/parent/builds
[travis img]:https://secure.travis-ci.org/dattack/parent.svg?branch=master

[license]:LICENSE
[license img]:https://img.shields.io/:license-Apache-blue.svg?style=plastic-square
