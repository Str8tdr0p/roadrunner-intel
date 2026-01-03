# Executive summary

A steganographic payload was found in IMG_1118.png. Extraction confirmed LSB → XOR → deflate chain. Primary C2 observed: 76.250.68.175. Key artifacts (hashes, GUID, ports) listed in IOCs.csv. Decompressed data remains high-entropy and likely encrypted. Hunters: block, hunt, and request samples via PGP if you need to detonate privately.
