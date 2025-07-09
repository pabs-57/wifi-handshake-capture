# 🔐 Wi-Fi Handshake Capture Lab

This lab demonstrates how to capture WPA/WPA2 handshakes using `hcxdumptool` and prepare the captured hashes for cracking with `hashcat`.

---

## 🎯 Objective

Capture WPA2 handshakes from nearby networks using a wireless adapter in monitor mode and convert them into a format that can be used for offline password cracking.

---

## 🛠 Tools Used

- Kali Linux
- Alfa AWUS036ACM (MT7612U)
- `hcxdumptool`
- `hcxpcapngtool`
- `hashcat`

---

## 🧪 Steps

1. **Enable monitor mode** on the Alfa adapter:
   ```bash
   ip link set wlan0 down
   iw dev wlan0 set type monitor
   ip link set wlan0 up
# wifi-handshake-capture
/wifi-handshake-capture/README.md

2. **Capture handshakes** with `hcxdumptool`:
   ```bash
   hcxdumptool -i wlan0 -o capture.pcapng --enable_status=15 --active_beacon

 3. **Convert to Hashcat format*
     hcxpcapngtool -o handshake.hccapx capture.pcapng

 4. **Crack using hashcat
      hashcat -m 22000 handshake.hccapx /path/to/wordlist.txt
---

## ✅ Result

Successfully captured a WPA2 handshake in a controlled test network. The password was cracked using a known value from the wordlist.

---

## 📁 Files

- `capture.pcapng`: Raw capture
- `handshake.hccapx`: Converted hash file
- `crack-output.txt`: Example hashcat output



