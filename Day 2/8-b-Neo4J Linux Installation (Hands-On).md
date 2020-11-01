Hardware requirements
---------------------

8 Core Processor

16 GB Ram

Sata Express -- 20 GB

Software requirements
---------------------

MacOS

Ubuntu Desktop

Windows Server 2016+

OpenJDK 11

For proper ACID behavior, the filesystem must support flush (fsync,
fdatasync).

Neo4j Desktop is available for developers and personal users. Neo4j
Desktop is bundled with a JVM.

Ubuntu Installation Instructions
--------------------------------

Refer:
<https://debian.neo4j.com/?_ga=2.15948341.2019572201.1603436054-533716159.1603436054>

sudo add-apt-repository universe

sudo apt-fast -y update

sudo add-apt-repository -y ppa:openjdk-r/ppa

sudo apt-fast -y update

sudo wget -O - https://debian.neo4j.com/neotechnology.gpg.key \| sudo
apt-key add -

echo \'deb https://debian.neo4j.com stable 4.1\' \| sudo tee -a
/etc/apt/sources.list.d/neo4j.list

sudo apt-fast update

**\#verify which Neo4j versions are available**

apt list -a neo4j

**\# Install Neo4j Enterprise Edition**

sudo apt-fast install -y neo4j-enterprise=1:4.1.3

-   Chose Ok and then \"I Accept\"

ulimit -n 60000

### Neo4J Configuration

Stored in /etc/neo4j/neo4j.conf

\#Set password

sudo usermod -aG sudo neo4j

sudo passwd neo4j

logout

Delete the previous connection from Mobaxterm

Now login again using neo4j user name

### Starting the service automatically on system start

sudo systemctl enable neo4j

### Controlling the service

sudo systemctl start neo4j

sudo systemctl stop neo4j

sudo systemctl restart neo4j

sudo systemctl status neo4j

### 

### Log

sudo journalctl -e -u neo4j

### Enable below Ports on Firewall/ Inbound Port Rules

7687,5000,6000,7000,7688,2003,2004,3637,5005,7474

### Allow All IP Addresses to access Neo4J

\#Open neo4j.conf file

sudo vim /etc/neo4j/neo4j.conf

**\#Uncomment:**

dbms.default_listen_address=0.0.0.0

**\#Restart**

sudo systemctl stop neo4j

sudo systemctl start neo4j

### Set Default Password (Optional)

sudo neo4j-admin set-initial-password secret

sudo neo4j-admin set-initial-password \--require-password-change secret

**Login Details:**

**URL**

**Username/Password**

neo4j/ secret

Or

neo4j/ neo4j

Uninstall Ubuntu (Not required)
-------------------------------

sudo systemctl stop neo4j

sudo apt-get -y purge neo4j

sudo apt-get -y purge neo4j-enterprise

sudo rm -rf /etc/neo4j

sudo rm -rf /var/lib/neo4j

sudo rm -rf /usr/share/neo4j

sudo rm -rf /var/log/neo4j
