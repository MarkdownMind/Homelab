
# 💾 Homelab Backup Strategy

This document outlines the backup policies, tools, and configurations in place to protect critical data across the homelab. It’s optimized for high-capacity storage, snapshot-based recovery, and off-site access — suitable for both infrastructure and media workloads.

---

## 🗂️ Backup Objectives

- Ensure data redundancy for critical services and VMs
- Enable quick restoration of Proxmox containers and virtual machines
- Maintain long-term archive of media assets
- Isolate backup traffic from production VLANs
- Provide disaster recovery across sites via Tailscale

---

## 🧱 Infrastructure

| Component               | Role                              |
|------------------------|-----------------------------------|
| Dell R720XD #2         | Primary backup host               |
| ZFS on R720XD #2       | Snapshot and integrity layer      |
| JBODs on R720XD #1     | Cold storage + archival target    |
| Tailscale VPN          | Remote backups & sync             |

---

## 🔄 Backup Flow

1. **Proxmox VMs & Containers**
   - Backed up nightly using Proxmox `vzdump`
   - Compressed and stored locally on R720XD #2
   - Weekly sync to JBODs (cold storage)

2. **Media Content**
   - Synced using `rsync` with checksum validation
   - Media containers mount source and backup volumes via NFS

3. **Configuration Files**
   - Proxmox config `/etc/pve` backed up via cron to backup server
   - pfSense config exported weekly and versioned

4. **Tailscale Nodes**
   - Secure connection enables backups of remote VPS and Mac Mini
   - Backups pulled to R720XD #2 nightly via `rsync` over Tailscale

---

## 🧪 Snapshot Strategy (ZFS)

- Hourly snapshots retained for 24 hours
- Daily snapshots retained for 14 days
- Weekly snapshots retained for 2 months
- Monthly snapshots retained for 6 months

---

## 🔐 Security

- Encrypted volumes for sensitive data
- VLAN 20 isolates backup traffic from rest of network
- Backup logs sent to syslog + monitored with lightweight script

---

## 🛠️ Tools Used

- `vzdump` (Proxmox)
- `zfs-auto-snapshot`
- `rsync` with `--checksum`
- Cron jobs for automation
- Tailscale VPN mesh
- `duplicacy` (planned for encrypted remote snapshots)

---

## 📌 Future Enhancements

- Off-site replication to cloud or remote datacenter via rclone
- BorgBackup or Restic for deduplicated encrypted archives
- Prometheus monitoring with backup job success metrics
