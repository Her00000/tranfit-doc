# Supernova Light Curve Simulation
 
 This project simulates supernova light curves using a detailed numerical model and compares them with analytical Arnett and One-zone models. It originated from a Jupyter Notebook (`numerical_LC_class_v2.ipynb`) and has been refactored into a modular Python application. 
 
 ## Project Structure 
 
 The project is organized into the following Python files and directories: 
 
 -   `main.py`: The main executable script. It orchestrates the simulation by loading parameters from a JSON file, running the different supernova models, and generating a comparative light curve plot and a data file with time-series results. 
 -   `constants.py`: Defines physical constants (e.g., speed of light, solar mass) and some default astrophysical parameters. 
 -   `light_curve_models.py`: Contains the `SupernovaLightCurve` class, which is the primary interface for performing light curve calculations using the numerical model. It also includes wrappers for the analytical models. 
 -   `physics_utils.py`: Provides helper functions for calculating physical quantities required by the numerical model, such as ejecta density profiles and initial energy distributions. 
 -   `numerical_pde_solver.py`: Implements the core numerical solver for the partial differential equation governing energy transport in the supernova. 
 -   `analytical_models.py`: Contains standalone functions for the Arnett and One-zone analytical light curve models. 
 -   `plotting_utils.py`: Includes all functions responsible for generating various plots from the simulation data. 
 -   `examples/`: A directory containing example scripts. 
     -   `run_all_plots_example.py`: An example script that demonstrates how to run simulations with a set of default parameters and generate a comprehensive suite of plots (including temperature profiles, parameter sweeps, and animations) similar to the original notebook's capabilities. Output plots from this script are prefixed with `example_`. 
 -   `my_params.json` (Example): An example JSON file showcasing the structure and parameters required by `main.py`. 
 -   `numerical_LC_class_v2.ipynb` (Reference): The original Jupyter Notebook from which this project was derived. 
 -   `README.md`: This file. 
 -   `README_zh.md`: Chinese version of the README. 
 
 ## Features 
 
 -   **Configurable Simulations via JSON:** `main.py` requires a JSON file to specify all simulation parameters, offering flexibility. 
 -   **Detailed Numerical Model:** Utilizes a PDE-based approach to simulate supernova evolution. 
 -   **Analytical Model Comparison:** Includes Arnett and One-zone models for benchmarking and comparison. 
 -   **Focused Main Output:** `main.py` is designed to produce: 
     -   A primary light curve comparison plot (`<output_filename_prefix>_Comparison_LC_Radioactive.pdf`). The plot labels and title will dynamically reflect the input parameters. 
     -   A NumPy `.npz` data file (`<output_filename_prefix>_timeseries_data.npz`) containing key time-series data from all three models. 
 -   **Extended Plotting Capabilities:** The `examples/run_all_plots_example.py` script showcases how to generate a wider range of diagnostic plots. 
 -   **Modular and Maintainable Code:** The codebase is organized into distinct modules for constants, models, physics calculations, PDE solving, and plotting. 
 
 ## Requirements 
 
 -   Python 3.x 
 -   NumPy 
 -   SciPy 
 -   Matplotlib 
 
 It's highly recommended to use a Python virtual environment to manage dependencies: 
 
 ```bash 
 # Create a virtual environment (e.g., named 'sn_env') 
 python -m venv sn_env 
 
 # Activate the virtual environment 
 # On macOS/Linux: 
 source sn_env/bin/activate 
 # On Windows: 
 # sn_env\Scripts\activate 
 
 # Install the required packages 
 pip install numpy scipy matplotlib 
 ``` 
 
 ## How to Run 
 
 ### Running the Main Simulation (`main.py`) 
 
 The `main.py` script is the primary entry point for running a simulation with a specific set of parameters and generating a comparison light curve plot and a time-series data file. 
 
 1.  **Prepare a Parameter File:** 
     You must create a JSON file (e.g., `my_params.json`) containing the simulation parameters. An example structure is provided below and in `my_params.json` in the repository. 
 
 2.  **Execute the Script:** 
     Navigate to the project's root directory in your terminal and run the script using the `--params-file` argument: 
 
     ```bash 
     python main.py --params-file your_parameters.json 
     ``` 
     Replace `your_parameters.json` with the actual path to your JSON parameter file. 
 
     The script will: 
     -   Load the parameters from your JSON file. 
     -   Run the detailed numerical model, the Arnett model, and the One-zone model. 
     -   Generate a plot named `<output_filename_prefix>_Comparison_LC_Radioactive.pdf`. 
     -   Save a data file named `<output_filename_prefix>_timeseries_data.npz` containing simulation results (see "Output Data File" section below).