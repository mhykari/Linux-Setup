# Ansible Automation Repository to install zabbix agent on ubuntu host

## Description

This repository contains Ansible playbooks and roles for automating zabbix agent installation and configuration
- Install zabbix agent
- Install zabbix agent 2
- Modify zabbix_agentd.conf.d file

## How to use:
1- Set your variables in defaults/main.yml<br />
2- Use tag "zabbix_agent" or "zabbix_agent2" to select the zabbix agent version when running the playbook<br />
3- Run ansible-playbook using tag zabbix-agent<br />
4- If you get this error: "Received empty response from Zabbix Agent at [host_ip]. Assuming that agent dropped connection because of access permissions."
  - Make sure that the server_address:10050 is accessible from the host
  - Login to your host, check zabbix agent logs using this command: "tail -f /var/log/zabbix/zabbix_agentd.log | grep connection"
  - Copy the ip address in allowed hosts error and add it in the "zabbix_server" and "zabbix_server_active" variables in ansible defaults and run the palybook again,<br />or directly add the address in the zabbix_agentd.conf file in the host ( /etc/zabbix/zabbix_agentd.conf )
  - Restart zabbix-agent service.
