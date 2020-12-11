---
title: "Configuration"
date: "2020-12-11T10:57:27+0000"
weight: 20
geekdocRepo: https://github.com/owncloud/ocis
geekdocEditPath: edit/master/store/templates
geekdocFilePath: CONFIGURATION.tmpl
---

{{< toc >}}

## Configuration

### Configuration using config files

Out of the box extensions will attempt to read configuration details from:

```console
/etc/ocis
$HOME/.ocis
./config
```

For this configuration to be picked up, have a look at your extension `root` command and look for which default config name it has assigned. *i.e: ocis-proxy reads `proxy.json | yaml | toml ...`*.

So far we support the file formats `JSON` and `YAML`, if you want to get a full example configuration just take a look at [our repository](https://github.com/owncloud/ocis/tree/master/config), there you can always see the latest configuration format. These example configurations include all available options and the default values. The configuration file will be automatically loaded if it's placed at `/etc/ocis/ocis.yml`, `${HOME}/.ocis/ocis.yml` or `$(pwd)/config/ocis.yml`.

### Environment variables

If you prefer to configure the service with environment variables you can see the available variables below.

### Commandline flags

If you prefer to configure the service with commandline flags you can see the available variables below. Command line flags are only working when calling the subcommand directly.

### store server

Start integrated server

Usage: `store server [command options] [arguments...]`

--tracing-enabled | $STORE_TRACING_ENABLED  
: Enable sending traces.

--tracing-type | $STORE_TRACING_TYPE  
: Tracing backend type. Default: `jaeger`.

--tracing-endpoint | $STORE_TRACING_ENDPOINT  
: Endpoint for the agent.

--tracing-collector | $STORE_TRACING_COLLECTOR  
: Endpoint for the collector.

--tracing-service | $STORE_TRACING_SERVICE  
: Service name for tracing. Default: `store`.

--debug-addr | $STORE_DEBUG_ADDR  
: Address to bind debug server. Default: `0.0.0.0:9460`.

--debug-token | $STORE_DEBUG_TOKEN  
: Token to grant metrics access.

--debug-pprof | $STORE_DEBUG_PPROF  
: Enable pprof debugging.

--debug-zpages | $STORE_DEBUG_ZPAGES  
: Enable zpages debugging.

--grpc-namespace | $STORE_GRPC_NAMESPACE  
: Set the base namespace for the grpc namespace. Default: `com.owncloud.api`.

--name | $STORE_NAME  
: Service name. Default: `store`.

--data-path | $STORE_DATA_PATH  
: location of the store data path. Default: `/var/tmp/ocis-store`.

### store ocis-store

Service to store values for ocis extensions

Usage: `store ocis-store [command options] [arguments...]`

--config-file | $STORE_CONFIG_FILE  
: Path to config file.

--log-level | $STORE_LOG_LEVEL  
: Set logging level. Default: `info`.

--log-pretty | $STORE_LOG_PRETTY  
: Enable pretty logging. Default: `true`.

--log-color | $STORE_LOG_COLOR  
: Enable colored logging. Default: `true`.

### store version

Print the versions of the running instances

Usage: `store version [command options] [arguments...]`

--grpc-namespace | $STORE_GRPC_NAMESPACE  
: Set the base namespace for the grpc namespace. Default: `com.owncloud.api`.

--name | $STORE_NAME  
: Service name. Default: `store`.

### store health

Check health status

Usage: `store health [command options] [arguments...]`

--debug-addr | $STORE_DEBUG_ADDR  
: Address to debug endpoint. Default: `0.0.0.0:9460`.
