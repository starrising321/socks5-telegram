#socks5 proxy telegram
#install dante-server
sudo apt update

sudo apt install dante-server

cd /etc/

rm -rf danted.conf

wget https://raw.githubusercontent.com/starrising321/socks5-telegram/main/danted.conf

nano danted.conf

search external: eth0 if it is default than ok if not change to external: venet0:0


sudo useradd --shell /usr/sbin/nologin proxyuser

sudo passwd proxyuser

sudo ufw allow 112

sudo ufw allow 113

sudo ufw allow 114

or

sudo iptables -I INPUT -p tcp -m tcp --dport 112 -j ACCEPT

sudo iptables -I INPUT -p tcp -m tcp --dport 113 -j ACCEPT

sudo iptables -I INPUT -p tcp -m tcp --dport 114 -j ACCEPT

iptables-save

mkdir /etc/iptables
i
ptables-save > /etc/iptables/rules.v4

sudo systemctl restart danted

sudo systemctl enable danted

sudo systemctl status danted


#you may see dante logs (connect disconnect error):

sudo journalctl -xe -u danted

#add -f argument to attach and watch

#test proxy on your local machine:

curl -v -x socks5://proxyuser:password@yourserverip:443 https://www.yandex.ru/


These files can be loaded again with the command iptables-restore for IPv4.

Debian/Ubuntu: iptables-restore < /etc/iptables/rules.v4


===============

COMPLETAMENTE FREE! 

===============

By ☆ https://t.me/star_Jani ☆ https://t.me/StarZany
