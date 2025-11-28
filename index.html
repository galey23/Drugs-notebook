<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>RRT Drug Dilution & Infusion Calculator</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    * {
      box-sizing: border-box;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
                   Roboto, sans-serif;
    }
    body {
      margin: 0;
      padding: 1.5rem;
      background: #f4f5f7;
    }
    .app {
      max-width: 800px;
      margin: 0 auto;
      background: #ffffff;
      padding: 1.5rem;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
    }
    h1 {
      font-size: 1.4rem;
      margin-top: 0;
      margin-bottom: 0.5rem;
    }
    p {
      margin: 0.25rem 0;
      font-size: 0.9rem;
      color: #444;
    }
    .warning {
      margin-top: 0.5rem;
      padding: 0.5rem 0.75rem;
      background: #fff7e6;
      border-left: 4px solid #faad14;
      font-size: 0.85rem;
    }
    label {
      display: block;
      font-size: 0.85rem;
      margin-bottom: 0.25rem;
      font-weight: 600;
    }
    select, input[type="number"] {
      width: 100%;
      padding: 0.4rem 0.5rem;
      border-radius: 4px;
      border: 1px solid #d9d9d9;
      font-size: 0.9rem;
    }
    .row {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
      margin-top: 0.75rem;
    }
    .col {
      flex: 1 1 160px;
    }
    .muted {
      font-size: 0.8rem;
      color: #777;
    }
    .standard {
      margin-top: 0.5rem;
      font-size: 0.85rem;
      color: #333;
    }
    button {
      margin-top: 1rem;
      padding: 0.5rem 1.25rem;
      border-radius: 4px;
      border: none;
      cursor: pointer;
      font-size: 0.95rem;
      font-weight: 600;
      background: #1677ff;
      color: #fff;
    }
    button:active {
      transform: translateY(1px);
    }
    .results {
      margin-top: 1.25rem;
      padding-top: 1rem;
      border-top: 1px solid #e5e5e5;
    }
    .results h2 {
      font-size: 1.1rem;
      margin: 0 0 0.5rem;
    }
    .result-main {
      font-size: 1.2rem;
      font-weight: 700;
      margin-bottom: 0.25rem;
    }
    .result-main span {
      font-size: 1.5rem;
    }
    .result-text {
      font-size: 0.9rem;
      margin-top: 0.5rem;
    }
    .error {
      margin-top: 0.5rem;
      color: #d4380d;
      font-size: 0.85rem;
    }
    .prep {
      margin-top: 0.5rem;
      padding: 0.5rem 0.75rem;
      background: #f0f5ff;
      border-left: 4px solid #1677ff;
      font-size: 0.85rem;
    }
    @media (max-width: 600px) {
      body {
        padding: 0.75rem;
      }
      .app {
        padding: 1rem;
      }
    }
  </style>
</head>
<body>
<div class="app">
  <h1>RRT Drug Dilution &amp; Infusion Calculator</h1>
  <p><strong>Note:</strong> This tool supports common RRT infusions and assumes standard preparations from your local guide. Always cross-check with the official protocol and clinical judgement.</p>

  <div class="warning">
    This calculator does <strong>not</strong> replace your local drug dilution guide, pump charts, or consultant/anaesthetist instructions. Use at your own responsibility and verify all results before prescribing or administering.
  </div>

  <div class="row" style="margin-top:1rem;">
    <div class="col" style="flex:2 1 260px;">
      <label for="drugSelect">Drug</label>
      <select id="drugSelect">
        <option value="dobutamine">Dobutamine</option>
        <option value="dopamine">Dopamine</option>
        <option value="norad_peripheral">Noradrenaline (Peripheral)</option>
        <option value="norad_central">Noradrenaline (Central syringe 60 mL)</option>
        <option value="isoprenaline">Isoprenaline</option>
        <option value="labetalol">Labetalol infusion</option>
        <option value="salbutamol_iv">Salbutamol IV infusion</option>
      </select>
    </div>
  </div>

  <div class="prep" id="prepText"></div>
  <p class="standard">
    Standard concentration: <span id="standardConcentration"></span>
  </p>
  <p class="muted">
    You may optionally override the concentration below if the prepared bag/syringe differs from the standard.
  </p>

  <div class="row">
    <div class="col" id="weightGroup">
      <label for="weightInput">Patient weight (kg)</label>
      <input type="number" id="weightInput" min="1" step="0.1" placeholder="e.g. 70">
    </div>
    <div class="col">
      <label id="doseLabel" for="doseInput">Target dose</label>
      <input type="number" id="doseInput" min="0" step="0.01" placeholder="">
    </div>
    <div class="col">
      <label id="concentrationLabel" for="concentrationInput">Custom concentration</label>
      <input type="number" id="concentrationInput" min="0" step="0.01" placeholder="Leave blank for standard">
    </div>
  </div>

  <button id="calculateBtn" type="button">Calculate infusion rate</button>
  <div class="error" id="error"></div>

  <div class="results" id="results" style="display:none;">
    <h2>Result</h2>
    <div class="result-main">
      Set pump to approximately <span id="rateOutput"></span> mL/h
    </div>
    <div class="result-text" id="summaryText"></div>
  </div>

  <div class="warning">
    Always confirm the calculation independently (e.g. with a second practitioner or pump chart) before starting an infusion.
  </div>
</div>

<script>
  // Drug configuration based on your RRT drug guide.
  // unitType:
  //   "mcg_kg_min" -> dose in micrograms/kg/min (requires weight)
  //   "mcg_min"    -> dose in micrograms/min
  //   "mg_min"     -> dose in milligrams/min
  const drugConfigs = {
    dobutamine: {
      name: "Dobutamine",
      unitType: "mcg_kg_min",
      concentrationMcgPerMl: 1000, // 250 mg in 250 mL => 1 mg/mL = 1000 mcg/mL
      defaultDose: 5,
      minDose: 1,
      maxDose: 20,
      defaultWeight: 70,
      prepText:
        "Standard bag: 250 mg in 250 mL NS or D5W (1 mg/mL = 1000 mcg/mL). Use a dedicated line."
    },
    dopamine: {
      name: "Dopamine",
      unitType: "mcg_kg_min",
      concentrationMcgPerMl: 1600, // 400 mg in 250 mL => 1600 mcg/mL
      defaultDose: 5,
      minDose: 2,
      maxDose: 25,
      defaultWeight: 70,
      prepText:
        "Standard bag: 400 mg in 250 mL NS or D5W (1600 mcg/mL). Use a dedicated line."
    },
    norad_peripheral: {
      name: "Noradrenaline (Peripheral)",
      unitType: "mcg_kg_min",
      concentrationMcgPerMl: 16, // 4 mg in 250 mL => 16 mcg/mL
      defaultDose: 0.05,
      minDose: 0.01,
      maxDose: 0.25,
      defaultWeight: 70,
      prepText:
        "Peripheral infusion: 4 mg in 250 mL NS (16 mcg/mL). Dedicated line only; follow local peripheral-use limits."
    },
    norad_central: {
      name: "Noradrenaline (Central syringe 60 mL)",
      unitType: "mcg_kg_min",
      concentrationMcgPerMl: 100, // 6 mg to 60 mL => 100 mcg/mL
      defaultDose: 0.05,
      minDose: 0.01,
      maxDose: 1,
      defaultWeight: 70,
      prepText:
        "Central syringe: 6 mg made up to 60 mL with NS or D5W (100 mcg/mL). Dedicated central line."
    },
    isoprenaline: {
      name: "Isoprenaline",
      unitType: "mcg_min",
      concentrationMcgPerMl: 4, // 2 mg in 500 mL => 4 mcg/mL
      defaultDose: 2,
      minDose: 1,
      maxDose: 10,
      prepText:
        "Standard bag: 2 mg in 500 mL D5W (4 mcg/mL). Dedicated line. Dose is in mcg/min (no weight)."
    },
    labetalol: {
      name: "Labetalol infusion",
      unitType: "mg_min",
      concentrationMgPerMl: 1, // 200 mg in 200 mL => 1 mg/mL
      defaultDose: 1,
      minDose: 0.5,
      maxDose: 4,
      prepText:
        "Standard bag: remove 90 mL from a 250 mL bag, add 200 mg (40 mL) labetalol to make 200 mL (1 mg/mL). Dedicated line."
    },
    salbutamol_iv: {
      name: "Salbutamol IV",
      unitType: "mcg_min",
      concentrationMcgPerMl: 200, // 10 mg in 50 mL => 200 mcg/mL
      defaultDose: 5,
      minDose: 2,
      maxDose: 20,
      prepText:
        "Maintenance infusion: 10 mg in 50 mL NS (200 mcg/mL). Dedicated line. Dose is in mcg/min."
    }
  };

  function setDrugDefaults() {
    const select = document.getElementById("drugSelect");
    const key = select.value;
    const config = drugConfigs[key];
    if (!config) {
      return;
    }

    const doseLabel = document.getElementById("doseLabel");
    const weightGroup = document.getElementById("weightGroup");
    const concLabel = document.getElementById("concentrationLabel");
    const standardConc = document.getElementById("standardConcentration");
    const prepText = document.getElementById("prepText");

    if (config.unitType === "mcg_kg_min") {
      doseLabel.textContent = "Target dose (mcg/kg/min)";
      weightGroup.style.display = "";
    } else if (config.unitType === "mcg_min") {
      doseLabel.textContent = "Target dose (mcg/min)";
      weightGroup.style.display = "none";
    } else {
      doseLabel.textContent = "Target dose (mg/min)";
      weightGroup.style.display = "none";
    }

    if (config.unitType === "mg_min") {
      concLabel.textContent = "Custom concentration (mg/mL, optional)";
      standardConc.textContent = config.concentrationMgPerMl + " mg/mL";
    } else {
      concLabel.textContent = "Custom concentration (mcg/mL, optional)";
      standardConc.textContent = config.concentrationMcgPerMl + " mcg/mL";
    }

    document.getElementById("doseInput").value =
      typeof config.defaultDose === "number" ? config.defaultDose : "";
    document.getElementById("weightInput").value =
      typeof config.defaultWeight === "number" ? config.defaultWeight : "";
    document.getElementById("concentrationInput").value = "";

    prepText.textContent = config.prepText || "";

    document.getElementById("results").style.display = "none";
    document.getElementById("error").textContent = "";
  }

  function calculateRate() {
    const select = document.getElementById("drugSelect");
    const key = select.value;
    const config = drugConfigs[key];
    const errorEl = document.getElementById("error");
    const resultsEl = document.getElementById("results");
    const rateEl = document.getElementById("rateOutput");
    const summaryEl = document.getElementById("summaryText");

    errorEl.textContent = "";
    resultsEl.style.display = "none";

    if (!config) {
      errorEl.textContent = "Unknown drug configuration.";
      return;
    }

    const doseInput = parseFloat(
      document.getElementById("doseInput").value
    );
    if (isNaN(doseInput) || doseInput <= 0) {
      errorEl.textContent = "Please enter a valid target dose.";
      return;
    }

    let weight = null;
    if (config.unitType === "mcg_kg_min") {
      weight = parseFloat(
        document.getElementById("weightInput").value
      );
      if (isNaN(weight) || weight <= 0) {
        errorEl.textContent = "Please enter a valid patient weight.";
        return;
      }
    }

    const concOverride = parseFloat(
      document.getElementById("concentrationInput").value
    );

    let rateMlPerHr;
    let concUsed;
    let concUnit;
    let summary;

    if (config.unitType === "mg_min") {
      // mg/min with mg/mL concentration
      const standardConcMgPerMl = config.concentrationMgPerMl;
      const concMgPerMl =
        !isNaN(concOverride) && concOverride > 0
          ? concOverride
          : standardConcMgPerMl;
      rateMlPerHr = (doseInput * 60) / concMgPerMl;
      concUsed = concMgPerMl;
      concUnit = "mg/mL";
      summary =
        config.name +
        ": dose " +
        doseInput +
        " mg/min, concentration " +
        concMgPerMl +
        " mg/mL ⇒ pump rate ≈ " +
        rateMlPerHr.toFixed(1) +
        " mL/h.";
    } else if (config.unitType === "mcg_kg_min") {
      // micrograms/kg/min with mcg/mL concentration
      const standardConcMcgPerMl = config.concentrationMcgPerMl;
      const concMcgPerMl =
        !isNaN(concOverride) && concOverride > 0
          ? concOverride
          : standardConcMcgPerMl;
      rateMlPerHr = (doseInput * weight * 60) / concMcgPerMl;
      concUsed = concMcgPerMl;
      concUnit = "mcg/mL";
      summary =
        config.name +
        ": dose " +
        doseInput +
        " mcg/kg/min at " +
        weight +
        " kg, concentration " +
        concMcgPerMl +
        " mcg/mL ⇒ pump rate ≈ " +
        rateMlPerHr.toFixed(1) +
        " mL/h.";
    } else {
      // mcg/min with mcg/mL concentration
      const standardConcMcgPerMl = config.concentrationMcgPerMl;
      const concMcgPerMl =
        !isNaN(concOverride) && concOverride > 0
          ? concOverride
          : standardConcMcgPerMl;
      rateMlPerHr = (doseInput * 60) / concMcgPerMl;
      concUsed = concMcgPerMl;
      concUnit = "mcg/mL";
      summary =
        config.name +
        ": dose " +
        doseInput +
        " mcg/min, concentration " +
        concMcgPerMl +
        " mcg/mL ⇒ pump rate ≈ " +
        rateMlPerHr.toFixed(1) +
        " mL/h.";
    }

    if (!isFinite(rateMlPerHr) || rateMlPerHr <= 0) {
      errorEl.textContent =
        "Calculation error – please check the dose and concentration values.";
      return;
    }

    rateEl.textContent = rateMlPerHr.toFixed(1);
    summaryEl.textContent = summary + " Always cross-check with your local protocol.";
    resultsEl.style.display = "block";
  }

  document.addEventListener("DOMContentLoaded", function () {
    const select = document.getElementById("drugSelect");
    select.addEventListener("change", setDrugDefaults);
    document
      .getElementById("calculateBtn")
      .addEventListener("click", calculateRate);
    setDrugDefaults();
  });
</script>
</body>
</html>
