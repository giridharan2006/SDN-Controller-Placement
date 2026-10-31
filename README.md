# GreenPlace — Energy-Efficient SDN Controller Placement

GreenPlace is a research prototype for energy-efficient Software-Defined Networking (SDN) controller placement under hard delay constraints. It combines offline multi-objective controller placement with a runtime manager that can put controllers to sleep or wake them as network traffic changes.

This repository upload contains the Python implementation archive and three standalone HTML demonstrations.

## Repository contents

| File | Description |
|---|---|
| `greenplace_python_mvp.zip` | Compressed Python project bundle. It contains the implementation, scripts, tests, experiment outputs, and supporting project files. Extract this archive to access the source project. |
| `GreenPlace_Demo_Dashboard.html` | Interactive dashboard for exploring the GreenPlace study and its results. |
| `GreenPlace_Running_Animation.html` | Browser-based animation illustrating controller sleep/wake behaviour and switch migration. |
| `GreenPlace_Tested_Networks_Gallery.html` | Gallery of the network topologies used in the study. |

> **Note:** The Python source files are inside `greenplace_python_mvp.zip`; they are not individually listed at the repository root. The HTML files are provided separately for convenient viewing.

## Framework overview

GreenPlace has two main phases:

1. **Offline placement:** Searches for controller placements while considering power consumption, worst-case switch-to-controller delay, and an estimate of future switch-migration burden. The implementation includes an exact optimization baseline and a multi-objective NSGA-II approach.
2. **Runtime management:** Adjusts the active controller set as traffic changes. It uses smoothed traffic measurements, a minimum dwell time between sleep decisions, and delay- and capacity-aware switch reassignment.

The project evaluates the trade-offs between modeled power consumption, delay, and switch migrations. The reported experiments use network topology data and simulated traffic traces; they should not be interpreted as physical hardware or live-network measurements.

## Viewing the demonstrations

Download or clone this repository, then open any of the three `.html` files in a modern web browser. They are standalone demonstration pages and do not require a Python environment.

- Open `GreenPlace_Demo_Dashboard.html` to explore the results dashboard.
- Open `GreenPlace_Running_Animation.html` to view the runtime animation.
- Open `GreenPlace_Tested_Networks_Gallery.html` to browse the tested network topologies.

GitHub may display an HTML file as source code rather than rendering it as a webpage. If that happens, download the file and open it locally in your browser.

## Running the Python project

1. Download `greenplace_python_mvp.zip` from this repository.
2. Extract the archive.
3. Open a terminal in the extracted `greenplace_mvp` project directory (the directory containing `README.md`, `requirements.txt`, and `demo.py`).
4. Create and activate a virtual environment:

   **Linux / macOS**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   **Windows PowerShell**
   ```powershell
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

5. Install the dependencies:
   ```bash
   python -m pip install -r requirements.txt
   ```

6. Run the quick demonstration:
   ```bash
   python demo.py --quick
   ```

For the full setup instructions, additional experiment commands, and testing guidance, refer to the `README.md` and `BENCHMARKING.md` files inside the extracted Python project.

## Research scope and limitations

- The study evaluates 46 Topology Zoo networks, multiple random seeds, and eight traffic scenarios, including two real traffic traces.
- The reported power values come from the project's modeled power formulation and simulation setup.
- The runtime migration counts are simulation results, not measurements from a deployed SDN testbed.
- GreenPlace is not claimed to be the best static energy-placement method. Its main research focus is the interaction between placement-time migration awareness and runtime controller management.
- The exact optimization baseline and heuristic methods use the formulations and evaluation procedures documented in the accompanying source project and research report.

Please consult the research report and experiment summaries included inside the Python archive for detailed methodology, numerical results, and qualifications.

## Reproducibility

The Python archive includes the project code and supporting experiment material. Refer to its internal documentation for the exact commands, dependencies, and details needed to reproduce individual experiments.

## Authors

Sivaseelan S and Giridharan S  
Computer Science, Vellore Institute of Technology (VIT), Vellore, India.
