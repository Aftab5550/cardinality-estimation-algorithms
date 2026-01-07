# Cardinality Estimation Algorithms (HLL & Recordinality)

A comparative study and implementation of **HyperLogLog (HLL)**, **Recordinality (REC)**, and **K-Minimum Values (KMV)** for cardinality estimation in data streams. This project evaluates these algorithms on real-world literary datasets (e.g., *Dracula*, *War and Peace*) and synthetic Zipfian streams to assess accuracy, scalability, and robustness to data skew.

## 📂 Repository Structure

```text
.
├── dracula.txt                 # All the 16 dataset files (8 .txt books and 8 .dat ground truths)
├── dracula.dat
├── ... (other datasets)
├── cardinality-estimation-algorithms.ipynb  # Main Jupyter Notebook with all code and experiments
├── requirements.txt            # Python dependencies
├── LICENSE                     # License file
└── README.md                   # Project documentation
```

## 🚀 Overview

Cardinality estimation (counting distinct elements) is a critical problem in Big Data. Storing every unique element requires linear memory $\mathcal{O}(N)$, which is unscalable for massive streams.

This project implements three probabilistic algorithms that use **constant memory** to estimate cardinality with small, predictable error:
1.  **HyperLogLog (HLL):** Uses harmonic averaging of register ranks (Industry Standard).
2.  **Recordinality (REC):** Uses order statistics (Record-breaking events).
3.  **K-Minimum Values (KMV):** Tracks the density of the $k$-smallest hash values (Bonus Implementation).

## 🛠️ Installation & Usage

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Aftab5550/cardinality-estimation-algorithms.git](https://github.com/Aftab5550/cardinality-estimation-algorithms.git)
    cd cardinality-estimation-algorithms
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the Notebook:**
    Open `cardinality-estimation-algorithms.ipynb` in Jupyter Lab or VS Code to reproduce all experiments, graphs, and tables.

## 📊 Key Results

### 1. Comparative Accuracy (Real-World Data)
Performance across 8 distinct literary works (average of 50 trials).
* **HLL ($m=1024$):** Consistent error ~2-3%.
* **REC ($k=128$):** Higher variance ~10-15%.
* **KMV ($k=128$):** Outperforms REC with same memory ~7%.

| Dataset | True $n$ | HLL Error % | REC Error % | KMV Error % |
| :--- | :--- | :--- | :--- | :--- |
| **Dracula** | 9,425 | **3.10%** | 12.38% | 7.50% |
| **War and Peace** | 17,475 | **2.05%** | 15.28% | 7.72% |
| **Don Quijote** | 23,034 | **2.57%** | 15.22% | 7.79% |

### 2. Robustness to Data Skew (The "Alpha Hypothesis")
We tested the algorithms on synthetic Zipfian data ($\alpha=0.0$ to $3.0$).
* **Result:** Accuracy is independent of data distribution. Hashing successfully "whitens" skewed data.
* **Failure Case:** Disabling the hash function caused **79% error** on skewed data, proving hashing is mathematically essential.

### 3. Scalability
* **HyperLogLog** becomes *more* accurate as cardinality grows (Error drops to ~4% at $n=50k$).
* **Recordinality** works best for small datasets where the buffer size $k$ covers a large portion of the universe.

## ⏱️ Experimental Rigor
The final batch of experiments was executed over **7 hours and 9 minutes**, processing millions of tokens across 50 independent trials per dataset to ensure statistical validity.

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
