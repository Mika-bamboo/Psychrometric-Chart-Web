# 🌡️ Psychrometric Chart — FCU Cooling Line Calculator

An interactive, browser-based psychrometric chart for calculating and visualizing **Fan Coil Unit (FCU) cooling lines**. No installation or server required — open the HTML file directly in any modern browser.

---

## 📌 Features

- **Interactive Psychrometric Chart** rendered on HTML Canvas
  - Dry-bulb temperature axis (°C)
  - Humidity ratio axis (g/kg dry air)
  - Constant relative humidity curves (10% – 100%)
  - Constant wet-bulb temperature lines
  - Constant enthalpy lines

- **FCU Cooling Line Calculation**
  - Input: Entering Air Dry-Bulb (DB) & Wet-Bulb (WB) temperature
  - Input: Entering Water Temperature (EWT) & Leaving Water Temperature (LWT)
  - Output: Leaving Air DB, WB, Relative Humidity, Humidity Ratio, Enthalpy
  - Cooling line plotted directly on the chart from entering to leaving air state point

- **Results Summary Panel**
  - Sensible Cooling Capacity (kW)
  - Latent Cooling Capacity (kW)
  - Total Cooling Capacity (kW)
  - Sensible Heat Ratio (SHR)
  - Leaving Air Conditions (DB / WB / RH / Enthalpy)

- **PDF Export**
  - Export the chart and results report as a formatted PDF with one click
  - Suitable for project documentation and submittals

---

## 🗂️ File Structure

```
/
├── index.html          # Main application — single self-contained file
└── README.md           # This file
```

> The entire application is a **single HTML file** with no external dependencies that require installation. CDN libraries are loaded automatically when you open the file with an internet connection.

---

## 🚀 Getting Started

### Option 1 — Open Locally

1. Clone or download this repository
2. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari)
3. No build step, no server, no setup needed

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
# Open index.html in your browser
```

### Option 2 — GitHub Pages (Recommended)

Host the chart online for free using GitHub Pages:

1. Go to your repository **Settings → Pages**
2. Under **Source**, select `main` branch and `/ (root)`
3. Click **Save**
4. Access your chart at:
   ```
   https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/
   ```

---

## 🖥️ How to Use

### Step 1 — Enter Entering Air Conditions
| Field | Description | Typical Range |
|-------|-------------|---------------|
| Dry-Bulb Temp (DB) | Entering air temperature | 24–28 °C |
| Wet-Bulb Temp (WB) | Entering air wet-bulb temperature | 17–21 °C |

### Step 2 — Enter Water Conditions
| Field | Description | Typical Range |
|-------|-------------|---------------|
| Entering Water Temp (EWT) | Chilled water supply temperature | 7–12 °C |
| Leaving Water Temp (LWT) | Chilled water return temperature | 12–17 °C |

> Optionally enter **Air Flow Rate (m³/h)** or **Water Flow Rate (L/min)** for capacity calculations.

### Step 3 — Calculate
Click **Calculate** to:
- Plot the entering air state point on the chart
- Plot the apparatus dew point (ADP)
- Draw the **cooling line** from entering to leaving air state
- Display the leaving air conditions and cooling capacities

### Step 4 — Export PDF
Click **Export PDF** to download a formatted report containing:
- The psychrometric chart with the cooling line
- A summary table of all input and output conditions
- Calculated cooling capacities and SHR

---

## 🔢 Calculation Methodology

All psychrometric calculations follow **ASHRAE Fundamentals** at standard atmospheric pressure (101.325 kPa).

### Key Relationships Used

**Saturation Pressure** (Magnus approximation):
```
Psat = 0.6108 × exp(17.27 × T / (T + 237.3))  [kPa]
```

**Humidity Ratio from Wet-Bulb** (Sprung's formula):
```
W = Wsat_wb − A × (Tdb − Twb)
where A = 0.000799 (psychrometric constant, °C⁻¹)
```

**Enthalpy of Moist Air**:
```
h = 1.006 × Tdb + W × (2501 + 1.86 × Tdb)  [kJ/kg dry air]
```

**Apparatus Dew Point (ADP)**:
```
Determined by extending the cooling line to the saturation curve (φ = 100%)
```

**Sensible Heat Ratio (SHR)**:
```
SHR = Qs / Qt = ΔTdb / ΔTdb_total (along the room ratio line)
```

**Cooling Capacity** (when airflow is provided):
```
Qt  = ṁ × (h_ea − h_la)         [kW]   Total
Qs  = ṁ × Cp × (Tdb_ea − Tdb_la) [kW]   Sensible
Ql  = Qt − Qs                    [kW]   Latent
```

---

## 📐 Assumptions & Limitations

- Standard atmospheric pressure: **101.325 kPa** (sea-level)
- Air density assumed at **1.2 kg/m³** for volumetric flow conversions
- Bypass factor (BF) is estimated based on EWT; for precision, input BF directly
- Chart range: **0–50 °C** DB, **0–30 g/kg** humidity ratio
- This tool is intended for **preliminary engineering estimates**, not for replacing certified equipment selection software

---

## 🛠️ Technologies Used

| Library | Purpose |
|---------|---------|
| HTML5 Canvas | Psychrometric chart rendering |
| Vanilla JavaScript | All psychrometric calculations |
| [jsPDF](https://github.com/parallax/jsPDF) | PDF export |
| [html2canvas](https://html2canvas.hertzen.com/) | Chart capture for PDF |

All libraries are loaded via **CDN** — no `npm install` required.

---

## 📄 License

This project is released under the [MIT License](LICENSE).  
Free to use, modify, and distribute for commercial and non-commercial purposes.

---

## 🙋 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📬 Contact

For questions or feedback, open a [GitHub Issue](../../issues).

---

*Built for HVAC engineers — focused on FCU cooling line analysis.*
