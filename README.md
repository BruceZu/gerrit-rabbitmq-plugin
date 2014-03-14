gerrit-rabbitmq-plugin: Gerrit event publish plugin via RabbitMQ
=======================

* Author: rinrinne a.k.a. rin_ne
* Repository: http://github.com/rinrinne/gerrit-rabbitmq-plugin

[![Build Status](https://travis-ci.org/rinrinne/gerrit-rabbitmq-plugin.png?branch=master)](https://travis-ci.org/rinrinne/gerrit-rabbitmq-plugin)

Synopsis
----------------------

This is Gerrit plugin.

This can publish gerrit events to message queue provided by RabbitMQ.
Published events are the same as Gerrit stream evnets.

This plugin works on Gerrit 2.8 or later.

About Buck
---------------------

[Buck] is a build system now gerrit adopt. If you want to use Buck,
you need to setup it referring [Building with Buck] in gerrit documentation.

[Buck]: http://facebook.github.io/buck/
[Building with Buck]: https://gerrit-documentation.storage.googleapis.com/Documentation/2.8.2/dev-buck.html


Environments
---------------------

* `linux`
  * `java-1.7`
    * `maven-3.0.4`
    * `buck`

Build
---------------------

* Using `maven`

    mvn package

* Using `buck`

    git clone git clone https://gerrit.googlesource.com/gerrit
    ln -s $(pwd) gerrit/plugins/rabbitmq
    cd gerrit
    buck build plugins/rabbitmq:rabbitmq

Using another version API
--------------------------

* For `maven`

Now avaliable for Gerrit 2.8.1 only. If you want to use it on another version of Gerrit, please try the below.

    mvn package -DGerrit-ApiVersion=2.8

* for `buck`

After clone gerrit, you can checkout specified version.

    git checkout -b v2.8 refs/tags/v2.8

Reference
---------------------

* [Configuration]
* [Message Format]

[Configuration]: https://github.com/rinrinne/gerrit-rabbitmq-plugin/blob/master/src/main/resources/Documentation/config.md
[Message Format]: https://github.com/rinrinne/gerrit-rabbitmq-plugin/blob/master/src/main/resources/Documentation/message.md

Minimum Configuration
---------------------

```
  [amqp]
    uri = amqp://localhost
  [exchange]
    name = exchange-for-gerrit-queue
  [message]
    routingKey = com.foobar.www.gerrit
  [gerrit]
    name = foobar-gerrit
    hostname = www.foobar.com
```

History
---------------------

* 1.3
  * Build with Buck

* 1.2
  * Fix repository location for gerrit-api
  * Update README

* 1.1
  * Fix channel handling
  * Add property: `monitor.failureCount`
  * Update README and documents 

* 1.0
  *  First release

License
---------------------

The Apache Software License, Version 2.0

Copyright
---------------------

Copyright (c) 2013 rinrinne a.k.a. rin_ne
