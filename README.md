# 📊 CSV Dashboard — Free Python Tool for Plotting Timeseries Data

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![pandas](https://img.shields.io/badge/pandas-1.5+-150458.svg)](https://pandas.pydata.org/)
[![matplotlib](https://img.shields.io/badge/matplotlib-3.6+-11557c.svg)](https://matplotlib.org/)
[![License](https://img.shields.io/badge/License-MIT--like-success.svg)](#-license)
[![Free](https://img.shields.io/badge/Price-FREE-50e69a.svg)](https://philyeh.gumroad.com)

> **Drop in any CSV. Pick a column. See the trend.** A free, lightweight
> Python plotter for timeseries data — built for engineers who are tired
> of Excel mangling timestamps. Multi-series overlay, auto twin Y-axis,
> smart time formatting, per-series stats, source code included.

CSV Dashboard screenshot
<img width="1280" height="720" alt="csv_cover" src="https://github.com/user-attachments/assets/828867bf-fb26-4d31-b395-d7c33c3bf58f" />


---

## 🎯 Why this exists

You shouldn't need Excel, Power BI, or a Jupyter notebook just to look
at a CSV log file. This is the simplest possible "drop in a file → see
the trend" tool, but with the polish you'd expect from a paid app.

**Free forever. Use it for whatever. Source code included.**

---

## ✨ Features

### Multi-series overlay (up to 4)

Compare four signals side-by-side on the same chart. Each gets a distinct
color (emerald, cyan, purple, amber).

### Auto twin Y-axis

Mix RPM (1850) with pressure (5 bar) on the same chart? The tool **detects
the magnitude difference automatically** and splits onto two Y-axes so
all signals stay readable. No manual configuration. This is the difference
between a useless chart and a useful one.

### Smart time-axis formatting

The tool inspects your timestamp range and picks an appropriate tick
density:

- **Sub-minute** → seconds shown
- **Up to 30 minutes** → minute granularity with seconds
- **Up to 6 hours** → minute ticks
- **Up to 2 days** → hourly ticks
- **Multi-day** → date + time

No more "30-second ticks on a 6-hour chart" mess.

### Per-series stats panel

Below the chart: min / max / mean / std / count for every series.
Useful for spotting outliers, baseline drift, or noisy sensors.

### Real matplotlib toolbar

Standard matplotlib navigation: pan, zoom-to-rectangle, view history,
save as PNG / SVG / PDF.

### Robust CSV handling

- Non-numeric columns (status flags, names) are detected and silently
  skipped if picked as Y-axis
- Failed timestamp parses fall back gracefully to row indices
- Mixed-type columns are coerced to numbers where possible
- Empty rows are filtered automatically

### Dark industrial theme

Same UI patterns as my paid Industrial Python Toolkit (J1939, Modbus,
MQTT, EtherNet/IP) — they all feel like one coherent family.

---

## 🚀 Quick Start

```bash
# Clone
git clone https://github.com/PhilYeh1212/Python-CSV-Visualization-Dashboard
cd Python-CSV-Visualization-Dashboard

# Install (just two dependencies)
pip install -r requirements.txt

# Run
python dashboard_app.py
```

The repo includes `Demo.csv` (600 rows of realistic industrial timeseries
data — pump RPM, pressure, flow, temperature) so you can verify everything
works in 10 seconds:

1. Click **📂 Load CSV** → pick `Demo.csv`
2. Click **📈 Plot**
3. Watch the auto twin-axis kick in (RPM is in the thousands, pressure in
   single digits — they get split automatically)

---

## 🐧 Linux note

Tkinter doesn't always ship with Python on Linux. If you hit
`ModuleNotFoundError: No module named 'tkinter'`:

```bash
sudo apt install python3-tk        # Ubuntu / Debian
sudo dnf install python3-tkinter   # Fedora
```

---

## 💡 Tips

### Best CSVs to throw at it

Anything matching this pattern:

```
Timestamp,            ColumnA, ColumnB, ColumnC
2026-01-05 14:00:00,  1850,    5.2,     34
2026-01-05 14:00:01,  1852,    5.3,     34
...
```

The first column doesn't have to be "Timestamp" — any column with
parseable date/time values is fine. If you don't have a timestamp,
pick **(row index)** as the X-axis to plot against sample number.

### Picking the right Y-axis combination

For best clarity, group signals with similar magnitudes:
- All 4 signals with values 0-100 → great
- 3 signals in single digits + 1 in thousands → still works (auto
  twin-axis kicks in)
- More than 4 signals → run twice with different combinations

### Exporting

Click 💾 in the matplotlib toolbar to save the current chart. PNG is best
for emails/presentations; SVG is best if you want to edit in Illustrator
or Inkscape.

---

## 🎁 Want to GENERATE the CSVs?

This dashboard is the **visualization** piece. The other half — actually
**logging data from your devices** — is what my paid Industrial Python
Toolkit handles:

| Tool | What it does | Price |
|---|---|---:|
| 🚛 **[J1939 Sniffer Pro](https://philyeh.gumroad.com)** | Heavy-duty CAN bus → CSV with auto-decoded units | $59 |
| ⚙️ **[Modbus Logger Pro](https://philyeh.gumroad.com)** | RTU + TCP polling → CSV with smart register decoding | $49 |
| 📡 **[MQTT Logger Pro](https://philyeh.gumroad.com)** | Subscribe + auto-JSON flatten → CSV ready for pandas | $39 |
| 🏭 **[EtherNet/IP Study Kit](https://philyeh.gumroad.com)** | Learn CIP byte-by-byte (Allen-Bradley etc.) | $29 |
| 🔒 **[Private ChatGPT Stack](https://philyeh.gumroad.com)** | Self-hosted RAG with Llama 3 + Docker | $59 |
| 📦 **[Industrial Python Toolkit Bundle](https://philyeh.gumroad.com)** | All 4 industrial tools (save $47) | **$129** |

All five paid tools share the same UI/UX as this dashboard, so once
you're comfortable here, the others feel familiar in seconds.

---

## 🤔 Why is this free?

Two reasons:

1. **The paid tools generate CSVs. This one visualizes them.** They go
   together. Making the visualizer free means more people discover the
   toolkit, and you get a polished plotter without me having to bundle
   it into every paid product.

2. **Distribution > revenue (for now).** A free tool people actually use
   is worth more than a $5 tool nobody hears about. If this saves you
   time and you decide to grab one of the paid tools, that's the
   exchange.

You can also grab this on Gumroad with the **"pay what you want"** option
(starting at $0) if you'd like to leave a small tip — but no obligation.

👉 **[Free download on Gumroad](https://philyeh.gumroad.com)**
(includes a setup guide and sample CSV)

---

## 📚 Related reading

I write about industrial Python and protocol internals at
**[dev.to/philyeh](https://dev.to/philyeh)** — including how this
dashboard was designed.

---

## 📫 About

**Phil Yeh** — Senior Automation Engineer based in Taiwan. I build Python
tools for industrial protocol work.

- 🛒 **Store:** [philyeh.gumroad.com](https://philyeh.gumroad.com)
- ✍️ **Blog:** [dev.to/philyeh](https://dev.to/philyeh)

---

## 📝 License

Free for any use — personal, commercial, modify, redistribute. No strings
attached.

If this tool saves you time, the only "thank you" I ask:

- ⭐ **A star on this repo** if you liked it
- 💚 **Check out the [paid toolkit](https://philyeh.gumroad.com)** if you
  need to log data from PLCs / sensors / IoT brokers / vehicle CAN buses

---

<sub>**Keywords:** CSV, Python, matplotlib, pandas, timeseries, plotting,
visualization, dashboard, industrial, data analysis, free, open source,
Tkinter, Modbus log, MQTT log, J1939 log, sensor data</sub>
