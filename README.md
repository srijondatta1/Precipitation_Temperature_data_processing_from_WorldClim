# 🌍 Climate Data Processing Pipeline for WorldClim CMIP6 Data

This project contains a series of Jupyter notebooks that create a complete data processing pipeline. The goal is to download future climate projection data (temperature and precipitation) from WorldClim, extract data for specific geographical points, and format it into text files suitable for hydrological or environmental models.

The pipeline is executed by running the notebooks in sequential order.

**The next part of the processing of data like temporal or spatial downscalling will be available on https://github.com/sifatsiddik**

---

## 💻 Workflow & Notebooks

1.  **`1_Download_tiff.ipynb`**: Downloads future climate model data (`.tif` raster files) from the WorldClim server. This script is built to be resilient, using a multi-threaded, resumable approach to handle large downloads efficiently.
2.  **`2_Extraction_tiff_to_csv.ipynb`**: Extracts monthly time-series data from the downloaded `.tif` files for a predefined list of station coordinates. The extraction is geospatial, and the output for each raster is saved as a separate CSV file.
3.  **`3_Name_CSVs_Model_SSPs_parameters.ipynb`**: Parses the filenames of the extracted CSVs to intelligently group and combine them. Files are merged based on the climate model, SSP scenario (e.g., `ssp245`), and variable (`prec`, `tmin`, `tmax`).
4.  **`4_Check_missing_values_CSVs.ipynb`**: Performs the first data quality assurance step. It scans the combined CSV files to generate a summary report on missing or blank values.
5.  **`5_Convert_CSV_to_text.ipynb`**: Converts the processed and combined CSV files into tab-delimited `.txt` files, preparing the data for use in other modeling software that requires plain text input.
6.  **`6_Check_missing_values_Texts.ipynb`**: Conducts another quality check on the final `.txt` files, providing a high-level summary of rows, columns, and total missing values.
7.  **`7_Again_check_missing_values_Texts.ipynb`**: Performs a final, more detailed validation on the `.txt` files. It verifies that the column structure is correct and specifically checks for missing data within the monthly value columns.

---

## 🛠️ Technologies Used

* **Python 3.10**
* **Jupyter Notebook**
* **Core Libraries:**
    * `pandas` for data manipulation and analysis.
    * `rasterio` & `pyproj` for geospatial raster data processing.
    * `requests` for downloading data from the web.
    * `tqdm` for progress bar visualization.

---

## 🚀 How to Use

1.  **Clone the repository:**
    ```bash
    git clone <your-repository-url>
    ```
2.  **Create the environment:** Use Mamba or Conda to create the environment (assuming an `environment.yml` or `requirements.txt` file is present).
    ```bash
    mamba env create -f environment.yml
    ```
3.  **Activate the environment:**
    ```bash
    mamba activate climate-data-pipeline
    ```
4.  **Update file paths:** Before running, open the notebooks and update the input/output folder paths to match your system.
5.  **Run the notebooks:** Execute the notebooks sequentially from `1` to `7`.

---

## ⚠️ Development Philosophy & AI Acknowledgment

**As the primary maintainer, my goal for this project was to develop a robust, production-ready scientific pipeline for complex geospatial and hydrological analysis**.

The development of this workflow was assisted by Large Language Models (LLMs), including **Gemini, ChatGPT, Claude, and Copilot**, in addition to standard open-source documentation and web resources. This approach facilitated the orchestration of complex Python libraries (like `rasterio` and `pandas`) and the refinement of the core data processing logic, demonstrating a modern, efficient method for building scientific software.
