---
title: Logback Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_logback.html
folder: mydoc
toc: false
---

[Logback](http://logback.qos.ch/) configuration reload.

#### Implementation notes:
Plugin hooks into `ch.qos.logback.core.joran.GenericConfigurator.doConfigure(URL)` call. All configuration URL's are
registered and watched for change. After the file change, full reconfiguration via the same method is executed.

## TODO:
* The plugin registers directly to the file URL. This is usually `target/classes/logback.xml`. If used together
with `watchResources` property in hotswap-agent.properties, the change may be only in
`src/main/resources/logback.xml` and hence not triggered. Usually this is solved by IDE's copy resources on save
feature.
