# metasploitable3
Metasploitable3 install on kali linux or debian

Metasploitable3 është një VM që është ndërtuar nga themeli me një sasi të madhe dobësish sigurie.
Ai synohet të përdoret si një objektiv për testimin e shfrytëzimeve me metasploit.

Metasploitable3 lëshohet nën një licencë të stilit BSD. 


1=> Si fillim nese keni instaluar paketues dhe virtualbox ne sistemin tuaj, kali linux ose debian!
duhet ti c`istaloni dhe te pastorni cachen e ktyre software dhe te hapat e me poshtme.

sudo apt --purge remove packer

sudo rm /usr/local/bin/packer

sudo rm /usr/bin/packer

sudo apt --purge remove virtualbox
sudo apt --purge remove virtualbox*

sudo rm ~/"VirtualBox VMs" -Rf

sudo rm ~/.config/VirtualBox  -Rf


duhet ti c`istaloni dhe te pastorni cachen e ktyre software dhe te hapat e me poshtme.

2=> Nese nuk i keni instaluar keto ater beni skip pjesen e mesiperme dhe fillon me komandat e me poshtme:

sudo apt install virtualbox-qt

sudo apt-get install libvirt-daemon libvirt-clients virt-manager python3-libvirt vagrant vagrant-libvirt

3=> Me pas duhet te krijojme nje file me emrin networks.conf per te assign ip per host-only per virtualbox:

mkdir /etc/vbox

4=> pastaj do krijojme nje file te ri me emrin si me siper:

sudo touch /etc/vbox/networks.conf 

5=> do editojme filen e ri qe krijuarm dhe do vendosim :

sudo nano /etc/vbox/networks.conf

* 0.0.0.0/0 ::/0

dhe pas ctrl + x dhe yes

6=> paster duhet te krijojme nje direktori me komandat e meposhteme:

mkdir metasploitable3-workspace

cd metasploitable3-workspace

curl -O https://raw.githubusercontent.com/rapid7/metasploitable3/master/Vagrantfile && vagrant up

7=> pasti te mbaroj procedura e instalimit te ubuntu server do te beni nje komande tjeter per installimin e windows server

vagrant up --provider virtualbox

dhe te dy sistemet jane aktive!


PS:

nese do keni error te tjera te tipit :

Emri: rapid7/metasploitable3-win2k8
Adresa: https://vagrantcloud.com/rapid7/metasploitable3-win2k8
Ofruesi i kërkuar: [:libvirt]

duhet te veproni si me poshte:
mkdir -p ~/tmp/

cd ~/tmp/

git clone https://github.com/jcf/vagrant-libvirt

cd ./vagrant-libvirt/

git checkout upgrade-nokogiri

gem build vagrant-libvirt.gemspec

vagrant plugin install  ~/tmp/vagrant-libvirt/vagrant-libvirt-*.gem
