# CLAUDE.md — books repository

## Overview

This repository is a curated personal reference library of technical books, academic papers, RFC standards, and companion source code. There is no build system, application code, or test suite — the primary artifacts are PDFs, plain-text RFCs, and a small collection of C source files that accompany signal-processing textbooks.

**Remote origin**: `kallolpar/books` (previously `spinlockirqsave/books`)  
**Active development branch**: `claude/claude-md-docs-f9uV2`  
**Default branch**: `master`

---

## Repository Structure

```
books/
├── GPU_FPGA/               CUDA, OpenCL, FPGA programming
├── brownian_motion/        Stochastic processes, Bachelier, Einstein
├── codec/                  Digital telephony (Bellamy), audio codecs
├── derivatives/            Financial derivatives, options pricing, volatility
│   ├── Taleb Nassim/       Nassim Taleb's papers and books
│   ├── arb/                Arbitrage theory
│   ├── black_scholes/      Black-Scholes model papers
│   ├── copula/             Copula methods and pricing kernels
│   ├── derman/             Emanuel Derman's volatility papers (some in Polish: wyklad*.ppt)
│   ├── market_conventions/ Interest rate instruments and conventions
│   ├── monte carlo/        Monte Carlo simulation methods (Glasserman et al.)
│   └── statarb/            Statistical arbitrage, pairs trading
├── econometrics/           Statistical/econometric methods
├── electronics/            Circuit design, microcontrollers, serial comms
│   ├── Barbara Pióro*/     Polish-language electronics fundamentals (2 vols)
│   ├── NoC/                Networks-on-Chip
│   ├── microcontrollers/   ATmega32a, USBasp documentation
│   └── serial_communication/rs232/  RS-232 specs
├── high_speed_computing/   FPGA high-performance computing
│   └── FPGA/
├── information_theory/     Information theory texts
├── math/                   Mathematics reference
│   ├── Concrete_Mathematics*/  Knuth/Graham/Patashnik
│   ├── discrete_mathemathics/  Discrete math (+ links.txt)
│   ├── in_programming/     Math as used in programming
│   ├── linear_algebra/     Linear algebra, vector spaces
│   ├── optimization/       Mathematical optimization
│   └── tools_docs/         Spreadsheets (correlation.ods, linear_forms.xlsx)
├── operating_system/       OS design and internals
├── osi_protocols/          OSI protocol stack
├── physics/                Physics texts
├── processors/             x86, AMD64, RISC processor architecture
├── programming/            Software development reference
│   ├── algorithms/         Knuth TAOCP (archived: .zip, .rar)
│   ├── algorithms_and_data_structures/  Knuth + links.txt
│   ├── c/                  C programming
│   ├── fixed_point/        Fixed-point arithmetic
│   ├── floating_point/     Floating-point (incl. linux_kernel_floating_point.txt)
│   ├── linux_kernel/       Kernel internals, drivers, work deferral, debugging
│   ├── misc/               Miscellaneous programming references
│   ├── processes_&_threads/ Process and thread models
│   ├── rtp/                RTP protocol implementation
│   ├── software_engineering/ SE practices
│   ├── synchronization/    Synchronization primitives
│   └── threads/            Threading models and C++11 threading
├── rfc_standards/          Networking RFCs and IEEE/ITU standards
│   ├── SIP suite           rfc3261, rfc3264, rfc3959, rfc3960
│   ├── RTP/RTCP            rfc3550, rfc3551, rfc1889, rfc1890, rfc5117, rfc5761
│   ├── NTP                 rfc1305
│   ├── Transport           rfc793 (TCP), rfc768 (UDP)
│   ├── Link layer          rfc826 (ARP), IEEE 802.3 Ethernet
│   ├── MRCP                rfc_4463_mrcp.txt
│   └── Audio               ITU G.701, G.711, AIFF-C, rfc2833
├── signal_processing/      DSP texts and C implementations
│   ├── orfanidis_c_funcs_optimumsp2e/   C code for "Optimum Signal Processing 2e"
│   ├── orfanidis_c_functions/           C code for "Introduction to Signal Processing"
│   ├── speech/             Speech processing
│   └── tone_detection/     Tone detection algorithms (TKEO)
├── ssh/                    SSH protocol RFC suite
│   ├── rfc4250–rfc4254.txt  Core SSH RFCs
│   └── ssh v2 extensions/  rfc4255–rfc6594.txt
├── statistics/             Statistical methods
├── trading/                Quantitative and algorithmic trading
│   ├── HFT algorithmic trading/   High-frequency trading, market microstructure
│   ├── order_flow/         Order flow analysis
│   ├── trade clustering trades matching engine/  Market structure and matching
│   ├── urbanowicz/         OBV-based options pricing strategy papers
│   └── volatility/         Volatility trading, FX vol, Heston model
└── twsapi_doc/             Interactive Brokers TWS API documentation
```

---

## File Types

| Extension | Description |
|-----------|-------------|
| `.pdf` / `.PDF` | Primary content — books, papers, standards |
| `.txt` | Plain-text RFCs (`rfc768_udp.txt`, etc.) and notes |
| `.c` / `.h` | C source: companion code for Orfanidis DSP textbooks |
| `.ods` / `.xlsx` | Spreadsheet tools in `math/tools_docs/` |
| `.ppt` | PowerPoint slides (`derivatives/derman/wyklad*.ppt`) |
| `.doc` | Word documents (`trading/*/Trade by the Book.doc`) |
| `.chm` | Compiled HTML help (`programming/Effective C++...chm`) |
| `.rar` / `.zip` | Archived Knuth TAOCP volumes |
| `.cdf` | Mathematica CDF (`trading/HFT.../The Mathematics of Scalping.cdf`) |

---

## C Source Code (signal_processing/)

The two `orfanidis_*` directories contain standalone C implementations from Prof. S.J. Orfanidis (Rutgers) distributed with his textbooks. They are **reference implementations, not part of a build system** — no Makefile exists.

**`orfanidis_c_funcs_optimumsp2e/`** — "Optimum Signal Processing, 2nd Edition"
- Adaptive filtering: `lms.c`, `rls.c`, `rlsl.c`, `faest.c`
- Spectral estimation: `burg.c`, `yw.c`, `music.c`, `schur*.c`
- Linear prediction: `lev.c`, `frwlev.c`, `bkwlev.c`
- Support: `complex.c/.h`, `poly.c`, `gauss.c`, `gran.c`

**`orfanidis_c_functions/`** — "Introduction to Signal Processing"
- Filter implementations: `fir.c`, `fir2.c`, `fir3.c`, `cfir*.c`, `sos.c`, `cheby.c`
- FFT: `fft.c`, `ifft.c`, `dft.c`, `dtft.c`
- Signal generation: `wavgen.c`, `sine.c`, `square.c`
- Utilities: `complex.c`, `conv.c`, `corr.c`, `ran*.c`

To compile individual files: `gcc -o <name> <name>.c -lm`

---

## Development Workflow

### Adding New Material

1. Place the file in the most specific relevant subdirectory.
2. Use descriptive filenames that match the document's title or standard name (e.g., `rfc3550_rtp.pdf`, `Options__Futures_and_Other_Derivatives_7th_John_Hull.pdf`).
3. For RFCs, the filename convention is `rfc<number>[_short_title].txt` or `.pdf`.
4. Commit with a short message describing what was added (the history uses terse messages like `"ITU g701 g711"`, `"TKEO in speech analysis"`, `"multithreaded servers"`).

### Git Conventions

- Commit messages are brief topic labels, not full sentences.
- No linting, CI, or pre-commit hooks exist.
- Large binary files (PDFs) are committed directly — no Git LFS is configured.

### Branch Strategy

- `master` is the long-term history branch.
- Feature/task branches follow the pattern `claude/<task-slug>`.

---

## Key Domain Notes

**Derivatives / Quantitative Finance**: Heavy focus on options pricing (Black-Scholes, local vol, stochastic vol/Heston), copula methods, FX derivatives, and statistical arbitrage. Derman's volatility papers are in Polish (`wyklad` = lecture).

**Signal Processing**: The Orfanidis C functions implement classical DSP algorithms. The `speech/` and `tone_detection/` subdirs cover Teager-Kaiser Energy Operator (TKEO) based methods, relevant to VoIP/telephony.

**Networking / VoIP**: RFC coverage spans the full SIP/RTP/RTCP stack used in VoIP applications, plus SSH, TCP/UDP, and Ethernet fundamentals.

**Trading Infrastructure**: The `twsapi_doc/` directory contains IB TWS API documentation; `trading/HFT*/` covers market microstructure, limit order books, and exchange protocols (CME FIXML, Deutsche Börse Xetra).

**Note on duplicates**: Some PDFs appear in multiple directories (e.g., `bachelier-thesis` in both `brownian_motion/` and `derivatives/`, several Carr and Protter papers duplicated across `math/` and `derivatives/`). This is intentional cross-referencing, not an error.
