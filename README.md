![Build](https://github.com/dattack/parent/actions/workflows/maven-deploy.yml/badge.svg?branch=dev)
[![license](https://img.shields.io/:license-Apache-blue.svg?style=plastic-square)](LICENSE.md)
[![Maven Central](https://img.shields.io/maven-central/v/com.dattack/parent.svg?label=Maven%20Central)](https://search.maven.org/artifact/com.dattack/parent)

# Parent POM

The _parent_ project provides common Maven settings used by Dattack projects. This mainly involves the versioning and
configuration of Maven plugins as well as the structure of the projects and the infrastructure used.

## Usage

This project is hosted into The Central Repository, so all you need to do to use it in a maven project is set the 
parent in your `pom.xml` file:

```xml
<parent>
    <groupId>com.dattack</groupId>
    <artifactId>parent</artifactId>
    <version>8-SNAPSHOT</version>
</parent>
```

The source code on the main branch is the current state of development; it is not
recommended for general use. If you prefer to build from source, please use an appropriate
release tag.

## Contributing

Pull requests and stars are always welcome. For bugs and feature
requests, [please create an issue](https://github.com/dattack/parent/issues).

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

If you have other questions, please contact by [email](mailto:dev@dattack.com) or
[@dattackteam](https://twitter.com/dattackteam)

## License

Code is under the [Apache Licence v2](https://www.apache.org/licenses/LICENSE-2.0.txt).
