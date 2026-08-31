# Low-Level Linux Kernel & Network Tuning Cheat-Sheet

A comprehensive guide for tuning the Linux kernel, network socket buffers, and memory subsystems for high-throughput homelab hypervisors (Proxmox VE, K3s, Ceph, and NVMe-oF).

---

## 1. TCP Socket Buffer Autotuning (10GbE / High BDP)

Standard Linux socket buffer defaults cause packet drops during multi-gigabit bursts. To achieve maximum throughput without micro-burst queue loss, expand socket memory boundaries:

```ini
# /etc/sysctl.d/99-lowlevel-tuning.conf

# Maximum Socket Receive and Send Buffer Sizes (64MB)
net.core.rmem_max = 67108864
net.core.wmem_max = 67108864
net.core.rmem_default = 33554432
net.core.wmem_default = 33554432

# TCP Memory Window (min, default, max in bytes)
net.ipv4.tcp_rmem = 4096 87380 67108864
net.ipv4.tcp_wmem = 4096 65536 67108864

# Maximum Network Ingress Backlog Queue
net.core.netdev_max_backlog = 300000
net.core.somaxconn = 65535
```

---

## 2. TCP Congestion Control (BBR + FQ)

BBR (Bottleneck Bandwidth and RTT) optimizes throughput over high-speed networks by preventing bufferbloat:

```bash
# Load TCP BBR module
sudo modprobe tcp_bbr

# Set Fair Queueing packet scheduler and BBR algorithm
sudo sysctl -w net.core.default_qdisc=fq
sudo sysctl -w net.ipv4.tcp_congestion_control=bbr

# Verify active algorithm
sysctl net.ipv4.tcp_congestion_control
```

---

## 3. Virtual Memory & Storage Write Flushing

Prevent sudden I/O pauses on fast NVMe/SATA storage by keeping dirty pages flushing in continuous small increments:

```ini
# Start background writeout when 5% of memory is dirty
vm.dirty_background_ratio = 5

# Force synchronous writeout when 10% of memory is dirty
vm.dirty_ratio = 10

# Proactive memory page compaction to prevent memory fragmentation
vm.compaction_proactiveness = 50

# Minimum free memory reserved for kernel networking allocations
vm.min_free_kbytes = 1048576
```

---

## 4. Applying and Persisting Changes

```bash
# Verify configuration syntax
sudo sysctl --system

# Check active socket limits live
cat /proc/sys/net/core/rmem_max
cat /proc/sys/net/ipv4/tcp_congestion_control
```
