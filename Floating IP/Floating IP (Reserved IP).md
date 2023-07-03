# **Floating IP (Reserved IP)**
A Floating IP is an IP address that can be instantly moved from one Droplet to another Droplet in the same datacenter.  
Part of a highly available infrastructure is being able to immediately point an IP address to a redundant server.
## **How It works**
Single points of failure can ve downfall of any application. With Floating IPs, customers can associate an IP address with a different Droplet, with minimal downtime. This makes it possible to set up a standby Droplet, ready to receive yourr production traffic at a moment's notice.  
![](img/ha-diagram-animated.gif)
### **Automatic Failover**
With a bit of scripting, you're able to set up redundant load balancers that automatically fail over. If the primary load balancer goes offline, your traffic can be redirected to the secondary one with minimal application downtime.
### **Smooth Upgrades**
Floating IPs aren't just for failover situations. You can also use them for application upgrades. For example, you can spin up a new Droplet, run the upgrades on the new Droplet, and then switch the flow of traffic to the new Droplet.
## **References**
[Floating IPs - Digital Ocean]: <https://www.digitalocean.com/blog/floating-ips-start-architecting-your-applications-for-high-availability>

[1] [Floating IPs - Digital Ocean]


