# 🕵️ Email Harassment PCAP Analysis at Nitroba University

This repository contains a detailed forensic investigation into an email harassment case that took place over the Nitroba State University dorm network. The case was solved using packet analysis techniques and Wireshark, identifying the perpetrator and reconstructing the timeline of events.

## 📄 Report Summary

**Case**: Harassment via anonymous email services  
**Victim**: Lily Tuckrige (Chemistry Instructor)  
**Perpetrator Identified**: Johnny Coach (CHEM109 Student)  
**Tools Used**: Wireshark, manual inspection, packet filtering

Two harassing emails were sent through anonymous services (`sendanonymousemail.net` and `willselfdestruct.com`). Network traffic captured in `nitroba.pcap` was analyzed to trace these emails back to a single internal IP and MAC address. Correlation with a Gmail session led to a conclusive identification of the attacker.

## 🧪 Investigation Techniques

The investigation used several Wireshark filters and steps:
- `ip.addr == 140.247.62.34` to trace NAT activity
- `http.host contains "willselfdestruct.com"` to identify the second harassing message
- `eth.src == 00:17:f2:e2:c0:ce && http.request.method == "POST"` to find POSTs
- DNS request timeline reconstruction
- TCP stream and HTTP payload analysis

## 🔍 Key Evidence

| Time (PST) | Action | Packet | Notes |
|------------|--------|--------|-------|
| 11:01 AM   | Gmail login | ~#79000 | Revealed session for `jcoachj@gmail.com` |
| 11:02 AM   | First harassment email sent | #80614 | Via `sendanonymousemail.net` |
| 11:04 AM   | Second harassment email sent | #83601 | Via `willselfdestruct.com` |
| 11:09 AM   | File transfer on Yahoo | - | Possibly irrelevant |

**All actions originated from:**
- Internal IP: `192.168.15.4`
- MAC Address: `00:17:f2:e2:c0:ce`
- Gmail Account: `jcoachj@gmail.com`

## 📚 Contents

- `AbdulRafay-report.pdf`: Full incident report with step-by-step analysis

## ✅ Outcome

Johnny Coach was conclusively identified as the source of both harassment emails. The findings were based on MAC address tracing, HTTP POST data, and Gmail session evidence.

## 🔐 Recommendations

- Enforce secured Wi-Fi (e.g., WPA2) in dorms
- Monitor POST traffic to anonymizing sites
- Educate students on ethical internet behavior
- Implement proper logging & intrusion detection

---

### 📌 Author

**Abdul Rafay**   
📅 Report Date: August 2nd, 2025

---

### 📁 License

This project is for educational and academic purposes only.
