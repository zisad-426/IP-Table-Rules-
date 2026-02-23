# IP-Table-Rules-
IP Table Rules on 2 Machinc

# IP Table Rules on 2 Machinc

#Total Project 
#I have finished setting up my 2 Ubuntu servers, one server can ping another server, now my plan is that in the same VM, the first Ubuntu can ping the second Ubuntu, and the second Ubuntu can ping the first Ubuntu, again the first Ubuntu can access the second, can access HTTP port-80, can't do other protocols and can't access anything, but Ubuntu 1 can't ping Ubuntu 2 or anything else, can't access, is this possible? Now I'm not able to connect to the terminals again. It will only be inside the 2 boxes, there will be no problems outside and everything will be done.

# Mu Project Plan

```1️ Agent-01 ↔ Agent-02 ping করবে```
2 Agent-01 → Agent-02 শুধু HTTP (80) access পাবে
3️ Agent-01 → Agent-02 SSH / অন্য কোনো protocol পাবে না
4️ Agent-02 → Agent-01 SSH পাবে না
5️ Termius (PC) → দুই agent-এই SSH পাবে
6️ সব কিছু এই 2টা VM এর ভেতরেই, বাইরে কোনো access দরকার নাই
7️ Termius যেন block না হয়

# All rules clear $ Commands for one click


$ sudo iptables -F
$ sudo iptables -X
$ sudo iptables -t nat -F
$ sudo iptables -t nat -X
$ sudo iptables -t mangle -F
$ sudo iptables -t mangle -X
$ sudo iptables -P INPUT ACCEPT
$ sudo iptables -P FORWARD ACCEPT
$ sudo iptables -P OUTPUT ACCEPT

# Ubuntu_Machin-01 Roles command

$ sudo iptables -F
$ sudo iptables -X
$ sudo iptables -A INPUT -i lo -j ACCEPT
$ sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A INPUT -p tcp -s 192.168.33.1 --dport 22 -j ACCEPT
$ sudo iptables -A INPUT -p icmp -s 192.168.33.132 -j ACCEPT
$ sudo iptables -P INPUT DROP
$ sudo iptables -P FORWARD DROP
$ sudo iptables -P OUTPUT ACCEPT
# Full Setup For Ubontu Machin-01

# Ubuntu_Machin-2 Roles command

$ sudo iptables -F
$ sudo iptables -X
$ sudo iptables -A INPUT -i lo -j ACCEPT
$ sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A INPUT -p tcp -s 192.168.33.1 --dport 22 -j ACCEPT
$ sudo iptables -A INPUT -p icmp -s 192.168.33.130 -j ACCEPT
$ sudo iptables -A INPUT -p tcp -s 192.168.33.130 --dport 80 -j ACCEPT
$ sudo iptables -P INPUT DROP
$ sudo iptables -P FORWARD DROP
$ sudo iptables -P OUTPUT ACCEPT
$ sudo apt update
$ sudo apt install apache2 -y

# More Important All allow Rouls

$ sudo iptables -F
$ sudo iptables -X
$ sudo iptables -A INPUT -i lo -j ACCEPT
$ sudo iptables -A OUTPUT -o lo -j ACCEPT
$ sudo iptables -A INPUT -p tcp -s ]<Your_IP> --dport 22 -j ACCEPT
$ sudo iptables -A OUTPUT -p tcp -d <Your_IP> --sport 22 -j ACCEPT
$ sudo iptables -A INPUT -s <Your_IP> -j ACCEPT
$ sudo iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A INPUT  -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -P INPUT DROP
$ sudo iptables -P FORWARD DROP
$ sudo iptables -P OUTPUT DROP


# Chack Your Rules 

# Pless Flow me 
#Thank You 
#2026


