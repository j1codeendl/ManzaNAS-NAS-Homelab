# ManzaNAS Troubleshooting Log

This document records technical issues encountered during the deployment and operation of ManzaNAS.

## 1. Troubleshooting Method

For each issue, the following approach is used:
1. Identify the symptoms.
2. Gather relevant information.
3. Investigate possible causes.
4. Apply an appropriate troubleshooting step.
5. Verify whether the issue was resolved.
6. Document the result.

## 2. Issue Log

### Issue 1: Total Network Lockout & "State DOWN"

**Symptoms:**
Both `eno1` (Ethernet) and `wlo1` (Wi-Fi) adapters dropped to `state DOWN`. The system lost its IP address, and the OMV web interface became completely unreachable.

**Investigation:**
Checked physical connections. Ran `ip a` on the laptop terminal, confirming no `inet` address was assigned. 

**Root Cause:**
Accidentally deleting the network setup in the OMV web interface wiped the underlying Debian configuration files. Additionally, enabling IPv6 erroneously caused a router conflict.

**Resolution:**
1. Connected a physical Ethernet cable.
2. Logged into the physical laptop terminal as `root`.
3. Flushed broken configurations: `ip addr flush dev eno1`
4. Woke the hardware: `ip link set eno1 up`
5. Injected a temporary IP address to force a backdoor: `ip addr add 192.168.1.113/24 dev eno1`
6. Accessed the web UI at `192.168.1.113`, corrected the interface to DHCP (IPv4) and Disabled (IPv6), and applied changes. Ran `omv-firstaid` in the terminal as a secondary fix.

**Verification:**
Rebooted the system and ran `ip a`. `eno1` showed `state UP` with a permanent IP address.

---

### Issue 2: Error 503 Software Failure Upon Network Apply

**Symptoms:**
Applying network changes using the yellow banner in the OMV web interface resulted in a black screen stating: "Software Failure. Press left mouse button to continue. The server is unavailable to handle this request right now."

**Investigation:**
Reviewed OMV documentation regarding network setting applications.

**Root Cause:**
Normal behavior. Applying core network interface changes forces OMV to restart its own background web server service (`nginx`), temporarily breaking the connection to the browser.

**Resolution:**
Cleared the address bar and navigated to the newly assigned IP address. 

**Verification:**
The OMV blue login screen loaded successfully on the new IP.

---

### Issue 3: HP Laptop Wi-Fi "Warm Boot Bug" (Hardware Hiding)

**Symptoms:**
After issuing a standard `reboot` command, the Wi-Fi interface (`wlo1`) completely vanished from the network list. Running `ip link` only showed `lo` and `eno1`. The static IP `192.168.x.x` could not load.

**Investigation:**
Verified the physical Wi-Fi button. Checked `ip link`.

**Root Cause:**
Hardware quirk with the HP motherboard and Linux Wi-Fi drivers. A soft "Warm Boot" (`reboot`) does not completely cut electrical power to the Wi-Fi chip. If the driver crashes, the chip remains in a frozen state and fails to initialize during startup.

**Resolution (Permanent Operational Procedure):**
Avoid standard reboots. Always perform a "Cold Boot":
1. Run `poweroff` in the terminal.
2. Wait for the laptop to completely shut down and the screen to go black.
3. Wait an additional 10 seconds to allow all residual motherboard electricity to drain from the Wi-Fi chip.
4. Press the physical power button to boot.

**Verification:**
Upon booting from a completely powered-off state, `ip link` detected `wlo1`, and the system successfully applied the static IP (`192.168.x.x`).

## 3. Known Limitations

- Hardware requires a strict Cold Boot protocol if restarted.
- No automated backup implementation.
- No remote access configuration.
- Limited hardware resources due to the repurposed laptop.

## 4. Future Troubleshooting and Maintenance

Potential maintenance activities include:
- Monitoring storage capacity.
- Checking system resource usage.
- Reviewing user permissions.
- Monitoring HDD health using appropriate tools.

---

**Project Name:** ManzaNAS  
**Project Type:** Personal IT HomeLab  
**Purpose:** Hands-on learning in system administration, networking, and IT infrastructure.
