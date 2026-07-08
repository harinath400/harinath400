# RV32I RISC-V Core — Physical Design (RTL-to-GDSII)

Physical design implementation of a 32-bit RISC-V (RV32I) core, taken from synthesizable RTL through to a sign-off-ready layout at 32nm.

## 🎯 Results

| Metric | Result |
|---|---|
| Target frequency | 250 MHz |
| Timing closure | ✅ Achieved (zero setup/hold violations) |
| DRC violations | 0 |
| LVS violations | 0 |
| Gate count | ~50K |
| Die area | 0.65 mm² |
| Power domains | Multi-domain (UPF, level shifters) |

## 🔧 Flow & Tools

- **Synthesis & PnR:** Synopsys Fusion Compiler
- **Static Timing Analysis:** Synopsys PrimeTime
- **Physical Verification:** Siemens Calibre (DRC / LVS / ERC / Antenna) + ICC2 built-in checks
- **Low Power:** UPF (Unified Power Format) — level shifters for multi-voltage domains
- **Scripting:** Tcl automation for synthesis and place-and-route steps

## 🪜 Flow Stages

1. **RTL & Synthesis** — RV32I RTL synthesized with Fusion Compiler, SDC constraints for target clock/IO timing
2. **Floorplanning** — Core area planning, power grid (rings/straps), pin placement
3. **Placement** — Standard cell placement with congestion and timing-driven optimization
4. **Clock Tree Synthesis (CTS)** — Balanced clock tree to minimize skew and insertion delay
5. **Routing** — Signal + power routing with DRC-clean results
6. **Signoff** — STA (PrimeTime) for timing closure, Calibre for DRC/LVS/ERC/antenna checks

## 📁 Repo Structure

```
rv32i-physical-design/
├── rtl/                # RV32I core RTL source
├── constraints/        # SDC timing constraints
├── upf/                # Power intent (UPF) files
├── scripts/            # Tcl scripts for synthesis & PnR
├── reports/            # Timing, DRC, LVS, power reports
├── docs/                # Flow writeup, floorplan diagrams, screenshots
└── README.md
```

## 📝 Notes

This project was completed as part of Advanced VLSI Physical Design & Verification training. RTL source is for portfolio/demonstration purposes.
