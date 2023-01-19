# Splunk Otel collector metrics example
Demonstrate how to use the splunk otel collector to collect metrics data using various methods and sent them to Splunk Enterprise via HEC.

## Summary / how to use
This demo runs a postgres database, prometheus sources, collectd senders, a splunk otel collector and splunk.

You can start this demo with ```docker-compose up```.

Splunk can be reached via 
```
url: http://localhost:18000  
user: admin 
pass: opentelemetry
```

Metrics are sent to splunk enterprise, via HEC.

Exmaple dashboards for splunk can be found in the directory ```dashboards```.

## Data collection
Data is collected in various ways:
- direct connection to postgresql
- collectd network protocol receiver
- prometheus scraping

## Data generation
### Postgres
Empty database in docker container
Default postgres metrics are sent to splunk enterprise, via HEC.
One extra metric (postgres_conflicts) is configured, to show how to add more, specific metrics.
List of supported metrics is available at: https://docs.splunk.com/Observability/gdi/postgresql/postgresql.html#postgresql
masterDBName in postgresconfig is needed to get the data collector to function correctly.

### Collectd
Container with just collectd installed, and the config file collectd.d/generator.conf
### Prometheus
Use a container with a minimal go program which exports internal go metrics based on https://github.com/esakat/prometheus-exporter-sample

## Data export
All collected metrics are sent to Splunk via HEC.
We use two HEC endpoints:
- all metrics collected via the opentelemetry collector
- all internal metrics from the opentelemetry collector

## External Documentation consulted:

Otel config Configurator:
https://bossofopsando11y.com/configurator/standalone  
Logging exporter:
https://github.com/open-telemetry/opentelemetry-collector/tree/main/exporter/loggingexporter  
Recievers, Processors and Exporters included in Splunk open telemetry collector:
https://github.com/signalfx/splunk-otel-collector/blob/main/go.mod  
Splunk HEC exporter documentation
https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/exporter/splunkhecexporter  
Postgres receiver
https://docs.splunk.com/observability/gdi/postgresql/postgresql.html#postgresql  
Postgres docker config
https://hub.docker.com/_/postgres/  
Example configuration metrics transform processor:
https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/processor/metricstransformprocessor/testdata/config_full.yaml  
Collectd network configuration:
https://collectd.org/wiki/index.php/Plugin:Network  
Collectd receiver configuration:
https://docs.splunk.com/observability/gdi/collectd/collectd.html#nav-Collectd-plugin  
Prometheus receiver:
https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/receiver/prometheusreceiver  
OpenTelemetry Collector filestorage extension:
https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/extension/storage/filestorage  
OpenTelemetry Collector exporterhelper: 
https://github.com/open-telemetry/opentelemetry-collector/tree/main/exporter/exporterhelper  

