# traffic-simulation
Python Stau-Simulation
stau-simulation/
│
├── README.md
├── requirements.txt
│
├── src/
│   ├── sim.py
│   └── utils.py
│
├── notebooks/
│   └── exploration.ipynb
│
├── results/
│   └── runs.csv
│
└── presentation/
    └── slides.pdf


# Stau-Simulation (Python)

Dieses Projekt simuliert den Verkehrsfluss auf einer einspurigen Straße
mithilfe eines einfachen zellulären Automaten.

## Features
- Einspurige Straße (Ring)
- Zufällige Startpositionen & Geschwindigkeiten
- Brems- und Beschleunigungsregeln
- Stauwellen sichtbar im Zeitpositionsdiagramm
- Reproduzierbarkeit (fixed random seed)

## Installation

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python src/sim.py
jupyter notebook
---

# 🧩 **requirements.txt**
---

# 🧠 **src/sim.py (fertig & funktionierend)**

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from tqdm import tqdm
from utils import initialize_cars, step

N_CARS = 30
ROAD_LENGTH = 200
STEPS = 200
SEED = 42

np.random.seed(SEED)

def run_sim():
    positions, velocities = initialize_cars(N_CARS, ROAD_LENGTH)
    trajectory = []

    for _ in tqdm(range(STEPS)):
        trajectory.append(positions.copy())
        positions, velocities = step(positions, velocities, ROAD_LENGTH)

    return np.array(trajectory)

if __name__ == "__main__":
    trajectory = run_sim()

    plt.figure(figsize=(10,5))
    plt.imshow(trajectory, aspect="auto", cmap="binary")
    plt.title("Stau-Simulation (Zeit vs Position)")
    plt.xlabel("Position")
    plt.ylabel("Zeit")
    plt.savefig("results/plot.png")
    plt.show()

    pd.DataFrame(trajectory).to_csv("results/runs.csv", index=False)
import numpy as np

V_MAX = 5
SLOWDOWN_PROB = 0.2

def initialize_cars(n_cars, road_length):
    positions = np.sort(np.random.choice(range(road_length), n_cars, replace=False))
    velocities = np.random.randint(0, V_MAX+1, n_cars)
    return positions, velocities

def step(positions, velocities, road_length):
    n = len(positions)
    new_velocities = velocities.copy()

    for i in range(n):
        if i < n-1:
            gap = positions[i+1] - positions[i] - 1
        else:
            gap = (road_length - positions[i]) + positions[0] - 1

        if new_velocities[i] < V_MAX:
            new_velocities[i] += 1

        if new_velocities[i] > gap:
            new_velocities[i] = gap

        if np.random.rand() < SLOWDOWN_PROB and new_velocities[i] > 0:
            new_velocities[i] -= 1

    new_positions = (positions + new_velocities) % road_length
    order = np.argsort(new_positions)
    
    return new_positions[order], new_velocities[order]
