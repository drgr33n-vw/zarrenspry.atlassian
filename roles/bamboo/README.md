# Bamboo DataCenter

Ansible role that provisions a Bamboo DataCenter instance.

This role is still in the early development stages and might not work as 
expected. Please report any issues, and I'll get onto them ASAP.

# Requirements
This service requires that postgresql is installed and running. I'm working on
a simple installer collection and will add it to the dependency list once 
complete.

## Variables

| Name | Description | Default |
| ---- | ------------| --------|
| bamboo_license_string | Bamboo License string | BLANK |
| bamboo_version | Bamboo version to install | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>major</td><td>Bamboo major version.</td><td>1</td></tr><tr><td>minor</td><td>Bamboo minor version.</td><td>2</td></tr><tr><td>patch</td><td>Bamboo patch version.</td><td>4</td></tr></tbody></table> |
| bamboo_system_user | Bamboo system user | bamboo |
| bamboo_installation_directory | Bamboo installation directory path | /opt/bamboo |
| bamboo_database.bamboo | Bamboo database configuration parameters | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>host</td><td>Postgres host address.</td><td>127.0.0.1</td></tr><tr><td>port</td><td>Postgres listening port.</td><td>5432</td></tr><tr><td>name</td><td>The name of the target database.</td><td>bamboo</td></tr><tr><td>owner</td><td>The owner of the target database.</td><td>bamboo</td></tr><tr><td>username</td><td>The username used to connect to the target database.</td><td>bamboo</td></tr><tr><td>password</td><td>The password used to connect to the target database.</td><td>password</td></tr><tr><td>enabled</td><td>Set postgresql database enabled.</td><td>enabled</td></tr></tbody></table> |
| bamboo_locale | Locale to use within the Bamboo installation | en_GB.UTF-8 |
| bamboo_webapp_context_path | Webapp context path | / |
| bamboo_java_heap_size | Java heap size | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>init</td><td>Initial heap size.</td><td>256</td></tr><tr><td>max</td><td>Max heap size.</td><td>512</td></tr></tbody></table> |
| bamboo_jmxremote | JMX Remote configuration. | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>enabled</td><td>Set Remote JMX enabled.</td><td>false</td></tr><tr><td>port</td><td>Set Remote JMX listening port.</td><td>4242</td></tr><tr><td>authenticate</td><td>Set JMX password authentication.</td><td>true</td></tr><tr><td>ssl</td><td>Enable SSL for JMX connections.</td><td>false</td></tr><tr><td>password_file</td><td>Full path to JMX password file.</td><td>conf/jmxremote.password</td></tr><tr><td>mbean_name</td><td>JMX management bean name.</td><td>wrapper:type=Java Service Wrapper Control</td></tr></tbody></table> |
| bamboo_logging_console | Bamboo console logging configuration. | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>format</td><td>Logging format</td><td>PM</td></tr><tr><td>loglevel</td><td>Console logging level.</td><td>INFO</td></tr></tbody></table> |
| bamboo_logging_logfile | Bamboo logfile configuration. | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>name</td><td>Full path and name of logfile</td><td>../logs/bamboo.log</td></tr><tr><td>format</td><td>Logging format.</td><td>LPTM</td></tr><tr><td>loglevel</td><td>Logging level.</td><td>INFO</td></tr><tr><td>maxsize</td><td>Log file max size.</td><td>10m</td></tr><tr><td>maxfiles</td><td>Max amount of logfiles to retain.</td><td>10</td></tr></tbody></table> |
| bamboo_logging_syslog | Bamboo syslog logging configuration. | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>loglevel</td><td>Logging level.</td><td>INFO</td></tr></tbody></table> |
| bamboo_console_title | Title to use when running as a console | Bamboo |
| temurin_version | Temurin (AdoptOpenJDK) Version | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>major</td><td>Temurin major version.</td><td>11</td></tr><tr><td>minor</td><td>Temurin minor version.</td><td>0</td></tr><tr><td>patch</td><td>Temurin patch version.</td><td>13</td></tr><tr><td>patch</td><td>Temurin build number.</td><td>8</td></tr></tbody></table> |
| postgres_java_version | Postgresql JDBC Driver version | <table><thead><tr><th>Name</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>major</td><td>Postgresql JDBC driver major version.</td><td>42</td></tr><tr><td>minor</td><td>Postgresql JDBC driver  minor version.</td><td>3</td></tr><tr><td>patch</td><td>Postgresql JDBC driver patch version.</td><td>1</td></tr></tbody></table> |
