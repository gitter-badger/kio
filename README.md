![Kio logo](docs/assets/images/logos/kio_small_logo.png)  
<small><sub><sup>Icon made by [Flat Icons](https://www.flaticon.com/authors/flat-icons) from [www.flaticon.com](http://www.flaticon.com/) </sup></sub></small>

---

**Kio** is a set of Kotlin extensions for [Apache Beam](https://beam.apache.org) to implement fluent-like API for Java SDK.

## Quick Start

```kotlin
// Create Kio context
val kio = Kio.fromArguments(args)

// Configure a pipeline
kio.read().text("~/input.txt")
    .map { it.toLowerCase() }
    .flatMap { it.split("\\W+".toRegex()) }
    .filter { it.isNotEmpty() }
    .countByValue()
    .forEach { println(it) }

// And execute it
kio.execute().waitUntilDone()
```

## Documentation

For more information about Kio, please see the documentation in the `docs` directory or here: [https://code.chermenin.ru/kio](https://code.chermenin.ru/kio).

## License

Copyright © 2020 Alex Chermenin

Licensed under the Apache License, Version 2.0: [https://www.apache.org/licenses/LICENSE-2.0.txt](https://www.apache.org/licenses/LICENSE-2.0.txt)