NGINX Server with PHP Extensions
================================

This role installs and configures the NGINX Web Server on a system, as well as the PHP 8.1 extensions.  Options exist whether the server is on an Internet-connected network or on an isolated network.

This role will also install a new default index.php file in /usr/share/nginx/html that shows the installed PHP extensions.
This file should be deleted on any further use after you have verified your system is operating correctly.

Requirements
------------

None

Role Variables
--------------

The following variables can be set for this role:

* connected_network: BOOLEAN.  Is the network connected to the Internet
* repo_server: STRING.  Protocol and server name (i.e., https://repo.test.lab)
* repo_path: STRING.  Path on the local repository server for the package repository
* cert_path: STRING.  Path on the local repository server to the Package GPG Certificate
* enable_service: BOOLEAN.  Do you want to enable this service on startup>
* enable_ssl: STRING.  Enable SSL/TLS certificates and the HTTPS protocol on port 443.
* ssl_cert_archive: STRING.  Path on the local system with an archive containing the server certificate and private key.

Dependencies
------------

None

Example Playbook
----------------

This role can be included into an Ansible playbook like so:

```
    - hosts: servers
      roles:
         - name: nginx-php-server
           connected_network: false
           repo_server: http://repo.lab.net
           repo_path: repo/nginx-server
           cert_path: certs/nginx-signing.gpg
           enable_service: true
           enable_ssl: false
```


License
-------

MIT

Author Information
------------------

Alex Ackerman, @darkhonor
