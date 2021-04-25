# Parent POM

[![license](https://img.shields.io/:license-Apache-blue.svg?style=plastic-square)](LICENSE.md)

The _parent-POM_ provides common settings for all Dattack's projects. _parent-POM_ is hosted into The Central Repository, so all you need to do to
use it in a maven project is set the parent:

```xml
    <parent>
        <groupId>com.dattack</groupId>
        <artifactId>parent</artifactId>
        <version>${dattack.parent.version}</version>
    </parent>
```

## Contributing

Pull requests and stars are always welcome.
For bugs and feature requests, [please create an issue](https://github.com/dattack/parent/issues).

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

Code is under the [Apache Licence v2](https://www.apache.org/licenses/LICENSE-2.0.txt).
