## 🖥️ Core Objectives

- Test and develop hybrid infrastructure solutions
- Train and benchmark AI models with GPU servers
- Maintain large-scale, high-throughput storage for media and data-intensive workloads
- Provide zero-trust remote access to distributed systems (including Helium nodes)
- Continuously improve my skills in Linux, networking, automation, and virtualization

---

## 🧩 Hardware Stack

| Device                  | Role                                   |
|------------------------|----------------------------------------|
| Supermicro (Proxmox)   | pfSense firewall, internet gateway, nginx     |
| Dell 1Gb Switch         | Layer 2 distribution to WiFi + Desktop |
| TP-Link Deco Mesh      | Wireless access for home + IoT devices |
| Mellanox SX6036        | 10GbE/40gbe backbone switch                  |
| Dell R720XD #1         | JBOD host (2x 60-bay, ~2PB total)      |
| Dell R720XD #2         | Media server, backups, VM host         |
| Supermicro (8x GPU)    | AI/ML workloads, training environment   |
| Desktop (Win11)        | Orchestration + management             |
| Mac Mini, VPS, Phone   | Remote devices via Tailscale VPN       |

---

## 🛠️ Virtualization Stack

- **Proxmox VE** on all nodes
- **Ubuntu** as the primary VM OS
- **LXC containers** for Media, DevOps tools, sysadmin services
- **Windows Server & Windows 11** test environments
- **AI Workloads** run inside Ubuntu VMs with Docker + CUDA

---

## 🧱 Storage Layout

- 2x Dell 60-bay JBODs (~2PB) directly attached via HBA to R720XD #1
- Media content and daily snapshots backed up to R720XD #2
- ZFS used for data integrity and snapshots

---

## 🛡️ Network & Access

- **pfSense** handles WAN, LAN, VLANs, DNS, DHCP
- **Tailscale** provides secure remote access across devices
- VLANs isolate traffic (Management, Storage, AI, Media, Remote Access)
- Management via Proxmox Web UI + SSH

---

## 🧪 Use Cases

- Infrastructure prototyping
- Script development + automation (Bash, Python)
- AI experimentation (text, vision models)
- Storage benchmarking
- Homelab documentation for GitHub

---

## 🔗 Future Plans

- Deploy Kubernetes across GPU + storage nodes
- Implement Grafana/Prometheus for advanced monitoring
- Publish Terraform modules for full infrastructure replication
- Public GitHub repo for open-source homelab playbooks
