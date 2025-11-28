# 🕵️‍♂️ Network Packet Sniffer (Python + Scapy)

This project is a lightweight **network packet sniffer** built using Python and the **Scapy** library.  
It captures live network traffic and displays essential details like source/destination IPs, ports, protocol types, and a preview of the payload.

---

## 🚀 Features

✅ Real-time packet capture  
✅ Supports IPv4, IPv6, TCP, UDP, and ICMP  
✅ Shows timestamps, source/destination, and payload preview  
✅ Memory-safe continuous sniffing

---

## 🧠 Example Output

```
[2025-11-04 15:30:12.354] TCP 192.168.1.10:51522 -> 142.250.190.68:443 | len=74 bytes | payload_preview='GET / HTTP/1.1\r\nHost: www.google.com\r\n...'
```

---

## 🧩 Requirements

- Python 3.x
- Scapy library

Install dependencies:

```bash
pip install scapy
```

---

## ▶️ Usage

Run:

```bash
python src/packet_sniffer.py
```

> 💡 You may need to run as **administrator** (Windows) or with `sudo` (Linux/Mac) for network access.

Stop capture anytime with `Ctrl + C`.

---

## ⚙️ Configuration

You can change capture settings in the script:

| Variable              | Description                                     | Default |
| --------------------- | ----------------------------------------------- | ------- |
| `PACKET_COUNT`        | Number of packets to capture (`0` = continuous) | 0       |
| `PAYLOAD_PREVIEW_LEN` | Max characters to show from payload             | 160     |

---

## 🛡️ Disclaimer

This project is for **educational and ethical** use only.  
Do **not** capture or inspect packets on networks you don’t own or have permission to monitor.

---

## 👨‍💻 Author

**Umed Ali**  
🎓 BS Cyber Security | 💻 Network Security Enthusiast  
📍 Karachi, Pakistan  
🔗 [LinkedIn](https://www.linkedin.com/in/ecstaticumed)

---

## 🏷️ License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.
