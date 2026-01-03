# OPERATION ROADRUNNER — SOC playbook 

Date: 2026-01-02  
TLP: AMBER

Immediate (first 15 minutes)
- Block outbound to 76.250.68.175.
- Alert on outbound to ports 39586 and 47862.
- Hunt for GUID 46d25f419b884be338 and SHA256 5e8987a1d1fbfcec...

Top IOCs
- SHA256: 5e8987a1d1fbfcecce443fcbdf133af5aa14dd4217ed6ed501c7282e4ebe834c
- MD5: 28a9a1f512da3e7bd4d67cf64e7b4e99
- GUID (hex): 46d25f419b884be338
- C2: 76.250.68.175 (AS20115)
- Ports: 39586/tcp, 47862/tcp

Immediate commands (copy/paste)
- Firewall block:
  iptables -A OUTPUT -d 76.250.68.175 -j DROP
  iptables -A OUTPUT -p tcp --dport 39586 -j DROP
  iptables -A OUTPUT -p tcp --dport 47862 -j DROP

- Splunk hunt:
  index=firewall (dest_ip="76.250.68.175" OR dest_port IN (39586,47862))
  | stats count by src_ip,dest_ip,dest_port, _time

- Endpoint grep:
  grep -R "46d25f419b884be338" /var/log || true

Short (1–48 hours)
- Deploy roadrunner_yara.yar to memory and disk images.
- Run operation_roadrunner_sigma.yml in SIEM; triage top hits.
- Snapshot and isolate any compromised hosts before remediation.

Medium (48 hours – 2 weeks)
- Network retrospective over last 30 days for public IP list in c2_infrastructure_report.md.
- Rotate exposed credentials.
- Aggregate sandbox summaries and update detection rules.

Detection artifacts
- YARA: roadrunner_yara.yar
- Sigma: operation_roadrunner_sigma.yml
- Suricata: roadrunner_suricata.rules

Notes
- Private RFC1918 addresses observed in payload are contextual; do not action private IPs publicly.
- Decompressed data remained high-entropy; final layer requires cryptanalysis or key material.
