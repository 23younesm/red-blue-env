# CCDC Qualifier Environment

Heat template to configure a copy of the MW/MACCDC qualifier environment with the following hosts:

* Internal Subnet
  * Windows Server 2019 - Remote Docker
  * Debian 10 - DNS NTP
* User Subnet
  * Ubuntu 18 - Web
  * Windows Server 2019 - AD/DNS/DHCP
  * Ubuntu Wkst
* Public Subnet
  * Splunk
  * CentOS 7 - Ecommerce
  * Fedora 21 - Webmail

Creates X instances of this environment for teams, and a central master subnet for scoring and ansible deployment.
