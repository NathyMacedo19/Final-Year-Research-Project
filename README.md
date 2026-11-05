# SMED Simulator

A Python application that helps reduce machine setup time in industry by applying the **SMED (Single-Minute Exchange of Die)** methodology.

The user records each step of a machine changeover, marks whether it needs the machine to be stopped, and tests possible improvements. The simulator then compares the process before and after, showing how much time the machine spends stopped and how much could be saved.

> 🚧 **Status:** in development — final-year research project, BSc in Computing, Dorset College Dublin.

---

## Why this project

Disorganised setups are a common source of lost production time. SMED tackles this by splitting setup activities into:

- **Internal** — can only be done with the machine stopped
- **External** — can be done while the machine is still running

and then converting, shortening, standardising or removing activities. This project turns that analysis into software, so different improvement scenarios can be tested and compared before changing anything on the shop floor.

## Features

### MVP
- [ ] Register a process (machine, current product, next product)
- [ ] Register setup activities with duration, operators and tools
- [ ] Classify activities as internal or external
- [ ] Calculate total, internal and external setup time
- [ ] Create scenarios and apply improvements (convert, reduce, eliminate)
- [ ] Before × after comparison with charts

### Next steps
- [ ] Database persistence and scenario history
- [ ] Setup timeline view
- [ ] Export results to PDF/CSV

### Advanced (optional)
- [ ] Activity dependencies and parallel activities
- [ ] Monte Carlo simulation (min / most likely / max times)

## Indicators

| Indicator | Formula |
| --- | --- |
| Total setup time | `T_setup = Σ tᵢ` |
| Internal time (machine stopped) | `T_internal = Σ tᵢ (internal)` |
| External time | `T_external = Σ tᵢ (external)` |
| Absolute reduction | `R = T_before − T_after` |
| Percentage reduction | `R% = (T_before − T_after) / T_before × 100` |
| Share of external activities | `P_external = N_external / N_total × 100` |

**Example:** a 48-minute setup reduced to 27 minutes → 21 minutes saved (43.75%).

## Tech stack

| Layer | Technology |
| --- | --- |
| Language | Python |
| Interface | Streamlit |
| Data & simulation | Pandas, NumPy |
| Database | SQLite + SQLAlchemy |
| Charts | Plotly |
| Tests | Pytest |

## Project structure

```
smed-simulator/
├── app/
│   ├── main.py            # Streamlit entry point
│   ├── pages/             # UI pages (processes, activities, scenarios, simulation)
│   ├── domain/            # Activity, Setup, Scenario, Simulator
│   ├── services/          # SMED rules, simulation, metrics
│   ├── database/          # connection, models, repositories
│   └── charts/            # comparison and timeline charts
├── tests/                 # unit tests (Pytest)
├── data/                  # sample data
├── docs/                  # project documentation
├── requirements.txt
└── README.md
```

## Getting started

```bash
git clone https://github.com/<your-username>/smed-simulator.git
cd smed-simulator
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app/main.py
```

Run the tests:

```bash
pytest
```

## Validation

Calculations are checked with automated tests and against manual calculations on a reference process. The simulator will be evaluated with a case study based on real or hypothetical setup data.

## Author

**Nathalia Macedo** — BSc in Computing Science, Dorset College Dublin
