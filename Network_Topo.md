Network Diagram

                               [Internet]
                                   │
                            [pfSense + Proxmox]
                      (Supermicro w/ ConnectX-3)
                       VLAN 40: 192.168.40.0/24
                                   │
                          [Dell 10Gb/1Gb Switch]
                                   │
            ┌────────────┬─────────┴───────────┐
            │            │                     │
        [TP-Link]   [Desktop PC]       [10Gb Trunk Link]
         (WiFi)     (192.168.40.50)           │
                                              │
                                  [Mellanox SX6036 40Gb]
                    VLAN 40: 192.168.40.0/24 (Backbone Fabric)
                 ┌──────────────┬──────────────┬──────────────┐
                 │              │              │
      [Dell 720XD #1]   [Dell 720XD #2]   [Supermicro AI Server]
   (2PB JBOD, .10)   (VMs, Media, .11)   (8x GPUs, .12 Compute)
