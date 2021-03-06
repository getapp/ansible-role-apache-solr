apache-solr
=========

Role to install Apache Solr 5.4.0+.

By default the role will download the file specified in defaults/main.yml by apache_solr.download_url
Currently the role excpects the download_url to end with solr-X.Y.Z.tgz (where X.Y.Z is the version).

The role will install Solr using the included script (bin/install_solr_service.sh) inside the archive
using only the defaults.


Defaults:

```
 Solr installation dir (solr.install.dir): /opt/solr
 Solr home dir (solr.solr.home):           /var/solr/data
 Environment overrides include file:       /etc/default/solr.in.sh
```


Role Variables
--------------

defaults/main.yml

```
apache_solr:
 download_url: http://archive.apache.org/dist/lucene/solr/5.4.0/solr-5.4.0.tgz
 java: openjdk-7-jdk

apache_solr_log4j: log4j.properties.j2
apache_solr_env: Debian/solr-5.4.0.in.sh.j2

NOTES: Java - you can comment apache_solr.java if you manage Java outside of this role.

       apache_solr_log4j and apache_solr_env can be relative or full path to the actual files
       to be copied to remote.
```


Example Playbook
----------------

```
- hosts: us-east-1b-prod-search
  roles:
   - apache-solr
```


License
-------

MIT


Author Information
------------------

Tal Lannder

tal@pjili.org
