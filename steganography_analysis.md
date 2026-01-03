# Stego notes 

What
- LSB layer confirmed. Extracted raw LSB: ~98 KB.
- Decoding chain observed: LSB → XOR → deflate → secondary LSB → unknown final encoding.

Keys / offsets
- XOR keys found: 0x88 (primary), 0x38, 0x70.
- Deflate payload location (example): offset ~68600 (decimal).
- GUID offset: 0x166D (5741).
- C2 marker offset: 0x4DE (1246).

Artifacts (kept offline)
- lsb_full_extraction.bin
- lsb_payload_gzip.bin
- decompressed_payload.bin (~29.7 KB)
- LSB_FROM_DECOMPRESSED.bin

Remaining work
- Decompressed data is high-entropy; final layer likely encrypted or custom-compressed.
- Proceed with cryptanalysis or known-plaintext attempts in a controlled lab.
