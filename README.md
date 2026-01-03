# Operation RoadRunner — drop note

I found a stego payload in IMG_1118.png. I extracted artifacts and decoded multiple layers. This repo is the raw drop: hashes, rules, IOCs, and concise notes for defenders. No binaries.

TLP: AMBER — share with defenders. Samples remain offline and are provided only to vetted analysts via encrypted transfer.

Contents
- OPERATION_ROADRUNNER_SOC_REPORT.md — short, actionable SOC playbook
- EXECUTIVE_SUMMARY.md — quick facts
- IOCs.csv / IOCs.json — machine-readable indicators (hashes, C2 IPs, ports, GUID)
- roadrunner_yara.yar — YARA (file & memory)
- operation_roadrunner_sigma.yml — Sigma for SIEM hunts
- roadrunner_suricata.rules — IDS rules
- steganography_analysis.md — extraction notes, offsets, keys
- c2_infrastructure_report.md — extracted IP candidates (public + private contexts)
- COMMUNITY_POST.md — coordination thread text
- SECURITY.md — sample request / handling
- CONTRIBUTING.md, ISSUE_TEMPLATE.md, CONTRIBUTORS.md — minimal collaboration templates
- .gitignore — blocks accidental uploads

What I did
- Confirmed LSB stego → XOR → deflate chain
- Found working XOR keys (0x88 primary; 0x38, 0x70 also observed)
- Extracted compressed payload and produced detection artifacts
- Partial decryption remains; final layer likely encrypted/custom-compressed

What I did not publish
- No .bin, no memory dumps, no PCAPs, no executables. Samples are offline.

If you want the sample
- Post a request in Discussions with your PGP fingerprint and short justification (role / org / pseudonym). I vet, then send encrypted.

If you will hunt
- Use the provided YARA/Sigma/Suricata and IOCs.csv. Run them, report sightings in Issues. Keep outputs high-level (counts, timestamps, source IPs). Do not publish raw PCAPs or sample binaries.

— single-operator drop
