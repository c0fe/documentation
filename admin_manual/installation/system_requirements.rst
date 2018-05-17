===================
System requirements
===================

Memory
------

Memory requirements for running an Nextcloud server are greatly variable,
depending on the numbers of users and files, and volume of server activity.
Nextcloud needs a minimum of 128MB RAM, and we recommend a minimum of 512MB.

Recommended setup for running Nextcloud
---------------------------------------

For best performance, stability, support, and full functionality we recommend:

* Red Hat Enterprise Linux 7 / Ubuntu 16.04 LTS
* MySQL/MariaDB
* PHP 7.0, 7.1, or 7.2
* Apache 2.4 with mod_php

Supported platforms
-------------------

* Server: Linux (Debian 8, SUSE Linux Enterprise Server 11 SP3 & 12,
  Red Hat Enterprise Linux/CentOS 6.5 and 7 (7 is 64-bit only), 16.04 LTS and 18.04 LTS)
* Web server: Apache 2 (mod_php, php-fpm) or Nginx (php-fpm)
* Databases: MySQL/MariaDB 5.5+; PostgreSQL 9, 10; Oracle 11g (currently only possible
  if you `contact us <https://nextcloud.com/enterprise>` as part of a subscription)
* PHP 5.6 + required (up to PHP 7.2)
* Hypervisors: Hyper-V, VMware ESX, Xen, KVM
* Desktop: Windows 7+, Mac OS X 10.7+ (64-bit
  only), Linux (CentOS 6.5, 7 (7 is 64-bit only), Ubuntu 16.04, Ubuntu 18.04,
  Fedora 20, 21, openSUSE 12.3, 13, Debian 7 & 8).
* Mobile apps: iOS 7+, Android 4+
* Web browser: IE11+, Microsoft Edge, Firefox 14+, Chrome 18+, Safari 7+

See :doc:`source_installation` for minimum software versions for installing
Nextcloud.

Database requirements for MySQL / MariaDB
-----------------------------------------

The following is currently required if you're running Nextcloud together with a MySQL / MariaDB database:

* InnoDB storage engine (MyISAM is not supported)
* "READ COMMITED" transaction isolation level (See: :ref:`db-transaction-label`)
* Disabled or BINLOG_FORMAT = ROW configured Binary Logging (See: https://dev.mysql.com/doc/refman/5.7/en/innodb-transaction-isolation-levels.html)

Emoji (UTF8 4-byte) support with MySQL / MariaDB
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to use UTF8 4-byte characters such as Emojis on your server, the database needs to be created with character set ``utf8mb4`` and collate ``utf8mb4_general_ci``, e.g.::

  CREATE DATABASE nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;

Additionally the following InnoDB settings need to be set::

  [mysqld]
  innodb_large_prefix=on
  innodb_file_format=barracuda
  innodb_file_per_table=true

See :doc:`../configuration_database/mysql_4byte_support` for more information.
