# VLSM-New-Warehouse

<img width="800" alt="image" src="https://github.com/user-attachments/assets/e7d880d1-99cb-43ca-a11c-1bb5f0fac2cf">

------

### Given IP Address

The ISP has provided the following IP block:

- **Network Address:** 172.21.42.0/24
- **IP Address (Binary):**  10101100.00010101.00101010.00000000 → 172.21.42.0
- **Subnet Mask (Binary):** 11111111.11111111.11111111.00000000 → 255.255.255.0 (/24)

---

## 💡 Network Requirements

We need to create **4 networks** to support the following host requirements:

| Network | Required Hosts |
|---------|----------------|
| Guest   | 10             |
| Robots  | 57             |
| Servers | 26             |
| Workers | 117            |

>  When performing VLSM, **always start with the largest host requirement**.

------
## 👷 Workers Network | 117 Hosts

**Step 1:** Use the Nosferatz chart to calculate how many host bits we need to hack to meet the 117 hosts requirement


```
            1   | 0     0    0    0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |

> We need to keep 7 hosts bit to meet 117 hosts requirement (total usable hosts 126)
----
**Step 2:** Hack the Host Bits

**Original Subnet Mask (Binary):**  

11111111.11111111.11111111.00000000 = 255.255.255.0 (/24)


**New Subnet Mask After hacking 1 Bits:**

11111111.11111111.11111111.1|0000000 = 255.255.255.128 (/25)

-----
**Step 3:** Find the Increment: Use the chart to calculate the increment:

> By using the last hacked increment we can determine the size of each network block and what the ranges are.

**The increment is 128** (Subtract 1)

172.21.42.0 + 127 = **172.21.42.127**
 
**IP Range:** `172.21.42.0 /25 – 172.21.42.127 /25`  

**Next Available Address:** `172.21.42.128 /25 – ?`

-------
## 🤖 Robots Network | 57 Hosts

**Now we need to create the Robots network to meet the 57 host requirements** 

> Using the IP Address:  172.21.42.128 /25


**Step 1:** Use the Nosferatz chart to calculate how many host bits we need to hack to meet the 57 hosts requirement

```
            1     1  |  0    0    0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |

> We need to keep 6 hosts bit to meet 57 hosts requirement (total usable hosts 62)

----
**Step 2:** Hack the Host Bits

**Original Subnet Mask (Binary):**  

11111111.11111111.11111111.1|0000000 = 255.255.255.128 (/25)


**New Subnet Mask After hacking 2 Bits:**

11111111.11111111.11111111.11|000000 = 255.255.255.192 (/26)

-----

**Step 3:** Find the Increment: Use the chart to calculate the increment:

**The increment is 64** (Subtract 1)

172.21.42.128 + 63 = **172.21.42.191**

**IP Range:** `172.21.42.128 /26 – 172.21.42.191 /26`  

**Next Available Address:** `172.21.42.192 /26 – ?`

----

-------
## 🖥️ Servers Network | 26 Hosts

**Now we need to create the Servers network to meet the 26 host requirements** 

> Using the IP Address:  172.21.42.192 /26


**Step 1:** Use the Nosferatz chart to calculate how many host bits we need to hack to meet the 26 hosts requirement

```
          1     1       1  |  0    0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |

> We need to keep 5 hosts bit to satisfy 26 hosts requirement (total usable hosts 30)

-----

**Step 2:** Hack the Host Bits

**Original Subnet Mask (Binary):**  

11111111.11111111.11111111.11|000000 = 255.255.255.192 (/26)


**New Subnet Mask After hacking 3 Bits:**

11111111.11111111.11111111.111|00000 = 255.255.255.224 (/27)

-----

**Step 3:** Find the Increment: Use the chart to calculate the increment:

**The increment is 32** (Subtract 1)

172.21.42.192 + 31 = **172.21.42.223**

**IP Range:** `172.21.42.192 /27 – 172.21.42.223 /27`  

**Next Available Address:** `172.21.42.224 /27 – ?`

----


-------
## ✅ Guest Network | 10 Hosts

**Now we need to create the Guest network to meet the 10 host requirements** 

> Using the IP Address: 172.21.42.224 /27


**Step 1:** Use the Nosferatz chart to calculate how many host bits we need to hack to meet the 26 hosts requirement

```
          1     1       1     1   | 0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |

> We need to keep 4 hosts bit to satisfy 10 hosts requirement (total usable hosts 14)

-----

**Step 2:** Hack the Host Bits

**Original Subnet Mask (Binary):**  

11111111.11111111.11111111.111|00000 = 255.255.255.224 (/27)


**New Subnet Mask After hacking 4 Bits:**

11111111.11111111.11111111.1111|0000 = 255.255.255.240 (/28)

-----

**Step 3:** Find the Increment: Use the chart to calculate the increment:

**The increment is 16** (Subtract 1)

172.21.42.224 + 15 = **172.21.42.239**

**IP Range:** `172.21.42.224 /28 – 172.21.42.239 /28`  

**Next Available Address:** `172.21.42.240 /27 – ?` = we have more space to make more network, but we only need 4 networks for this warehouse.

-----

## 📊 Final Subnet Allocation (VLSM)

| Network  | IP Range                        | CIDR | Usable Hosts |
|----------|----------------------------------|------|--------------|
| Workers  | `172.21.42.0 – 172.21.42.127`    | /25  | 126          |
| Robots   | `172.21.42.128 – 172.21.42.191`  | /26  | 62           |
| Servers  | `172.21.42.192 – 172.21.42.223`  | /27  | 30           |
| Guest    | `172.21.42.224 – 172.21.42.239`  | /28  | 14           |

---
















