🧩 Infrastructure Components

🔧 Core Networking
	•	pfSense router and firewall virtualized on Proxmox (Supermicro)
	•	ConnectX-3 NIC for WAN/LAN split and trunking
	•	Dell 1Gb switch for basic client + WiFi connectivity
	•	Mellanox SX6036 10Gb Infiniband switch for backend server interconnects
	•	TP-Link Deco mesh for wireless

🖥️ Compute + Storage
	•	Proxmox on all servers, with:
	•	LXC containers (Media, Linux services)
	•	Ubuntu VMs
	•	Windows Server and Win11 for testing
	•	Dell R720XD #1: Direct-attached 2x 60-bay JBODs (~2PB) via HBA
	•	Dell R720XD #2: General workloads, media server, backups
	•	Supermicro AI server: 8x GPUs for AI training workloads
	•	Desktop: Orchestration and local access
	•	Tailscale VPN: Mesh access to Mac Mini, VPSs, phone, remote Linux systems (Helium monitoring)
