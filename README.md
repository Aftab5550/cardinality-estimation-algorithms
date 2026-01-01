# Cardinality Estimation Algorithms (HLL & Recordinality)

This repository contains the implementation and experimental study of two probabilistic cardinality estimation algorithms: **HyperLogLog** and **Recordinality**. 

This work was done for **Assignment #3** of the **Randomized Algorithms (RA-MIRI)** course.

## 📂 Project Structure

* `cardinality_estimation.ipynb`: The complete Jupyter Notebook containing the source code, data generator, and experiment drivers.
* `data/`: Folder containing the dataset files (e.g., `dracula.txt`, `dracula.dat`).
* `requirements.txt`: List of Python dependencies.

## 🚀 Setup & Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/cardinality-estimation-algorithms.git](https://github.com/YOUR_USERNAME/cardinality-estimation-algorithms.git)
    cd cardinality-estimation-algorithms
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    *Note: You may need to install `randomhash` directly from source if not in PyPI:*
    ```bash
    pip install git+[https://github.com/jlumbroso/python-random-hash.git](https://github.com/jlumbroso/python-random-hash.git)
    ```

## 🏃 Usage

### 1. Download Datasets
Download the datasets (e.g., `dracula.txt`, `dracula.dat`) from the course link and place them in the `data/` folder.

### 2. Run the Notebook
Open the notebook `cardinality_estimation.ipynb` using Jupyter Notebook, JupyterLab, or Google Colab.

Run all cells to:
1.  Load the data.
2.  Execute the **HyperLogLog** and **Recordinality** algorithms (10 trials).
3.  Generate the comparison tables and the Memory vs. Error impact plots.

## 🧪 Algorithms Implemented

### HyperLogLog (HLL)
* **Description:** Estimates cardinality using the maximum number of leading zeros in the binary representation of hash values.
* **Implementation:** Includes bias correction constants $\alpha_m$ as derived by Flajolet et al.
* **Parameters:** Configurable bit-width $b$ (memory $m = 2^b$).

### Recordinality (REC)
* **Description:** Estimates cardinality based on the number of times the set of $k$-smallest (or largest) hash values is updated (records).
* **Implementation:** Tracks the $k$-largest hash values (mathematically equivalent to $k$-smallest).
* **Parameters:** Configurable sample size $k$.

## 📚 References

1.  **HyperLogLog:** Ph. Flajolet, É. Fusy, O. Gandouet, and F. Meunier. "Hyperloglog: the analysis of a near-optimal cardinality estimation algorithm." *Analysis of Algorithms (AofA)*, 2007.
2.  **Recordinality:** A. Helmi, J. Lumbroso, C. Martínez, and A. Viola. "Data streams as random permutations: the distinct element problem." *Analysis of Algorithms (AofA)*, 2012.
3.  **Hash Functions:** J. Lumbroso. `python-random-hash` library. [GitHub Link](https://github.com/jlumbroso/python-random-hash).
