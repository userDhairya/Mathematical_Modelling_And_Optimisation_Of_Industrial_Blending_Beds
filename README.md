Blending Bed Optimisation Using LSTM Surrogates and NSGA-III

This repository contains the full implementation of a multi-objective optimisation framework for analysing bulk material blending behaviour using:

LSTM surrogate models (predicting simulation objectives F1 and F2)

High-fidelity blending simulations

NSGA-III evolutionary multi-objective optimisation

Latin Hypercube Sampling (LHS) for experimental design

The project is part of an MSc Data Science dissertation completed in collaboration with J&C Bachmann (Germany), focusing on evaluating whether machine learning surrogates can replace computationally expensive simulation models in optimisation workflows.

🚀 Repository Structure
├── lstm_training/
│   ├── model7.h5                 # LSTM model for F1
│   ├── model8.h5                 # LSTM model for F2
│   ├── scaler_X.pkl              # Saved StandardScaler for inputs
│   └── training_scripts.py
│
├── nsga_optimisation/
│   ├── NSGA-III_modelling.py     # ⚠️ LARGE FILE – download & run locally
│   ├── simulation_results_model/ # JSON outputs
│
├── simulation/
│   ├── simulation_functions.py   # Simulation helper functions
│   └── evaluate_simulation.py
│
├── plots/
│   ├── surrogate_vs_simulation.png
│   ├── pareto_fronts.png
│   └── hypervolume_convergence.png
│
├── README.md                     # Project documentation
└── requirements.txt              # All dependencies

⚠️ Important Note
NSGA-III_modelling.py is too large to render on GitHub.

GitHub cannot display large Python files.
To use it:

Download the file from the repo

Open it in VS Code / PyCharm / Jupyter

Run it inside your local Python environment

git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
python nsga_optimisation/NSGA-III_modelling.py

🧠 Project Overview

The optimisation aims to minimise:

F1: Standard deviation of quality after reclaiming

F2: Standard deviation of volume after reclaiming

Two LSTM models (LSTM_sim_1 and LSTM_sim_2) were trained on 200,000 simulated samples to approximate these objectives. NSGA-III is then used to generate Pareto-optimal solutions using both:

The simulation model

The LSTM surrogate models

Finally, all LSTM-optimised solutions are recomputed using simulation to study differences and correlations.

🔧 How to Run the Optimisation
1. Install dependencies
pip install -r requirements.txt

2. Run NSGA-III optimisation with the surrogate models
python nsga_optimisation/NSGA-III_modelling.py


Output will be stored in:

simulation_results_model/*.json


Each JSON file contains:

Optimisation run metadata

Decision variables (X)

Objective values predicted by LSTM (F1, F2)

3. Recompute objective values using simulation

Use:

python simulation/recompute_simulation.py

📊 Included Plots

The plots/ folder includes visualisations:

LSTM vs Simulation Objective Scatter Plot

Surrogate-Based vs Simulation-Based Pareto Fronts

Hypervolume Convergence Curves

Parameter Space Clustering

These figures were used in the dissertation results chapter.

📁 Dataset

The project uses a proprietary dataset provided by J&C Bachmann, containing:

200,000 simulation samples

70 input variables

Corresponding objective values (F1, F2)

This dataset cannot be published due to confidentiality constraints.

✨ Key Features

Fully modular codebase

Supports rapid surrogate evaluation

Parallelisable simulation evaluation

NSGA-III multi-objective optimiser

JSON-based result storage

Reproducible LHS experiment generation

👨‍💻 Author

Dhairya Bhavesh Shah
MSc Data Science (Business & Management)
University of Manchester

🤝 Industry Collaboration

This work was completed with support from:

J&C Bachmann GmbH, Germany
Special thanks to Michael Cipold (Head of Software Engineering) for technical guidance and provision of simulation datasets.
