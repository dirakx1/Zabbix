# Zabbix

# Install zabbix_agent
## Install Zabbix Agent as non root on Debian

### Download the precompiled binary :
$> mkdir /tmp/zagent && cd /tmp/zagent
$> wget http://repo.zabbix.com/zabbix/3.2/debian/pool/main/z/zabbix/zabbix-agent_3.2.0-1+jessie_amd64.deb

### Decompress the package in a temporary directory :
$> dpkg -x zabbix-agent_3.2.0-1+jessie_amd64.deb

### Keep only the interesting file and remove the rest :
$> cp /tmp/zagent/usr/sbin/zabbix_agentd .
$> cp /tmp/zagent/etc/zabbix/zabbix_agentd.conf .

### Change some lines in the config file :
- LogFile=   (line 33)
- PidFile=   (line 14)
- Include=   (line 267)
- ListenPort= (if needed)
- Server= (line 95) set it to : 10.133.97.105

### Start the zabbix-agent daemon :

$> ./zabbix_agentd -c zabbix_agentd.conf -f

### And start as a "background" process (so it stays up after SSH disconnect) :

$> nohup ./zabbix_agentd -c zabbix_agentd.conf -f &

