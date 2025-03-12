# Firewall-Configuration-for-Secure-Web-Traffic

## Firewall Configuration Tutorial (Windows & Linux)

This tutorial guides you through the process of configuring a firewall to allow only secure web traffic (HTTPS) to a server while blocking all other incoming connections. This is essential to ensure that only encrypted traffic reaches your server, enhancing security.

---

## Task Overview

- **Access the firewall configuration interface.**
- **Create a rule to allow incoming HTTPS (port 443) traffic to the server.**
- **Deny all other incoming traffic.**
- **Save and apply the configuration changes.**

---

## Step 1: Access the Firewall Interface

### If Using Windows Defender Firewall:

1. Open **Windows Defender Firewall with Advanced Security** by typing `wf.msc` in the Start menu search bar and pressing Enter.
2. In the left panel, select **Inbound Rules** to begin managing incoming traffic.

### If Using Linux IPTables:

1. Open a terminal window.
2. Gain root privileges by running the following command:
   ```bash
   sudo su
   
---

## Step 2: Create a Rule to Allow HTTPS Traffic

## Windows Firewall:
1. In the Inbound Rules section, click New Rule.
2. Select Port and click Next.
4. Choose TCP and specify port 443.
5. Select Allow the connection to permit HTTPS traffic.
6. Apply the rule to Domain, Private, and Public networks.
7. Click Finish to save the rule.

## Linux IPTables:
To allow HTTPS traffic on port 443, run the following command, replacing 192.168.1.100 with the IP address of your server:
  
sudo iptables -A INPUT -p tcp --dport 443 -d 192.168.1.100 -j ACCEPT
  

## Step 3: Deny All Other Incoming Traffic

## Windows Firewall:
1. In the Inbound Rules section, click New Rule again.
2. Choose Custom and click Next.
3. For Program, select All Programs and click Next.
4. Under Protocol and Ports, leave the settings as Any and click Next.
5. In the Scope section, keep the default settings (which apply to all IP addresses) and click Next.
6. For Action, select Block the connection and click Next.
7. Ensure that Domain, Private, and Public are all checked.
8. Click Next, then enter a descriptive name for the rule, such as Block All Incoming Traffic.
9. Click Finish to finalize the rule.

## Linux IPTables:
To block all other incoming traffic, run the following command, replacing 10.0.2.11 with your server's IP address:
  
  sudo iptables -A INPUT -d 10.0.2.11 -j DROP


## Step 4: Save and Apply the Rules

## Windows Firewall:
Windows automatically saves the firewall rules, so no additional steps are needed to apply them.

## Linux:
To ensure your changes persist after a reboot, save the IPTables rules with the following command:
  
  sudo iptables-save > /etc/iptables/rules.v4



✅ You’re Done!
Your firewall is now configured to allow only HTTPS traffic to your server, blocking all other incoming connections. This setup ensures that your server remains secure while enabling encrypted communication for legitimate users.

Final Thoughts
Configuring a firewall is a fundamental step in securing your server. By restricting traffic to HTTPS only, you significantly reduce the risk of unauthorized access and data breaches. Whether you’re using Windows or Linux, the process is straightforward and highly effective.
