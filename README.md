# 🎯 Dartboard Monte Carlo Simulation

A beautiful and intuitive visualization of Monte Carlo simulation using a realistic dartboard representation. This project demonstrates probability theory and random sampling through an elegant, GitHub-ready Python implementation.

![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.0+-orange.svg)
![NumPy](https://img.shields.io/badge/NumPy-1.19+-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
<img width="1149" height="1190" alt="download" src="https://github.com/user-attachments/assets/4f1d1115-4d8f-40fc-8715-37ee604bda71" />

## 📋 Overview

This project visualizes the Monte Carlo method by simulating thousands of dart throws at a dartboard. Each throw is randomly generated, and the visualization helps understand:

- **Random sampling** and probability distributions
- **Monte Carlo estimation** techniques
- **Statistical convergence** through visual representation
- **Geometric probability** and hit detection

## ✨ Features

- 🎨 **Realistic dartboard design** with multiple concentric rings
- 🎯 **Segmented dartboard** with alternating colors (20 segments)
- 💫 **Color-coded visualization**:
  - Blue dots: Regular board hits
  - Orange dots: Inner bull hits
  - Green stars: Bullseye hits ★
  - Gray dots: Misses (outside board)
- 📊 **Real-time statistics** including accuracy and hit counts
- 🌙 **Modern dark theme** optimized for GitHub
- ⚡ **High-performance rendering** of 8,000+ data points

## 🚀 Getting Started

### Prerequisites

```bash
pip install numpy matplotlib
```

### Installation

1. Clone the repository:
```bash
git clone https://github.com/BUAksakal/dartboard-monte-carlo.git
cd dartboard-monte-carlo
```

2. Run the simulation:
```bash
python mcds_main.py
```

## 💻 Usage

Simply execute the script to generate the visualization:

```python
python dartboard_simulation.py
```

### Customization

You can easily modify simulation parameters at the top of the script:

```python
n_throws = 8000        # Number of dart throws
board_radius = 10      # Dartboard radius
bullseye_radius = 0.6  # Bullseye size
```

## 📊 Understanding the Output

The visualization includes:

1. **Dartboard Geometry**:
   - Outer ring (double scoring zone)
   - Triple ring (triple scoring zone)
   - Inner bull (green circle)
   - Bullseye (red center)

2. **Statistics Panel**:
   - Total throws
   - Board hits
   - Inner bull hits
   - Bullseye hits
   - Overall accuracy percentage

3. **Legend**:
   - Visual guide for different hit types
   - Color-coded categories

## 🧮 Mathematical Foundation

### Core Geometry

**1. Random Dart Generation:**
```python
x = np.random.uniform(-board_radius, board_radius, n_throws)
y = np.random.uniform(-board_radius, board_radius, n_throws)
```
- Darts are randomly thrown within a **square** boundary (-10 to +10)
- Each dart gets random (x, y) coordinates
- Uses **uniform distribution** - the foundation of Monte Carlo

**2. Distance Calculation:**
```python
distances = np.sqrt(x**2 + y**2)
```
- **Pythagorean theorem** in action!
- Distance from point (x, y) to center (0, 0): √(x² + y²)
- Example: point (3, 4) → √(9 + 16) = √25 = 5 units from center

**3. Zone Classification:**
```python
bullseye_hits = distances <= 0.6        # Center: radius 0.6
inner_bull_hits = 0.6 < distances <= 1.2  # Inner bull: radius 1.2
board_hits = distances <= 10.0           # Entire board: radius 10
```
- Each dart is classified by comparing its distance to zone radii
- Uses **boolean masking** for efficient categorization
- If distance ≤ 0.6 → Bullseye ★
- If 0.6 < distance ≤ 1.2 → Inner Bull
- If distance > 10 → Miss (outside board)

**4. Monte Carlo Estimation:**
```python
hits_on_board = np.sum(board_hits)
accuracy = (hits_on_board / n_throws) * 100
```
- **Law of Large Numbers**: As throws increase, accuracy converges to true probability
- Can estimate π using: π ≈ 4 × (hits in circle / total throws)
- Area of circle = πr², Area of square = (2r)²
- Ratio = πr² / 4r² = π/4

### Why This Works

The Monte Carlo method works because:
- **Random sampling** simulates real-world probability
- **Large numbers** (8,000 throws) give accurate estimates
- **Geometric probability**: ratio of areas = ratio of hits
- **Visual convergence**: more throws = clearer pattern

### Example Calculation

For a dart at position (6, 8):
```
Distance = √(6² + 8²) = √(36 + 64) = √100 = 10 units
Since 10 ≤ 10 (board radius) → HIT!
Since 10 > 1.2 (inner bull) → Regular board hit (blue dot)
```

---

⭐ **Star this repository** if you found it helpful!
