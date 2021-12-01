# Bamboo DataCenter

Ansible role that provisions a Bamboo DataCenter install based on the official
Docker project from Atlassian.

This role is still in the early development stages and might not work as 
expected. Please report any issues, and I'll get onto them ASAP.

# Requirements

This service requires that postgresql is installed and running. I'm working on
a simple installer collection and will add it to the dependency list once 
complete.

## Variables

### Tomcat and Reverse Proxy Setting
#### bamboo_tomcat_proxy_name 
- Default: ""
- Description: The reverse proxy's fully qualified hostname. 
#### bamboo_tomcat_proxy_port
- Default: ""
- Description: The reverse proxy's port number via which Bamboo is accessed.
#### bamboo_tomcat_port
- Default: 8085
- Description: The port for Tomcat/Bamboo to listen on.
#### bamboo_tomcat_scheme
- Default: http
- Description: The protocol via which the application is accessed. 
#### bamboo_tomcat_secure
- Default: false
- Description: Set 'true' if bamboo_tomcat_scheme is 'https'.
#### bamboo_tomcat_contextpath
- Default: ""
- Description: The context path the application is served over. 
#### bamboo_tomcat_management_port
- Default: 8007
- Description: The TCP/IP port number on which this server waits for a shutdown command. Set to -1 to disable the shutdown port.
#### bamboo_tomcat_maxthreads
- Default: 150
- Description: The maximum number of request processing threads to be created by this Connector, which therefore determines the maximum number of simultaneous requests that can be handled.
#### bamboo_tomcat_connection_timeout
- Default: 25
- Description: The number of milliseconds this Connector will wait, after accepting a connection, for the request URI line to be presented.
#### bamboo_tomcat_enable_lookups
- Default: false
- Description: Set to true if you want calls to request.getRemoteHost() to perform DNS lookups in order to return the actual host name of the remote client. Set to false to skip the DNS lookup and return the IP address in String form instead (thereby improving performance).
#### bamboo_tomcat_acceptcount
- Default: 1000
- Description: The maximum length of the operating system provided queue for incoming connection requests when maxConnections has been reached.
#### bamboo_tomcat_address
- Default: ""
- Description: or servers with more than one IP address, this attribute specifies which address will be used for listening on the specified port. By default, the connector will listen all local addresses.
##### bamboo_tomcat_encryption_key
- Default: ""
- Description: File which contains encryption key used for Bamboo-specific connectors.
#### bamboo_tomcat_client_auth
- Default: ""
- Description: This is an alias for the certificateVerification attribute of the SSLHostConfig element with the hostName of _default_. If this SSLHostConfig element is not explicitly defined, it will be created.
#### bamboo_truststore
- file
  - Default: ""
  - Description: The trust store file to use to validate client certificates. The default is the value of the javax.net.ssl.trustStore system property. If neither this attribute nor the default system property is set, no trust store will be configured. Relative paths will be resolved against $CATALINA_BASE. A URL may also be used for this attribute.
- password
  - Default: ""
  - Description: The password to access the trust store. The default is the value of the javax.net.ssl.trustStorePassword system property. If that property is null, no trust store password will be configured. If an invalid trust store password is specified, a warning will be logged and an attempt will be made to access the trust store without a password which will skip validation of the trust store contents.
#### bamboo_tomcat_ssl
  - enabled 
    - Default: false
    - Description: Use this attribute to enable SSL traffic on a connector. 
  - protocol
    - Default: TLSv1.2
    - Description: The SSL protocol(s) to use (a single value may enable multiple protocols - see the JVM documentation for details).
  - cert_file
    - Default: ""
    - Description: Name of the file that contains the server certificate.
  - key_file
    - Default: ""
    - Description: Name of the file that contains the server private key.
  - key_password:
    - Default: ""
    - Description: The password used to access the private key associated with the server certificate from the specified file.
  - keystore_file:
    - Default: ""
    - Description: The pathname of the keystore file where you have stored the server certificate and key to be loaded. 
  - keystore_password: 
    - Default: changeit
    - Description: The password to use to access the keystore containing the server's private key and certificate.

### Bamboo
#### bamboo_version
- major
  - Default: 8
  - Description: Bamboo major version.
- minor
  - Default: 0
  - Description: Bamboo minor version.
- patch 
  - Default: 4
  - Description: Bamboo patch version. 
#### bamboo_system_user
- Default: bamboo
- Description: The system user that will be running the service.
#### bamboo_home_directory
- Default: /opt/bamboo
- Description: The bamboo home directory path.
#### bamboo_locale
- Default: en_GB.UTF-8
- Description: The locale to set when creating the postgres database and user.
#### bamboo_broker_uri
- Default: nio://0.0.0.0:54663
- Description: The ActiveMQ Broker URI to listen on for in-bound remote agent communication.
#### bamboo_broker_client_uri
- Default: ""
- Description: The ActiveMQ Broker Client URI that remote agents will use to attempt to establish a connection to the ActiveMQ Broker on the Bamboo server.
#### bamboo_build_number
- Default: 0
- Description: Bamboo initial build number.
#### bamboo_autologin_cookie_age
- Default: 1209600
- Description: The maximum time a user can remain logged-in with 'Remember Me'.

### Database
#### bamboo_database_pool
- min
  - Default: 3
  - Description: Database pool min size.
- max
  - Default: 100
  - Description: Database pool max size.
#### bamboo_database_timeout
- Default: 120000
- Description: Database connection timeout.
#### bamboo_database
- Description: Bamboo database connection variables
- Default: 
  - bamboo
    - host 
      - Default: 127.0.0.1
      - Description: The Hostname / IP of the database.
    - port
      - Default: 5432
      - Description: The port to use when connecting to the database.
    - name
      - Default: bamboo
      - Description: The name of the schema to use.
    - owner
      - Default: bamboo
      - Description: The owner of the database schema.
    - username
      - Default: bamboo
      - Description: The username to use when connecting to the database.
    - password
      - Default: password
      - Description: The password to use when connecting to the database.
    - enabled
      - Default: true
      - Description: Set whether to enable the database. Will be used in future iterations.

### Webserver
#### bamboo_webserver_port
- Default: 8085
- Description: The port that the webserver will listen on.
#### bamboo_webserver_baseurl
- Default: http://127.0.0.1
- Description: The base URL to set when configuring Bamboo.
#### bamboo_webapp_context_path
- Default: /
- Description: The context path the application is served over.

### Temurin / OpenJDK
# temurin_version
- major
  - Default: 11
  - Description: OpenJDK major version
- minor
  - Default: 0
  - Description: OpenJDK minor version
- patch
  - Default: 13
  - Description: OpenJDK patch version
- build
  - Default: 8
  - Description: OpenJDK build number

### Bamboo Preseed (Not supported until version 8.1)
#### bamboo_pressed_security_token
- Default: ""
- Description: The security token to use for server/agent authentication
#### bamboo_preseed_disable_agent_auth
- Default: false
- Description: 
#### banboo_unattended_installation
- Default: false
#### bamboo_license
- Default: ""
- Description: The licence to supply. Licenses can be generated at [https://my.atlassian.com/](https://my.atlassian.com/)
#### bamboo_admin:
- username
  - Default: admin
  - Description: The administrator username to configure upon initialisation.
- password
  - Default: password
  - Description: The administrator password to configure upon initialisation.
- full_name
  - Default: Systems Administrator
  - Description: The full name of the system administrator.
- email
  - Default: systems.administrator@example.local
  - Description: The email address of the system administrator.
#### bamboo_skip_config
- Default: false
- Description: If true skip the generation of bamboo.cfg.xml
#### bamboo_import_option
- Default: clean
- Description: Import data from backup file during setup. Default value is 'clean' which skip import step and create Bamboo home from scratch. If value is 'import' then _bamboo_import_path_ should contain path to backup archive.
#### bamboo_import_path: 
- Default: ""
- Description: Full path to backup archive. 