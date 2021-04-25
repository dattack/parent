# Parent POM [![license](https://img.shields.io/:license-Apache-blue.svg?style=plastic-square)](LICENSE.md)

The _parent-POM_ provides common settings for all Dattack's projects.

Try it out
=========

_parent-POM_ is hosted into The Central Repository, so all you need to do to
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

[license]:LICENSE
[license img]:https://img.shields.io/:license-Apache-blue.svg?style=plastic-square
