# Datastax Java Driver for Apache Cassandra®

[![Build Status](https://travis-ci.org/datastax/java-driver.svg?branch=3.x)](https://travis-ci.org/datastax/java-driver)

*If you're reading this on github.com, please note that this is the readme
for the development version and that some features described here might
not yet have been released. You can find the documentation for the latest
version through the [Java driver
docs](http://docs.datastax.com/en/developer/java-driver/latest/index.html) or via the release tags,
[e.g.
3.5.1](https://github.com/datastax/java-driver/tree/3.5.1).*

_**Feeback requested!** Help us focus our efforts, provide your input on 
the [Platform and Runtime Survey](http://goo.gl/forms/qwUE6qnL7U) (we kept it short)._

A modern, [feature-rich](manual/) and highly tunable Java client
library for Apache Cassandra (2.1+) and using exclusively Cassandra's binary protocol 
and Cassandra Query Language v3. _Use the [DataStax Enterprise Java driver][dse-driver]
for better compatibility and support for DataStax Enterprise._

**Features:**

* [Sync](manual/) and [Async](manual/async/) API
* [Simple](manual/statements/simple/), [Prepared](manual/statements/prepared/), and [Batch](manual/statements/batch/)
  statements
* Asynchronous IO, parallel execution, request pipelining
* [Connection pooling](manual/pooling/)
* Auto node discovery
* Automatic reconnection
* Configurable [load balancing](manual/load_balancing/) and [retry policies](manual/retries/)
* Works with any cluster size
* [Query builder](manual/statements/built/)
* [Object mapper](manual/object_mapper/)

The driver architecture is based on layers. At the bottom lies the driver core.
This core handles everything related to the connections to a Cassandra
cluster (for example, connection pool, discovering new nodes, etc.) and exposes a simple,
relatively low-level API on top of which higher level layers can be built.

The driver contains the following modules:

- driver-core: the core layer.
- driver-mapping: the object mapper.
- driver-extras: optional features for the Java driver.
- driver-examples: example applications using the other modules which are
  only meant for demonstration purposes.
- driver-tests: tests for the java-driver.

**Useful links:**

- JIRA (bug tracking): https://datastax-oss.atlassian.net/browse/JAVA
- MAILING LIST: https://groups.google.com/a/lists.datastax.com/forum/#!forum/java-driver-user
- DATASTAX ACADEMY SLACK: #datastax-drivers on https://academy.datastax.com/slack 
- TWITTER: [@dsJavaDriver](https://twitter.com/dsJavaDriver) tweets Java
  driver releases and important announcements (low frequency).
  [@DataStaxEng](https://twitter.com/datastaxeng) has more news including
  other drivers, Cassandra, and DSE.
- DOCS: the [manual](http://docs.datastax.com/en/developer/java-driver/3.5/manual/) has quick
  start material and technical details about the driver and its features.
- API: http://www.datastax.com/drivers/java/3.5
- GITHUB REPOSITORY: https://github.com/datastax/java-driver
- [changelog](changelog/)
- [binary tarball](http://downloads.datastax.com/java-driver/cassandra-java-driver-3.5.1.tar.gz)

## Getting the driver

The last release of the driver is available on Maven Central. You can install
it in your application using the following Maven dependency (_if
using DataStax Enterprise, install the [DataStax Enterprise Java driver][dse-driver] instead_):

```xml
<dependency>
  <groupId>com.datastax.cassandra</groupId>
  <artifactId>cassandra-driver-core</artifactId>
  <version>3.5.1</version>
</dependency>
```

Note that the object mapper is published as a separate artifact:

```xml
<dependency>
  <groupId>com.datastax.cassandra</groupId>
  <artifactId>cassandra-driver-mapping</artifactId>
  <version>3.5.1</version>
</dependency>
```

The 'extras' module is also published as a separate artifact:

```xml
<dependency>
  <groupId>com.datastax.cassandra</groupId>
  <artifactId>cassandra-driver-extras</artifactId>
  <version>3.5.1</version>
</dependency>
```


We also provide a [shaded JAR](manual/shaded_jar/)
to avoid the explicit dependency to Netty.

If you can't use a dependency management tool, a
[binary tarball](http://downloads.datastax.com/java-driver/cassandra-java-driver-3.5.1.tar.gz)
is available for download.

## Compatibility

The Java client driver 3.5.1 ([branch 3.x](https://github.com/datastax/java-driver/tree/3.x)) is compatible with Apache
Cassandra 2.1, 2.2 and 3.0+ (see [this page](http://docs.datastax.com/en/developer/java-driver/latest/manual/native_protocol/) for
the most up-to-date compatibility information).

UDT and tuple support is available only when using Apache Cassandra 2.1 or higher (see [CQL improvements in Cassandra 2.1](http://www.datastax.com/dev/blog/cql-in-2-1)).

Other features are available only when using Apache Cassandra 2.0 or higher (e.g. result set paging,
[BatchStatement](https://github.com/datastax/java-driver/blob/3.x/driver-core/src/main/java/com/datastax/driver/core/BatchStatement.java),
[lightweight transactions](http://www.datastax.com/documentation/cql/3.1/cql/cql_using/use_ltweight_transaction_t.html) 
-- see [What's new in Cassandra 2.0](http://www.datastax.com/documentation/cassandra/2.0/cassandra/features/features_key_c.html)). 
Trying to use these with a cluster running Cassandra 1.2 will result in 
an [UnsupportedFeatureException](https://github.com/datastax/java-driver/blob/3.x/driver-core/src/main/java/com/datastax/driver/core/exceptions/UnsupportedFeatureException.java) being thrown.

The java driver supports Java JDK versions 6 and above.

If using _DataStax Enterprise_, the [DataStax Enterprise Java driver][dse-driver] provides 
more features and better compatibility.

__Disclaimer__: Some _DataStax/DataStax Enterprise_ products might partially work on 
big-endian systems, but _DataStax_ does not officially support these systems.

## Upgrading from previous versions

If you are upgrading from a previous version of the driver, be sure to have a look at
the [upgrade guide](/upgrade_guide/).

If you are upgrading to _DataStax Enterprise_, use the [DataStax Enterprise Java driver][dse-driver] for more
features and better compatibility.

## License
Copyright 2012-2018, DataStax

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

[dse-driver]: http://docs.datastax.com/en/developer/java-driver-dse/latest
