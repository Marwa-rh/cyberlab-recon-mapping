# Building a Dual-Subnet Enterprise Network in Packet Tracer

Hey! 👋 This is a hands-on Cisco Packet Tracer project where I designed, configured, and tested a small enterprise network topology from scratch. 

My main goal was to set up inter-subnet routing, deploy basic DNS and HTTP services, and practice network reconnaissance commands from a host machine to map out the environment.

---

## 📐 Network Layout

The project connects two separate subnets through a pair of Cisco 2911 routers over a point-to-point WAN link[cite: 1]:

* **User LAN (`192.168.10.0/24`)**: Workstations (`PC-ANALYSTE` and `PC-USER`)[cite: 1].
* **Server LAN (`192.168.30.0/24`)**: Core infrastructure (`DNS-SERVER` and `WEB-SERVER`)[cite: 1].
* **WAN Link (`10.0.0.0/30`)**: Router-to-router point-to-point connection (`R1` ↔ `R2`)[cite: 1].



## ⚡ What I Configured

1. **IP & Host Setup**: Configured static IP addresses, default gateways, and DNS server pointers across endpoints[cite: 1].
2. **Cisco IOS CLI**: Configured interface IP addresses on both routers (`R1` and `R2`) and enabled them[cite: 1].
3. **Static Routing**: Added static routes on both routers to allow cross-subnet communication[cite: 1]:
   * **R1**: `ip route 192.168.30.0 255.255.255.0 10.0.0.2`[cite: 1]
   * **R2**: `ip route 192.168.10.0 255.255.255.0 10.0.0.1`[cite: 1]
4. **Services**: Added an A Record on the DNS server mapping `www.entreprise.local` to `192.168.30.20` and hosted a custom webpage on the Web Server[cite: 1].

---

## 🔎 Testing & Network Reconnaissance

To verify everything worked, I tested the network from `PC-ANALYSTE` using built-in CLI diagnostic tools[cite: 1]:

* **`ipconfig`**: Verified local IP and gateway settings[cite: 1].
* **`arp -a`**: Inspected local MAC address discovery on the local switch segment[cite: 1].
* **`ping`**: Tested end-to-end reachability across gateways and remote servers[cite: 1].
* **`tracert`**: Watched packets hop through `192.168.10.1` ➔ `10.0.0.2` ➔ `192.168.30.20`[cite: 1].
* **`nslookup`**: Verified domain name resolution for `www.entreprise.local`[cite: 1].
* **`netstat`**: Observed active TCP connections while opening the site in the web browser[cite: 1].

---

## 🛠️ How to Open
1. Download `network-recon-lab.pkt`.
2. Open it in **Cisco Packet Tracer (v8.0+)**[cite: 1].
3. Run diagnostic commands from `PC-ANALYSTE` or inspect device configs in `/configs`[cite: 1]!
