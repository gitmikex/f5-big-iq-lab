Getting Started
===============

Starting the Lab
----------------

In order to complete this lab, you will find 2 ways to access the different systems in this lab:
   - From the Jump Host
      From the lab environment, launch a remote desktop session to access the Jump Host (Ubuntu Desktop). 
      To do this, in your lab deployment, click on the *ACCESS* button of the **Ubuntu Lamp Server** system and click on
      *noVNC*. The password is ``purple123``.

      |

      You can also use *XRDP* as an alternative, click on the resolution that works for your laptop. 
      When the RDP session launches showing *Session: Xorg*, simply click *OK*, no credentials are needed.
      Modern laptops with higher resolutions you might want to use 1440x900 and once XRDP is launched Zoom to 200%.

      |
      
      |udf_ubuntu_rdp_vnc|

   - Going directly to the BIG-IQ CM or BIG-IP TMUI or WEB SHELL/SSH
      To access the BIG-IQ directly, click on the *ACCESS* button under **BIG-IQ CM**
      and select *TMUI*. The credentials to access the BIG-IQ TMUI are ``david/david`` and ``paula/paula`` as directed in the labs.

      |udf_bigiq_tmui|

      To ssh into a system, you can click on *WEB SHELL* or *SSH* (you will need your ssh keys setup in the lab environment for SSH).

      |    

      You can also click on *DETAILS* on each component to see the credentials (login/password).

.. |udf_ubuntu_rdp_vnc| image:: /pictures/udf_ubuntu_rdp_vnc.png
   :scale: 60%

.. |udf_bigiq_tmui| image:: /pictures/udf_bigiq_tmui.png
   :scale: 60%

BIG-IQ User Interface
---------------------

Once you connect to BIG-IQ, you can navigate in the following tabs:

- **Applications** - Application Management (Legacy, AS3) and Cloud Environment
- **System** - Manage all aspects for BIG-IQ and DCDs.
- **Devices** - Discover, Import, Create, Onboard (DO) and Manage BIG-IP devices.
- **Deployment** - Manage evaluation task and deployment for Configuration Management (none AS3)
- **Configuration** - ADC and Security Object Management (ASM, AFM, APM, DDOS, SSLo config/monitoring)
- **Monitoring** - Event collection per device, statistics monitoring, iHealth reporting integration, alerting, and audit logging.

|welcomebigiq|

.. |welcomebigiq| image:: /pictures/welcomebigiq.png
   :scale: 40%

Lab Diagram
-----------

.. image:: ./pictures/diagram_udf.png
   :align: center
   :scale: 40%

List of instances & Credentials
-------------------------------

The following table lists the virtual appliances in the lab along with their credentials to use.

+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| System                  | Version | Description                                                                                  | Credentials                     |
+=========================+=========+==============================================================================================+=================================+
| BIG-IQ CM               | 7.1.0.1 | Using BIG-IQ, you can centrally manage your BIG-IP devices,                                  | - admin/purple123 *(local)*     |
| 10.1.1.4                |         | performing operations such as backups, licensing, monitoring,                                | - david/david *(RadiusServer)*  |
|                         |         | and configuration management.                                                                | - paula/paula *(RadiusServer)*  |
|                         |         |                                                                                              | - paul/paul *(RadiusServer)*    |
|                         |         |                                                                                              | - olivia/olivia *(RadiusServer)*|
|                         |         |                                                                                              | - larry/larry *(RadiusServer)*  |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| BIG-IQ DCD              | 7.1.0.1 | A data collection device (**DCD**) is a specially provisioned                                | admin/purple123                 |
| 10.1.1.6                |         | BIG-IQ system that you use to manage and store alerts, events,                               |                                 |
|                         |         | and statistical data from one or more BIG-IP systems.                                        |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| BIG-IP Boston           | 13.1    | HA Pair                                                                                      | admin/purple123                 |
| 10.1.1.8/10.1.1.10      |         |                                                                                              |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| BIG-IP Seattle          | 14.1    | Standalone                                                                                   | admin/purple123                 |
| 10.1.1.7                |         |                                                                                              |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| BIG-IP Paris            | 14.1    | Standalone                                                                                   | admin/purple123                 |
| 10.1.1.13               |         |                                                                                              |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| BIG-IP San Jose         | 15.1    | Standalone                                                                                   | admin/purple123                 |
| 10.1.1.11               |         |                                                                                              |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| SSLo Service TAP and L3 |         | Maximize infrastructure investments, efficiencies,                                           | ubuntu/purple123                |
| 10.1.1.14/10.1.1.16     |         | and security with dynamic, policy-based decryption,                                          |                                 |
|                         |         | encryption, and traffic steering through multiple inspection devices.                        |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| Venafi Trust Protection | 20.1    | Manages, secures and protects keys and certificates, delivering an enterprise-grade platform | venafi/Purple123\@123           |
| 10.1.1.17               |         | that provides enterprise-wide security, operational efficiency and                           |                                 |
|                         |         | organizational compliance.                                                                   |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+
| LAMP Server             |         | - Radius, LDAP, TACAx (auth)                                                                 | f5student/purple123             |
| 10.1.1.5                |         | - xRDP and noVNC for User Remote Desktop                                                     |                                 |
|                         |         | - AWX/Ansible Tower                                                                          | noVNC password is purple123     |
|                         |         | - GitLab                                                                                     |                                 |
|                         |         | - Splunk                                                                                     |                                 |
|                         |         | - Application Servers (Hackazon, dvmw, f5 demo app, arcadia, juice shop)                     |                                 |
|                         |         | - Traffic Generator (HTTP, Access, DNS, Security)                                            |                                 |
|                         |         | - Visual Studio Code                                                                         |                                 |
|                         |         | - Samba                                                                                      |                                 |
+-------------------------+---------+----------------------------------------------------------------------------------------------+---------------------------------+

Networks
--------

- 10.1.1.0/24 Management Network
- 10.1.10.0/24 External Network
- 10.1.20.0/24 Internal Network
- 10.1.30.0/24 SSLo Inline L3 IN Network
- 10.1.40.0/24 SSLo Inline L3 OUT Network
- 10.1.50.0/24 SSLo TAP Network
- 172.17.0.0/16 Docker Internal Network
- 172.100.0.0/16 AWS Internal Network
- 172.200.0.0/16 Azure Internal Network

Application Services already deployed in this lab
-------------------------------------------------

+------------------+-------------------------------------+-------------------------------------------------------------+----------------------+--------------+-------------+
| Applications     | Application Services                | BIG-IQ Template used                                        | IP/WideIP            | Location     | User Access |
+==================+=====================================+=============================================================+======================+==============+=============+
| airport_security | AS3 security_site18_seattle         | AS3-F5-HTTPS-WAF-external-url-lb-template-big-iq-default-v2 | 10.1.10.118          | Seattle      | Paula       |
|                  +-------------------------------------+-------------------------------------------------------------+----------------------+--------------+             |
|                  | AS3 security_site16_boston          | AS3-F5-HTTP-lb-traffic-capture-template-big-iq-default-v1   | 10.1.10.116          | Boston       |             |
|                  +-------------------------------------+-------------------------------------------------------------+----------------------+--------------+             |
|                  | AS3 security_fqdn                   | AS3-F5-DNS-FQDN-A-type-template-big-iq-default-v1           | airports.example.com | Boston       |             |
+------------------+-------------------------------------+-------------------------------------------------------------+----------------------+--------------+-------------+
| IT_apps          | AS3 backend_site24tcp               | AS3-F5-TCP-lb-built-in-profile-template-big-iq-v1           | 10.1.10.124          | Seattle      | Paula       |
|                  +-------------------------------------+-------------------------------------------------------------+----------------------+--------------+             |
|                  | Service Catalog site36.example.com  | Default-f5-HTTPS-WAF-lb-template-v1                         | 10.1.10.136          | Boston       |             |
|                  +-------------------------------------+-------------------------------------------------------------+----------------------+--------------+             |
|                  | Legacy App media.site42.example.com |                                                             | 10.1.10.142          | Seattle      |             |
+------------------+-------------------------------------+-------------------------------------------------------------+----------------------+--------------+-------------+
| finance_apps     | AS3 conference_site41waf            | without AS3 template using API                              | 10.1.10.141          | Seattle      | Paul        |
|                  +-------------------------------------+-------------------------------------------------------------+----------------------+--------------+             |
|                  | AS3 mail_site40waf                  | without AS3 template using API                              | 10.1.10.140          | Seattle      |             |
|                  +-------------------------------------+-------------------------------------------------------------+----------------------+--------------+             |
|                  | AS3 tax_site17access                | without AS3 template using API                              | 10.1.10.117          | Seattle      |             |
+------------------+-------------------------------------+-------------------------------------------------------------+----------------------+--------------+-------------+
        
User Roles
----------

+----------------------------+---------------------------------------------------------------+----------------+--------+
| Role Name                  | AS3 Templates                                                 | Devices        | Users  |
+============================+===============================================================+================+========+
| Administrator Role         | All                                                           | All            | david  |
|                            |                                                               |                | marco  |
+----------------------------+---------------------------------------------------------------+----------------+--------+
| Security Manager           | All                                                           | All            | larry  |
|                            |                                                               |                | chris  |
+----------------------------+---------------------------------------------------------------+----------------+--------+
| Application Creator AS3    | Allow using AS3 without Template                              | All            | olivia |
+----------------------------+---------------------------------------------------------------+----------------+--------+
| Application Creator Cloud  | - AS3-F5-HTTP-lb-template-big-iq-default-v1                   | All            | paul   |
|                            | - AS3-F5-TCP-lb-template-big-iq-default-v2                    |                |        |
|                            | - AS3-F5-HTTPS-WAF-existing-lb-template-big-iq-default-v1     |                |        |
+----------------------------+---------------------------------------------------------------+----------------+--------+
| Application Creator VMware | - AS3-F5-DNS-FQDN-A-type-template-big-iq-default-v1           | Boston BIG-IPs | paula  |
|                            | - AS3-F5-HTTP-lb-template-big-iq-default-v1                   | Seattle BIG-IP |        |
|                            | - AS3-F5-HTTP-lb-traffic-capture-template-big-iq-default-v1   |                |        |
|                            | - AS3-F5-HTTPS-WAF-external-url-lb-template-big-iq-default-v2 |                |        |
|                            | - AS3-F5-FastL4-TCP-lb-template-default-v2                    |                |        |
|                            | - AS3-F5-TCP-lb-built-in-profile-template-big-iq-v1           |                |        |
+----------------------------+---------------------------------------------------------------+----------------+--------+

Traffic Generation
------------------

The Ubuntu Jump-host in the lab environment has multiple cron jobs that are generating traffic that populates the Monitoring tab 
and Application dashboard in BIG-IQ. Note you can also use `locust.io`_  to generate HTTP traffic toward a specific virtual IP address.

.. _locust.io: ./class3/module1/module1.html#traffic-generation-with-locus-io

Below table shows the list of **Virtual Servers** and *Backend *Web Applications Servers** where various type of traffic
is being sent (check ``crontab`` config for more details).

.. warning:: Make sure the IP address on the external network 10.1.10.0/24 is defined in lab environment on 
             the BIG-IP external interface where you are deploying the application service or VIP.

+---------------------------------------------------------------------------------------------+
| Virtual IP addresses where the traffic generator send traffic to                            |
+================================+============================================================+
| HTTP clean traffic every 5 min | 10.1.10.110-116, 10.1.10.118, 10.1.10.120, 10.1.10.123-142 |
+--------------------------------+------------------------------------------------------------+
| HTTP bad traffic every 3 hours | 10.1.10.110-116, 10.1.10.118, 10.1.10.120, 10.1.10.123-142 |
+--------------------------------+------------------------------------------------------------+
| Access traffic (class 9)       | 10.1.10.117, 10.1.10.119, 10.1.10.121, 10.1.10.222         |
+--------------------------------+------------------------------------------------------------+
| DNS traffic (class 10)         | 10.1.10.203, 10.1.10.204                                   |
+--------------------------------+------------------------------------------------------------+

.. note:: IPs from ``10.1.10.110`` to ``10.1.10.142`` have a corresponding FQDN named from ``site10.example.com`` to ``site42.example.com``.

+-----------------------------------------------------------------------+
| Backend Web Applications Servers                                      |
+=======================================================================+
| 10.1.20.110-123                                                       |
|                                                                       |
| - Port ``80``: `hackazon`_ application (test_user/123456)             |
| - Port ``8080``: `web-dvwa`_ application (admin/password)             |
| - Port ``8081``: f5-hello-world application                           |
| - Port ``8082``: f5-demo-httpd application                            |
| - Port ``8083``: nginx application (delay 300ms loss 30% corrupt 30%) |
| - Port ``8084``: `arcadia finance`_ (admin/iloveblue)                 |
| - Port ``8085``: `juice-shop`_ (admin@juice-sh.op/admin123)           |
| - Port ``446``: ASM Policy Validator                                  |
+-----------------------------------------------------------------------+

.. _hackazon: https://github.com/rapid7/hackazon
.. _web-dvwa: https://hub.docker.com/r/vulnerables/web-dvwa
.. _arcadia finance: https://gitlab.com/MattDierick/arcadia-finance
.. _juice-shop: https://owasp.org/www-project-juice-shop/

Miscellaneous
-------------

To run `Kali Linux`_ Docker Image: ``docker run -t -i kalilinux/kali-linux-docker /bin/bash`` *(run apt-get update && apt-get install metasploit-framework after starting Kali Linux)*

.. _Kali Linux: https://en.wikipedia.org/wiki/Kali_Linux

To connect to a docker instance: ``docker exec -i -t <container id or name> /bin/bash``

+--------+--------------------------------------------------------------------------------+
| Radius | - ip:port 10.1.1.5:1812                                                        |
|        | - secret = default                                                             |
|        | - Users: https://github.com/f5devcentral/f5-big-iq-lab/tree/develop/lab/radius |
+--------+--------------------------------------------------------------------------------+
| LDAP   | - ip:port 10.1.1.5:389                                                         |
|        | - SSL: Disabled                                                                |
|        | - Bind User Distinguished Name: cn=admin,dc=f5demo,dc=com                      |
|        | - Bind User Password: ldappass                                                 |
|        | - User Bind Template: uid={username},ou=People,dc=f5demo,dc=com                |
|        | - Root Distinguished Name: dc=f5demo,dc=com                                    |
|        | - Group Search Filter: (&(objectClass=groupOfUniqueNames)(cn={searchterm}*))   |
|        | - Group Membership Filter: uniqueMember={userDN}                               |
|        | - Directory User Search Filter: uid={username}                                 |
|        | - Group Distinguished Name: cn=admin,ou=Groups,dc=f5demo,dc=com                |
|        | - Users: https://github.com/f5devcentral/f5-big-iq-lab/tree/develop/lab/ldap   |
+--------+--------------------------------------------------------------------------------+
| Tacac+ | - ip:port 10.1.1.5:49                                                          |
|        | - secret = ciscotacacskey                                                      |
|        | - Primary Service = shell                                                      |
|        | - Encrypt = yes                                                                |
|        | - Users: iosadmin/cisco, nxosadmin/cisco                                       |
+--------+--------------------------------------------------------------------------------+

+-------+-------------------------------+
| XRDP  | - ip:port 10.1.1.5:3389       |
+-------+-------------------------------+
| noVNC | - ip:port 10.1.1.5:6080 https |
+-------+-------------------------------+

+------------------------+----------------------------------------+
| `Splunk`_              | - ip:port 10.1.1.5:8000 https          |
|                        | - HTTP Event Data Collector port 8088  |
+------------------------+----------------------------------------+
| `AWX (Ansible Tower)`_ | - ip:port 10.1.1.5:9001 https          |
+------------------------+----------------------------------------+
| `GitLab`_              | - ip:port 10.1.1.5:7002 https 7022 ssh |
+------------------------+----------------------------------------+
| `Visual Studio Code`_  | - ip:port 10.1.1.5:7001 https          |
+------------------------+----------------------------------------+
| `Locust`_              | - ip:port 10.1.1.5:7089 https          |
+------------------------+----------------------------------------+
| Samba                  | - ip:port 10.1.1.5:445                 |
|                        | - User: f5student/purple123            |
|                        | - Domain: WORKGROUP                    |
|                        | - Storage Path: //10.1.1.5/dcdbackup   |
+------------------------+----------------------------------------+

.. _AWX (Ansible Tower): https://www.ansible.com/products/awx-project/faq
.. _Splunk: https://www.splunk.com
.. _Visual Studio Code: https://github.com/cdr/code-server
.. _GitLab: https://gitlab.com
.. _Locust: https://locust.io