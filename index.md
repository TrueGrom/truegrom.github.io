---
layout: default
---

## FdKit — Android Fast Development Kit

[![Maven Central](https://img.shields.io/maven-central/v/io.github.truegrom/bom?label=release)](https://central.sonatype.com/artifact/io.github.truegrom/bom)
![Snapshot](https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Fcentral.sonatype.com%2Frepository%2Fmaven-snapshots%2Fio%2Fgithub%2Ftruegrom%2Fbom%2Fmaven-metadata.xml&label=snapshot)

Modular Android SDK with state, networking, logging, and slot-based Compose UI.

Example — declare the BOM once, then add only the modules you need:

```kotlin
dependencies {
    implementation(platform("io.github.truegrom:bom:<version>"))

    implementation("io.github.truegrom:utils")       // Result/Either/Value, coroutine helpers
    implementation("io.github.truegrom:state")       // StateViewModel, RemoteData, traits, errors
    implementation("io.github.truegrom:viewmodel")   // BaseViewModel (task/uniqueTask)
    implementation("io.github.truegrom:repository")  // BaseRepository, BaseDispatchers
    implementation("io.github.truegrom:logging")     // FdkLog, LogSink, Timber backend
    implementation("io.github.truegrom:http-error")  // HttpError hierarchy, HttpErrorMapper
    implementation("io.github.truegrom:network")     // Ktor HttpClient (@BaseHttp)
    implementation("io.github.truegrom:crypto")      // CryptoManager (Tink + Keystore)
    implementation("io.github.truegrom:datetime")    // java.time format extensions
    implementation("io.github.truegrom:ui-kit")      // Compose primitives, localized formatters
    implementation("io.github.truegrom:screen")      // FdKit* screen scaffolding
}
```

- [All artifacts on Maven Central](https://central.sonatype.com/namespace/io.github.truegrom)
- [BOM](https://central.sonatype.com/artifact/io.github.truegrom/bom)
- [Using FdKit — Agent Skill]({{ "/fdkit-agent-skill.html" | relative_url }}) — guide for AI coding agents
