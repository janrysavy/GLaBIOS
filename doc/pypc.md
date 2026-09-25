# PyPC profile

The `pypc` branch is based on the stable `v0.4.2` tag and adds a build profile
for the [PyPC-MCP](https://github.com/janrysavy/PyPC-MCP) emulator.

PyPC has no floppy disk controller. Its conventional-memory map ends at 640 KB
for both its CGA and VGA adapters. The profile therefore:

- disables the floppy controller and its POST path;
- skips the destructive RAM test while retaining RAM size detection;
- fixes conventional memory at 640 KB instead of deriving it from XT video
  switches;
- skips the keyboard reset delay and POST beep.

From DOS or DOSBox with MASM 5 and LINK on `PATH`, change to `src` and run:

```dos
PYPC.BAT
```

The batch file passes the release version and date explicitly because the
`v0.4.2` source tag still contains the earlier fallback values. It produces an
8 KiB `GLABIOS.ROM` using the repository's `GLA2ROM` tool. MASM 5.00 and LINK
3.60 produce SHA-256
`10d07e6052ae7e5ecdceba84a5635ec1482488bee800fe1a2541bfedc95bea33`.
