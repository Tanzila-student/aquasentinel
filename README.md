# AquaSentinel — Competition Prototype

AquaSentinel is a polished software demonstration of a water-network incident-response workflow: explainable anomaly triage, an animated pipe digital twin with distinct leak/burst audio, a synthetic validation bench, multi-node segment ranking, and repair verification.

## Run locally

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Open `http://localhost:8501` in your browser.

## Demonstration flow

1. Start in **Command centre** and review pressure, inlet flow, outlet flow, imbalance, and the decision trace.
2. Open **Live pipe twin** to trigger a leak or burst and watch the animated incident response.
3. Use **Validation lab** to compare normal operation, leak, burst, demand surge, and sensor failure.
4. Open **Detection engine** to inspect decision thresholds and run the repeatable synthetic evaluation. Review precision, recall, false-alarm rate, per-class metrics, and the confusion matrix.
5. Open **Localization lab** to inject a synthetic leak into different segments and simulate unavailable sensor nodes. The system can report insufficient evidence rather than forcing a location.
6. Open **Components & system design** for the plain-language component guide, signal/data-flow diagram, hardware interface review, validation gates, and operational safeguards.
7. Use **Repair operations** to assign a crew, record completion, and verify the simulated return to baseline.

## What is demonstrated

- Interactive, scenario-driven telemetry and animated pipe incident simulation.
- Distinct browser-synthesized sound profiles: leak rushing-water hiss + warning pulses; burst low pressure thump + stronger rapid alarm. Enable sound by clicking the control in the pipe twin; browser audio requires a user gesture and device volume.
- Configurable, explainable rule-based classification with a data-quality gate.
- Repeatable synthetic test generation with class metrics and confusion matrix.
- Synthetic multi-node segment ranking, sensor-dropout handling, and an abstain state.
- Repair workflow, event trail, integration architecture, and pre-pilot acceptance plan.

## Interpretation of results

All telemetry, alarms, network values, localization scores, and repair effects in this build are simulated. Synthetic metrics characterize only the generated test distributions and current rule thresholds; they are not field-performance claims. The detector is rule-based rather than a trained machine-learning model. The app does not acquire physical sensor data, connect to a municipal network or live GIS, or actuate a valve.

## Proposed reference architecture

Pressure transducer + flow meter (+ optional acoustic/vibration sensing) → ESP32 edge node → LoRa or wired communication → gateway/MQTT → time-series store → explainable detection engine → segment triage → operator-confirmed repair → post-repair verification.

Candidate parts and interfaces are presented as a design starting point, not a build-ready bill of materials. Before physical assembly, finalize exact manufacturer part numbers and datasheets; verify ADC range, signal conditioning, protection/isolation, meter protocol, radio-region compliance, enclosure, and calibration.

## Validation path

1. Calibrate sensors against references and validate timestamps/units.
2. Characterize normal operation across demand and pump states.
3. Run repeated controlled leak/burst trials at labelled locations and severities.
4. Freeze thresholds and evaluate blind/held-out trials.
5. Report precision, recall, false-alarm rate, detection delay, and segment localization error, including noisy and missing-sensor conditions.
6. Complete safety, cybersecurity, audit, and operator-approval reviews before any field deployment or physical actuation.
