        [Internet]
            │
   [pfSense + Proxmox]
 (Supermicro w/ ConnectX-3)
            │
      [Dell 1Gb Switch]
        ├──────┬────────────┐
        │      │            │
   [TP-Link] [Desktop] [10Gb Trunk]
                        ↓
                [Mellanox SX6036 56gb]
        ┌────────────┬────────────┐
        ↓            ↓            ↓
 [Dell 720XD #1] [Dell 720XD #2] [Supermicro AI Server]
    (2PB JBOD)     (Media, VMs)     (8x GPUs)
