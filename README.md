# IPA
A simplified model for racemization
# README

## Simulation Model for Peptide Decay and Racemization

### Overview

This simulation model is designed to study the decay and racemization of a peptide polymer over time. It uses a simplified model with three amino acids: A (apolar residues), P (polar residues), and I (internal racemization residues). The model tracks the breakdown of peptide bonds, the formation of free amino acids, and the racemization (conversion between L and D forms) of these amino acids. Multiple simulations are run to average the results, providing smoother and more reliable data.

### Key Features

- **Peptide Decay**: Simulates the hydrolysis of peptide bonds in the polymer, resulting in smaller fragments over time.
- **Racemization**: Simulates the racemization of amino acids, converting between L and D forms at different rates for free and bound amino acids.
- **Multiple Simulations**: Runs multiple simulations with the same initial polymer to average the results and reduce random fluctuations.
- **Threshold for D/L Ratio Detection**: Applies a threshold to avoid choppy output when the numbers of free amino acids are very low.

### Model Components

#### Constants and Parameters

- **LEN**: Length of the initial polymer.
- **H**: Base hydrolysis rate.
- **HYDL_SCALE_RATE**: Factor to scale the hydrolysis rates for different bond types.
- **R, R_FAST, R_FREE**: Racemization rates for in-chain, fast racemizing amino acids, and free amino acids respectively.
- **BOND_RATES**: Dictionary containing the hydrolysis rates for different types of peptide bonds.
- **L_AMINO_ACIDS, D_AMINO_ACIDS**: Lists of L and D forms of the amino acids.
- **DL_THRESHOLD_PERCENTAGE**: Minimum percentage of free amino acids required to detect and plot the D/L ratio.

#### Functions

- **create_polymer(length)**: Generates an initial polymer sequence of given length using random L amino acids.
- **racemize(aa, is_free)**: Simulates racemization of an amino acid, considering whether it is free or part of a chain.
- **decay_step(fragment)**: Simulates a single step of peptide bond hydrolysis, creating new fragments.
- **count_amino_acids(sequence)**: Counts the number of each type of amino acid in a sequence.
- **simulate_decay_and_racemization(initial_polymer, time_steps)**: Runs the decay and racemization simulation for a single polymer over a specified number of time steps.
- **average_simulations(simulations)**: Averages the results from multiple simulations to produce smoother data.
- **calculate_dl_ratio(counts, aa)**: Calculates the D/L ratio for a given amino acid type, considering a threshold for detection.

#### Simulation Process

1. **Initialization**: Create an initial polymer sequence of length `LEN`.
2. **Multiple Simulations**: Run `num_simulations` simulations with the same initial polymer to average the results.
3. **Decay and Racemization**: For each time step, simulate bond hydrolysis and racemization, and track the resulting fragments and free amino acids.
4. **Data Collection**: Collect data on average peptide lengths, free amino acid counts, and total amino acid counts over time.
5. **D/L Ratio Calculation**: Calculate D/L ratios for total and free amino acids, applying a threshold for free amino acids to avoid low-number artifacts.
6. **Plotting and Analysis**: Plot the results to visualize the decay process, the formation of free amino acids, and the racemization dynamics.

### Plotting Results

- **Average Peptide Size**: Plots the average size of peptide fragments over time on a logarithmic scale.
- **Percentage of FAA Amino Acids**: Plots the percentage of free amino acids relative to the initial counts for each amino acid type.
- **D/L Ratio (THAA System)**: Plots the D/L ratio for each amino acid type in the total system over time.
- **D/L Ratio (FAA Amino Acids)**: Plots the D/L ratio for free amino acids, applying a threshold to ensure reliable detection.

### Final Statistics

The final statistics provide a summary of the total amino acid composition and D/L ratios for both the total system and the free amino acids at the end of the simulation.

### Output

Files are saved as `.csv`.

### Setup and Usage

#### Installation

1. Ensure you have Python installed on your system.
2. Install the required packages using the following command:
   ```bash
   pip install numpy pandas matplotlib scipy
   ```
3. Download the repository or clone it using:
   ```bash
   git clone <repository_url>
   ```

#### Running the Simulation

1. Mount Google Drive if running on Google Colab:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
2. Update the `file_path` variable with the path to your CSV file:
   ```python
   file_path = '/content/drive/MyDrive/Colab_Notebooks/AAR_Model/OES.csv'
   ```
3. Run the simulation by executing the script.

#### Customization

- Modify the initial polymer length (`LEN`) and other parameters in the constants section as needed.
- Adjust the hydrolysis and racemization rates based on your specific requirements.
- Add or modify functions to extend the simulation capabilities.

### Troubleshooting

- Ensure all required packages are installed.
- Verify the path to your CSV file is correct.
- Check for NaN or infinite values in the dataset and clean the data accordingly.

### License

This project is licensed under the MIT License.

### Acknowledgements

Special thanks to contributors and researchers who provided valuable insights and data for this project.
