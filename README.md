# Storage VPS: What a Terabyte Costs, HDD vs RAID-10 SSD, and Which Plan Fits Backups, Nextcloud or Plex (Full Plan Table)

Cheap capacity in this market bottoms out around **€6.87 per TB per month**: YorkHost's 16 TB SAS plan at €109.99 monthly, no minimum term. SSD-backed storage VPS plans run $22 to $32 per TB at the rates Contabo prints on its storage page. SpinServers occupies a third position — its KVM VPS line starts at **$39.00/mo for 6 vCPU, 8 GB RAM, 120 GB RAID-10 SSD and 8 TB of monthly transfer on a 1 Gbps port**, which buys compute and bandwidth rather than bulk disk.

Below: every plan SpinServers currently lists for that line, the real cost per usable terabyte across the plans worth comparing, and the restrictions that only surface in provider FAQ pages — missing snapshots, fair-use throttling, upgrades that force a reinstall.

> **Quick pick.** Two terabytes or more of cheap disk for backups, archives or a media library? Buy an HDD-backed plan; SpinServers' VPS catalogue tops out at 500 GB of SSD and is not built for that job. Need a fast VM on a 1 Gbps port with 8–20 TB of monthly transfer and a few hundred GB of RAID-10 SSD for Nextcloud, a CI cache or a small app server? The 6 vCPU plan at $39/mo is the entry point. 👉 [See current SpinServers KVM VPS plans and prices](https://bit.ly/Spinservers)

## What "storage vps" actually covers

Two products get sold under the same name, and their prices are not comparable.

The first is a full virtual machine with a large SSD block device. Contabo describes its storage line as "a large SSD block device inside a full virtual machine with root access, sized for capacity rather than peak I/O throughput," and sells 300 GB to 1.4 TB of it. SpinServers' KVM plans belong here too, at 120 GB to 500 GB on RAID-10 SSD.

The second is HDD or distributed-storage capacity, where the disk is measured in terabytes and the IOPS are an afterthought. YorkHost ships 1 TB to 16 TB of enterprise SAS in RAID60; Onidel runs HDD behind Ceph up to 10 TB per server; RamNode sells 160 GB to 4 TB of spinning disk with 2 TB to 150 TB of monthly bandwidth attached.

Both HDD providers say the same thing in their own documentation. Onidel's FAQ: storage VPS is "ideal for backups, archives, and media libraries where capacity matters more than raw I/O speed," and databases are possible but not recommended because HDD latency is higher. YorkHost's FAQ tells customers with intensive random access to buy an SSD plan instead. A 16 TB HDD box and a 500 GB SSD box at similar monthly prices behave nothing alike under load.

## The five KVM plans SpinServers lists

| Plan | vCPU / RAM | Disk | Transfer & port | Price as displayed | Order |
| --- | --- | --- | --- | --- | --- |
| Simple Application Server | 6 vCPU / 8 GB DDR4 | 120 GB RAID-10 SSD | 8 TB/mo · 1 Gbps | $39.00/mo | [Order](https://bit.ly/Spinservers) |
| Simple Application Server | 8 vCPU / 8 GB DDR4 | 160 GB RAID-10 SSD | 10 TB/mo · 1 Gbps | Shown in cart | [Order](https://bit.ly/Spinservers) |
| Simple Application Server | 12 vCPU / 12 GB DDR4 | 160 GB RAID-10 SSD | 10 TB/mo · 1 Gbps | Shown in cart | [Order](https://bit.ly/Spinservers) |
| Simple Application Server (Intel Xeon) | 16 vCPU / 16 GB DDR4 | 320 GB RAID-10 SSD | 15 TB/mo · 1 Gbps | Shown in cart | [Order](https://bit.ly/Spinservers) |
| Advanced Application Server | 32 vCPU / 32 GB | 500 GB SSD | 20 TB/mo · 1 Gbps | Shown in cart | [Order](https://bit.ly/Spinservers) |

The product page prints two featured starting prices, $39.00/mo and $62.00/mo, and leaves the remaining three configurations to the order flow, so confirm the figure in the cart before you pay. Every plan includes one IPv4 and one IPv6 address and a 1 Gbps network port.

One operational detail matters if the box is going to send you backup-failure emails: **port 25 is closed by default on all of these VPS plans**. SpinServers opens it by ticket with a justification and reserves the right to refuse. Plan on using a relay or an external monitoring service instead of building alerts around local SMTP.

Read the specs column by column and the shape of the offer becomes clear. Transfer grows from 8 TB to 20 TB across the range while disk grows from 120 GB to 500 GB, and core count climbs from 6 to 32. This is a compute-and-bandwidth catalogue with SSD attached, priced for people running services, not for people hoarding files.

## Cost per terabyte, from verified plan pages

| Provider and plan | Disk | Price | Per TB / month |
| --- | --- | --- | --- |
| YorkHost STOR-16T | 16 TB SAS RAID60 | €109.99/mo | €6.87 |
| YorkHost STOR-1T | 1 TB SAS RAID60 | €9.99/mo | €9.99 |
| RamNode 4000 GB | 4 TB HDD | $64/mo | $16.00 |
| RamNode 160 GB | 160 GB HDD | $4/mo | $25.00 |
| Contabo Storage VPS 10 | 300 GB SSD | $6.60/mo displayed | $22.00 |
| Contabo Storage VPS 50 | 1.4 TB SSD | $44.50/mo displayed | $31.79 |
| SpinServers 6 vCPU | 120 GB RAID-10 SSD | $39.00/mo | $325.00 |

Two readings of that table.

In HDD territory, capacity gets cheaper as it grows, every time. YorkHost drops from €9.99 to €6.87 per TB between 1 TB and 16 TB; RamNode drops from $25 to $16 between 160 GB and 4 TB. If your requirement is measured in terabytes, buying the largest plan you can justify is the cheaper move per unit.

Contabo breaks that pattern because its storage plans carry real compute: 14 vCPU and 50 GB RAM ride along with the 1.4 TB, so the top plan costs more per terabyte than the 300 GB one. SpinServers is the extreme version of the same logic at $325 per TB on the entry plan. Nobody should buy it as a per-terabyte purchase; the honest use case is a workload that needs cores, a 1 Gbps port and a large monthly transfer allowance, where 120 GB of RAID-10 SSD is enough room to work in.

One caution on Contabo's figures: the same page shows $6.60 against Storage VPS 10 and a footnote saying the displayed price is the effective monthly rate for a 24-month subscription including taxes. Both cannot be true at once, so treat those numbers as indicative and check the checkout total.

## How the three main storage VPS options compare

| Provider | Storage type and range | Top-end compute | Transfer | Snapshots / backups |
| --- | --- | --- | --- | --- |
| Contabo Storage VPS | SSD, 300 GB – 1.4 TB | 14 vCPU / 50 GB at 1.4 TB | "Unlimited", fair use applies | None: no snapshots, no auto-backup add-on, no storage extension on this family |
| YorkHost | SAS RAID60, 1 – 16 TB (200 GB and 400 GB tiers ship as SSD or HDD depending on the server) | 6 vCPU / 24 GB at 16 TB | 1–10 Gbps, fair use | None |
| RamNode | HDD, 160 GB – 4 TB | 4 vCPU / 12 GB at 4 TB | 2 TB – 150 TB/mo | Not stated on the plan page |

Add Onidel on the durability side: HDD behind Ceph, three replicas across separate nodes, self-healing and checksum scrubbing, with a provider-stated 99.999999% durability figure. Its own FAQ is explicit that triple replication protects against hardware failure and is "not a replacement for backups." Replication is not a backup on any of these platforms.

## Limits that live in the FAQ, not the pricing table

- **No snapshot or backup on the storage tiers.** Contabo's documentation lists snapshots for Core and Performance VPS and dashes for Storage VPS, with no auto-backup add-on either. YorkHost states plainly that backups and snapshots are not included. If your data only exists on the storage box, you have one copy.
- **"Unlimited" traffic has a throttle behind it.** Contabo meters inbound as unlimited and unmetered, and describes outbound as unlimited under a fair-use policy, reserving the right to throttle servers with exceptionally high or disruptive usage, with email notice first. YorkHost labels its 1–10 Gbps network as fair use too.
- **Upgrade paths cost different amounts.** Contabo upgrades in place within a family and keeps the IP, but has no direct downgrade (new smaller server, manual migration, IP changes), no conversion between Core, Performance and Storage families, and an SSD-to-NVMe move means a reinstall that erases everything. YorkHost lets you add disk in 1 TB increments above 1 TB without reinstalling, and RAM at €4.00/GB/month.
- **Large HDD plans are not instant.** YorkHost notes that provisioning for 1 TB and above may take several hours.
- **HDD is the wrong disk for a database.** Both HDD providers say so directly. Nextcloud with a handful of users is fine on HDD; Nextcloud with a busy database behind it is not.

## Which plan to order

Work down this list until one line matches your situation.

1. **2 TB or more of cold data** — backups, restic or borg targets, archives, a Plex or Jellyfin library. Buy the largest HDD plan you can afford; per-TB cost falls as capacity rises, and 4 TB to 16 TB is available for €6.87 to $16 per TB per month.
2. **100–500 GB of fast disk with a big pipe** — Nextcloud for a team, a CI artefact cache, a Docker registry, a log store, an app server that also serves large files. SpinServers' 6 vCPU plan at $39/mo with 8 TB of transfer covers the low end; step up to the 16 vCPU or 32 vCPU configurations when 15–20 TB of transfer or more cores matter. 👉 [Compare all five KVM configurations](https://bit.ly/Spinservers)
3. **Both at once** — put the application on an SSD VPS and point its backups at a separate HDD box. YorkHost makes the same argument in its own FAQ, and it removes the single-copy risk that comes with storage plans that include no snapshots.
4. **You need snapshots before you go live** — ask support first. The SpinServers VPS page does not advertise snapshot or backup features, so confirm what is available on the plan you pick rather than assuming.

Two things to settle before you enter payment details. Check the cart total against the featured price, since three of the five configurations only show their price at that step. And decide now whether 120 GB or 500 GB is your real ceiling: the VPS catalogue ends at 500 GB, and upgrading later means moving to a bigger plan in the same line rather than attaching another disk.

If your answer was line 2, the 6 vCPU plan is the cheapest way into a 1 Gbps port and 8 TB of monthly transfer with RAID-10 SSD underneath. 👉 [Open the SpinServers order page and confirm the current plan price](https://bit.ly/Spinservers)
