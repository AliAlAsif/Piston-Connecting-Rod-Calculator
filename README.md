# ME-3118 Piston & Connecting Rod Calculator

![Status](https://img.shields.io/badge/status-active-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![Field](https://img.shields.io/badge/field-mechanical%20engineering-orange)

An Excel-based engineering design calculator for **piston and connecting rod** sizing in a single-cylinder four-stroke engine. Developed as part of **ME-3118** coursework, it consolidates gas-force, thermal, stress, buckling, and fatigue calculations into a single auditable workbook with fully linked formulas.

---

## 📋 Overview

This workbook automates the preliminary design of two critical engine components:

1. **Piston assembly** — crown thickness, compression rings, skirt, gudgeon pin, and a Von Mises stress check on the head.
2. **Connecting rod** — I-section sizing, direct compression, whipping bending, combined Von Mises stress, and fatigue life via Soderberg/Goodman criteria.

All derived quantities are live formulas referencing a single `Inputs` sheet, so changing an engine parameter propagates through every result.

---

## 🗂️ Workbook Structure

| Sheet | Contents |
|-------|----------|
| **Inputs** | Engine geometry, material properties, heat-flow data, connecting-rod material, Marin factors, reciprocating mass. |
| **Piston** | Gas force, head thickness (strength & thermal), ring dimensions, skirt & barrel, gudgeon pin sizing, Von Mises stress check. |
| **Connecting Rod** | I-section proportions, direct compressive stress, whipping bending, combined Von Mises, fatigue analysis (Soderberg/Goodman), pin bore sizes. |

---

## ⚙️ Key Inputs (default configuration)

| Parameter | Symbol | Value | Unit |
|-----------|--------|-------|------|
| Rated power / cylinder | P | 6.23 | kW |
| Engine speed | N | 7500 | rpm |
| Bore | D | 51 | mm |
| Stroke | L | 48.8 | mm |
| Stroke type | x | 2 (four-stroke) | — |
| Max gas pressure | p | 4.5 | N/mm² |
| Connecting rod length | l | 97.9 | mm |
| Piston material | — | Al GHS 1300 | — |
| Rod material | — | Al GHS 1300 | — |
| Factor of safety (piston) | FOS | 2.25 | — |

---

## 🔬 Calculation Highlights

### Piston
- **Gas force:** \(F_g = p \cdot \frac{\pi D^2}{4}\)
- **Head thickness (strength):** Grashoff formula \(t = D\sqrt{\frac{3p}{16\sigma_t}}\)
- **Head thickness (thermal):** heat conducted through crown vs. allowable temperature drop
- **Gudgeon pin:** sized by both bearing pressure and bending stress; hollow ratio supported
- **Von Mises check** on crown with radial + hoop stress

### Connecting Rod
- **I-section:** flange = 4t, depth = 5t, all walls = t
- **Direct compression:** \(F_g / A\)
- **Whipping bending:** distributed inertia load → max moment → bending stress
- **Fatigue:** corrected endurance limit (Marin factors) → Soderberg & Goodman FOS
- **Pin bores:** small-end (gudgeon pin OD) and big-end bearing lengths

---

## 🚀 Usage

1. **Clone / download** the repository.
2. Open `ME-3118 piston connecting rod calculation.xlsx` in Excel, LibreOffice Calc, or Google Sheets.
3. Edit only the **yellow/input cells** on the `Inputs` sheet.
4. Review results on the `Piston` and `Connecting Rod` sheets.
5. Cross-check the Von Mises FOS values against your chosen design factor (default FOS = 2.25).

> ⚠️ **Do not edit formula cells** unless you intend to modify the calculation methodology. Sheets are fully cross-linked.

---

## 📐 Assumptions & Limitations

- Single-cylinder, naturally aspirated, four-stroke engine.
- Quasi-static gas loading; no dynamic valve-train or torsional effects.
- Piston treated as a flat circular plate under uniform pressure (Grashoff).
- Connecting rod treated as a short column in direct compression with whipping bending; buckling not explicitly checked beyond compressive yield.
- Fatigue uses fully reversed cycle approximation (σ_min = 0 at BDC).
- Material properties are typical handbook values for Al GHS 1300 — verify against your supplier datasheet before production use.

---

## ✅ Validation Checklist

Before using results for manufacturing:

- [ ] Von Mises FOS (piston) ≥ target FOS
- [ ] Von Mises FOS (rod) ≥ target FOS
- [ ] Soderberg & Goodman FOS ≥ 1.5–2.0
- [ ] Gudgeon pin diameter governed by both bearing and bending checks
- [ ] Head thickness = max(strength, thermal) requirement
- [ ] Ring axial width within min/max band

---

## 🛠️ Requirements

- Microsoft Excel 2016+ / LibreOffice Calc 7+ / Google Sheets
- No macros or add-ins required — pure formula workbook

---

## 📄 License

Released under the **MIT License** — free to use, modify, and distribute with attribution. See `LICENSE` for details.

---

## 👤 Author

**ME-3118 Course Project**
Mechanical Engineering — Machine Design

Contributions, corrections, and issue reports are welcome via pull requests or the issue tracker.

---

## 🔗 Related

- Shigley's *Mechanical Engineering Design* — fatigue & Marin factors
- Heywood, *Internal Combustion Engine Fundamentals* — gas loading
- Khurmi & Gupta, *Machine Design* — piston & connecting rod proportions

---

> **Disclaimer:** This workbook is intended for **educational and preliminary design** purposes. All results must be independently verified by a qualified engineer before use in any physical prototype or production component.
