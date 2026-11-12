# IoT-Enabled Real-Time Patient Monitoring and Alert System

**Research and software project | Central Asian University**  
**Student:** Alisher Babadjanov (230271)  
**Course:** Scientific Research and Communication (4-SRC-10-804)

**[Open the live web prototype](https://mooregamer12-hue.github.io/monitoring/)**

## Project overview

This project explores a web-based monitoring and alert workflow for patients during intraoperative and postoperative care. The current prototype uses **manually entered and simulated vital-sign readings**, rather than physical medical sensors. It allows a user to manage several patients, inspect recent measurements and trends, and respond to configurable threshold and missing-data alerts.

**Research prototype only. Not a medical device and not intended for clinical use.**

## Current functionality

- Add, edit, select, and delete patients, including care phase and ward/room information.
- Enter or simulate heart rate (bpm), oxygen saturation (SpO₂, %), and temperature (°C).
- View patient status, current readings, and trend charts.
- Configure per-patient alert thresholds and acknowledge alerts in the alert log.
- Simulate device disconnection and reconnection; a watchdog checks for missing data.
- Browse recent reading history (up to 500 stored readings per patient; the history table displays the latest 100).
- Save patient information locally in the browser and restore it on page reload.
- Switch between automatic update intervals of 2 minutes, 30 seconds, and 10 seconds for demonstrations.

## Technology and architecture

The prototype is a single-page application implemented in **HTML, CSS, and vanilla JavaScript**, including Canvas-based trend charts. Its source is currently contained in one file, `index.html`.

```text
Manual input / Virtual sensor
              |
              v
     Reading and validation
              |
              v
  Threshold alerts + watchdog
              |
              v
  Patient dashboard and history
              |
              v
  Browser localStorage (GitHub Pages)
```

The code also includes an optional adapter for a host-provided shared database, but that integration is **not available on standard GitHub Pages**. On the published site, data are stored in each visitor's own browser; they are not synchronized between users or devices.

## Run the project

### Online

Open the **[live prototype](https://mooregamer12-hue.github.io/monitoring/)** in a modern browser.

### Locally

1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. Click **Add 3 demo patients** to populate the dashboard, or create a patient manually.
4. Select a patient to enter readings, turn on auto-simulation, adjust thresholds, or simulate disconnection.

No package installation, build step, or external server is required for the browser-only prototype.

## Research questions

1. **RQ1 — Near-real-time monitoring:** How can an IoT system collect and display patient vital signs in near real time?
2. **RQ2 — Reliability:** To what extent can reliable data handling maintain timely monitoring during interruptions?
3. **RQ3 — Alerts and visualization:** How can visualization and threshold alerts improve identification of abnormal readings?

The current web prototype demonstrates these concepts with virtual devices. It does **not** establish real sensor-to-dashboard network latency or resilience of MQTT transmission.

## Repository structure

```text
monitoring/
├── index.html          # Current web prototype (HTML, CSS, JavaScript)
├── README.md           # Project overview and setup instructions
└── docs/               # Research papers, proposals, assignments, presentations
```

The `docs/` folder contains research and course deliverables. Updated versions should be committed with meaningful messages so development and documentation changes can be reviewed over time.

## Limitations and future work

The current implementation uses simulated/manual data and browser-local storage. It has not been clinically validated and should not be used with real patient data. Physical ESP32 sensors, MQTT communication, a server-side backend, centralized storage, authentication, and more comprehensive performance and fault-injection testing are possible future extensions; **they are not implemented in the published prototype**.

## Academic context

Developed as part of the *Scientific Research and Communication* course at Central Asian University. The accompanying proposal, IEEE-style research paper, and other course materials are maintained in `docs/`.
