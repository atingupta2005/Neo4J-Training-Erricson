Download Mobaxterm
==================

https://download.mobatek.net/2032020060430358/MobaXterm_Portable_v20.3.zip

SSH to the Cloud Machine
========================

-   Extract MobaXterm_Portable_v20.3.zip

-   Run MobaXterm_Personal_20.3.exe

-   Take your VM IP address and credentials

-   Create SSH session to the cloud machine

Enable for Fast Download
========================

sudo apt -y update

sudo apt -y upgrade

sudo add-apt-repository ppa:apt-fast/stable

sudo apt -y update

sudo apt -y install apt-fast

-   Package manager to install: apt

-   Maximum number of connections: 20

-   Supress apt-fast confirmation dialogue: Yes

sudo vim /etc/apt-fast.conf

MIRRORS=(\'http://fr.archive.ubuntu.com/ubuntu,http://bouyguestelecom.ubuntu.lafibre.info/ubuntu,http://mirror.ovh.net/ubuntu,http://ubuntu-archive.mirrors.proxad.net/ubuntu,http://mirror.enzu.com/ubuntu,http://mirror.genesisadaptive.com/ubuntu,http://mirror.math.princeton.edu/pub/ubuntu,http://mirror.pit.teraswitch.com/ubuntu,http://mirrors.xtom.com/ubuntu,http://mirror.arizona.edu/ubuntu,http://mirror.brightridge.com/ubuntuarchive,http://mirror.nodesdirect.com/ubuntu,http://mirrors.rit.edu/ubuntu,http://ny-mirrors.evowise.com/ubuntu,http://plug-mirror.rcac.purdue.edu/ubuntu\')

sudo apt-fast install -y ne

Add User to Sudoers
===================

sudo usermod -aG sudo \$USER

\#Verify User Belongs to Sudo Group

groups \$USER

\#Verify Access

su - \$USER

exit

\#Install Ubuntu various utilities

sudo apt-fast -y install tree

sudo apt-fast -y install unzip

sudo apt-fast -y install htop

sudo apt-fast -y install jq
