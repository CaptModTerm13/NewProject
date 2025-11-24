# DRAM

## Introduction
Dynamic Random Access Memory (DRAM) is a volatile semiconductor memory technology that stores each bit of data using a **single transistor and a capacitor** (1T cell). Due to inherent charge leakage in capacitors, DRAM requires **periodic refreshing**, which is why it is called *dynamic*.

Compared to SRAM, DRAM offers:
- **Higher density**
- **Lower cost**
- **Lower speed** (due to refresh and charge‑based operation)

DRAM is widely used in systems requiring large memory arrays.

---

## Synchronous DRAM (SDRAM)
SDRAM is a DRAM architecture that operates **synchronously with a system clock** and requires a specialized **memory controller** to manage:
- Initialization
- Row/Column addressing
- Read/Write activation
- Refresh cycles
- Timing constraints

### Common SDRAM Variants
- **DDR SDRAM** – Used in computer systems; transfers data on both clock edges
- **LPDDR** – Low‑power DRAM for mobile devices
- **GDDR** – High‑speed DRAM for GPUs and parallel computing
- **HBM** – High Bandwidth Memory used in AI accelerators for extreme throughput

---

## DRAM Cell Structure
A DRAM bit‑cell consists of:
- **Access Transistor (NMOS)** – Controlled by the *Word Line (WL)*
- **Storage Capacitor** – Holds the charge representing a logic 1 or 0

**Word Line (WL):** Horizontal line that selects an entire row.

**Bit Line (BL):** Vertical line used for reading and writing data to cells in the column.

<img width="291" height="173" alt="image" src="https://github.com/user-attachments/assets/a9b0322c-09d2-47ec-baf6-9e5383193e6a" />


---

## DRAM Operations
DRAM supports two primary operations: **Write** and **Read**.

### Write Operation
#### Writing a '1'
1. Enable WL (turn on access transistor)
2. Drive Bit Line to **VDD**
3. Capacitor charges to **VDD**

#### Writing a '0'
1. Enable WL
2. Drive Bit Line to **0V**
3. Capacitor discharges to Bit Line level

---

## Read Operation
DRAM uses **sense amplifiers** to detect small voltage changes.

### Steps
1. Precharge Bit Line to **VDD/2**
2. Enable Word Line
3. Charge sharing occurs:
   - If capacitor = **VDD** → BL voltage slightly increases
   - If capacitor = **0V** → BL voltage slightly decreases
4. Sense amplifier detects and amplifies this change, interpreting logic 0/1

### Charge Sharing
During read, the capacitor's charge redistributes with the Bit Line. This disturbs its original state.

### Destructive Read
Since reading alters the stored charge, DRAM reads are **destructive**. After sensing:
- If sense amplifier detects **1**, BL is driven to logic 1
- If sense amplifier detects **0**, BL is driven to logic 0

This restores the original data — a process called **refreshing**.

---

## DRAM Refresh
Example specification:
- Total rows: **4096**
- All rows refreshed every **64 ms**
- Each row refresh period: **15.62 µs**

### Types of Refresh
1. **Auto Refresh** – Performed automatically during normal SDRAM operation
2. **Self Refresh** – Used in low‑power mode; SDRAM refreshes itself without controller intervention

---

## Summary
DRAM is a fundamental memory technology using charge storage, with high density and low cost. Its operation relies on controlled access, charge sensing, and periodic refreshing to maintain data integrity. SDRAM architectures further enhance performance through clock‑synchronous operation and advanced memory management features.
