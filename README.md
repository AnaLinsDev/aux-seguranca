<h2>
  
 hostname -I
  
sudo apt-get install iptables
  
sudo apt update
  
sudo apt install build-essential git dkms
  
git clone https://github.com/tomaspinho/rtl8821...
  
cd rtl8821ce
  
sudo ./dkms-install.sh
  
sudo modprobe 8821ce
  
reboot
  
  -----------------------------
  -----------------------------
  -----------------------------
  
comando→ sudo su <br>
comando→ apt-get install -y apache2 telnetd nmap curl

comando→ iptables -F INPUT <br>
comando→ iptables -A INPUT -p all -j ACCEPT

comando→ iptables -L -n --line-numbers

curl http://IP_HOST_A

comando→ iptables -I INPUT 1 -p tcp --dport 80 -j REJECT

comando→ iptables -L -n --line-numbers

curl http://IP_HOST_A


comando→ telnet IP_HOST_A
senha: ****
exit

comando→ iptables -I INPUT 1 -p tcp --dport 23 -j REJECT

comando→ iptables -L -n --line-numbers

comando→ ping IP_HOST_A

comando→ iptables -I INPUT 1 -p icmp -j REJECT

comando→ iptables -L -n --line-numbers

comando→ iptables -D INPUT 1

comando→ iptables -I INPUT 1 -p icmp -j DROP

comando→ iptables -L -n --line-numbers

comando→ iptables -I INPUT 1 -p icmp -s IP_HOST_B -j ACCEPT

comando→ iptables-save > iptables-rules.txt

comando→ iptables -F INPUT

comando→ iptables -L -n --line-numbers

comando→ iptables-restore < iptables-rules.txt

comando→ cp iptables-rules.txt joao-iptables-rules.txt


</h2>










