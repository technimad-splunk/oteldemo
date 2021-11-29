Purpose:
Demonstrate how to use the splunk otel collector to collect performance metrics from postgres and send them to splunk eterprise.

Solution:
This demo runs a postgres database, a splunk otel collector and splunk.
Splunk can be reached via http://localhost:18000 user: admin pass: opentelemetry
Default postgres metrics are sent to splunk enterprise, via HEC.
One extra metric (postgres_conflicts) is configured, to show how to add more, specific metrics.
List of supported metrics is available at: https://docs.splunk.com/Observability/gdi/postgresql/postgresql.html#postgresql
masterDBName in postgresconfig is needed to get the data cllector to function correctly.

Resources:
Postgres docker config: https://hub.docker.com/_/postgres/

