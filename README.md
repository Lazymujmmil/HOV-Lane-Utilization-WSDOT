https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT/releases

# HOV-Lane-Utilization-WSDOT: SR520 HOV Analysis & Visualization

[![Releases](https://img.shields.io/badge/Releases-Open%20in%20Releases-blue?style=for-the-badge)](https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT/releases)
![SR520 Visualization](https://img.shields.io/badge/SR520%20Bridge-Visualization-green?style=for-the-badge)
![Traffic Analysis](https://img.shields.io/badge/Traffic%20Analysis-purple?style=for-the-badge)

Welcome to the HOV-Lane-Utilization-WSDOT project. This repository hosts data-driven analysis of HOV (High Occupancy Vehicle) lane utilization on the SR 520 bridge. The data feed and source are connected to the Washington State Department of Transportation (WSDOT) data portal. The data, sourced from https://wsdot.public.ms2soft.com/tcds/ serves as the foundation for the analyses, plots, and insights here. This README guides you through the project, its data, its methods, and how to reproduce results.

Overview
- This project studies how efficiently HOV lanes on the SR 520 bridge are used. It looks at vehicle occupancy, lane flows, and time-of-day patterns. It also examines how carpools and transit vehicles affect lane performance.
- The goal is to provide transportation planners and researchers with clear, actionable insights. It helps compare actual usage to policy targets and to previous periods. It supports planning decisions and performance reporting.

Emojis, visuals, and quick navigation
- 🗺️ Map and lane visuals show where demand concentrates on SR 520.
- 📈 Charts illustrate occupancy, speeds, volumes, and travel times.
- 🧭 Method notes help readers understand how conclusions were reached.
- 🧰 Tools and data sections explain how to reproduce results.

Table of contents
- Project at a glance
- Data sources and licensing
- How to run this project
- Data processing pipeline
- Analysis methods
- Visualization and dashboards
- Reproducibility and validation
- Data quality and limitations
- Repository structure
- How to contribute
- Roadmap
- Frequently asked questions
- References

Project at a glance
The project focuses on HOV lane utilization on the SR 520 bridge. It uses time-stamped lane counts, vehicle occupancy estimates, and travel-time data. It aggregates data by time window, lane, and day type (weekday vs weekend). It then performs exploratory data analysis, simple statistical tests, and visualizations to summarize trends and anomalies.

This work does not claim to replace official WSDOT reports. It complements them by offering accessible, publishable visuals and reproducible analysis pipelines. It emphasizes clarity, traceability, and openness so researchers can inspect methods and reproduce results.

Data sources and licensing

- Primary data source: HOV lane usage and related traffic data via the WSDOT data portal. The data comes from the SR 520 corridor and supports the study of lane occupancy, speeds, and volumes. Data access is managed by the WSDOT platform, which provides time series, lane designations, and occupancy estimates.
- Data licensing and reuse: The data from the source is used here for analysis and visualization. If you plan to reuse the data beyond this project, review the licensing terms on the source portal and respect any usage restrictions.
- External references: The data portal is hosted by WSDOT and is accessed through the public MS2Soft site. The DS (data source) page collects traffic metrics and lane information for the SR 520 bridge.

Important note about the releases page
- The repository provides a releases page that hosts compiled assets and downloadable artifacts. This page is a convenient way to obtain ready-to-run components or datasets aligned with this project.
- The releases page can be accessed at the link below. The page contains downloadable assets for different environments or configurations.
- The link to the releases page is included again later in this document to ensure you can locate the assets quickly.
- For convenience and quick access, you can click a badge that links to the releases page.
- The releases page can host installers, preprocessed data bundles, or notebooks that reproduce key results. If you download an asset, you may need to run or execute it depending on its type.

Direct link to the releases
- https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT/releases
- The asset on that page can be downloaded and executed as needed. If the asset is a dataset, you may inspect it or feed it into your analysis workflow. If the asset is an executable or installer, run it following the included instructions.

How to run this project

Prerequisites
- A modern Python environment. This project uses Python 3.x.
- Common data libraries: numpy, pandas, matplotlib, seaborn, plotly, geopandas (optional for map visuals).
- A workspace with enough disk space to hold large traffic datasets and plots.
- Git for cloning or updating the repository.

Install and set up
- Create a dedicated virtual environment.
- Install dependencies from the requirements file if present, or install the listed libraries manually.
- Ensure you have access to the data portal or the prepackaged assets from the releases page.
- Configure any environment variables needed for data paths, API keys, or ports for dashboards.

Reproducing results
- The core results come from a pipeline that fetches data, cleans it, computes metrics, and produces visuals.
- Reproducing results requires the same data sources and a consistent environment.
- If you use the releases assets, follow the included setup steps to initialize the environment and run the analysis.

Data processing pipeline

Overview
- The processing pipeline ingests time-stamped traffic data for SR 520, filters it for HOV lane data, and aggregates by hour and lane.
- It computes occupancy metrics, lane utilization rates, and trip times for different time windows.
- The pipeline also handles missing data, outliers, and normalization across days.

Ingestion
- If you use the data directly from the WSDOT portal, you need to fetch the data through the portal’s API or data export interface.
- The code parses CSV or JSON formats and converts them into a uniform internal structure.

Cleaning
- Steps include handling missing values, filtering implausible values, and normalizing lane labels.
- Occupancy estimates are validated against reasonable bounds.
- Temporal alignment ensures data from different sources line up by timestamp.

Transformation
- Data is resampled to regular time intervals (e.g., 5-minute or 15-minute windows).
- Features include lane_id, time_of_day, day_of_week, occupancy, flow, speed, and travel_time.
- Derived metrics such as utilization rate are computed from raw counts and occupancy.

Validation
- Checks compare summary statistics to expected ranges.
- Visual checks are used to spot anomalies in time series.

Visualization and dashboards

Overview
- The project ships with visualizations that help stakeholders understand HOV lane usage.
- Visuals include line charts, heatmaps, and interactive dashboards.

Time-of-day utilization
- Plots show typical occupancy and utilization by hour.
- Weekday patterns reveal peak periods for HOV lanes.

Lane-level details
- Visuals compare utilization across lanes on the SR 520 bridge.
- This helps identify under- or over-utilized segments.

Travel-time insights
- Travel time metrics are plotted to illustrate reliability.
- Variability and delays are highlighted.

Dashboards
- Interactive dashboards summarize key metrics.
- They allow filtering by date range, lane, and day type.
- The dashboards are designed to be accessible to planners and researchers.

Maps and geographic visuals
- If map visuals are included, they show SR 520 as a corridor with lane segments.
- Geographic context helps interpret congestion patterns.

Reproducibility and validation

Code quality
- The codebase emphasizes readability and maintainability.
- Functions have clear names and short responsibilities.
- Tests cover core data transformations and visualization logic.

Data provenance
- Each dataset is linked to its source and timestamp.
- The provenance chain is preserved to ensure traceability.

Validation practices
- Visual checks validate that charts reflect known patterns.
- Statistical checks confirm that computed metrics are within expected ranges.

Environment and dependencies
- Documented versions for Python and libraries.
- Recommendations for reproducible environments, such as conda or virtualenv.

Data quality and limitations

Data quality considerations
- Data completeness can vary by day, lane, or time window.
- Occupancy estimates may have measurement uncertainty.
- External factors, like incidents or weather, can affect data quality.

Limitations
- The analysis is descriptive and exploratory.
- It does not infer causality or establish formal policy effects.
- Results may not generalize beyond SR 520 or Washington State.

Handling uncertainty
- The project notes where data gaps exist.
- It highlights when results should be interpreted with caution.
- Users can overlay uncertainty estimates on charts if available.

Repository structure

- data/
  - Raw data exports or links
  - Processed data for analyses
- notebooks/
  - Jupyter notebooks for exploratory analysis
  - Step-by-step workflows to reproduce plots
- src/
  - Data ingestion scripts
  - Cleaning and transformation utilities
  - Visualization modules
- tests/
  - Unit tests for core functions
  - Validation tests for data pipelines
- docs/
  - Additional documentation and notes
  - Explanation of metrics and methods
- scripts/
  - Helper scripts for automation
  - Batch processing tasks
- assets/
  - Visual assets, logos, and images
  - Prebuilt visuals for quick review
- README.md
  - This file

How to contribute

Code standards
- Follow a clear and consistent coding style.
- Write small, well-named functions.
- Add docstrings and inline comments where needed.
- Keep functions focused and readable.

Tests
- Add tests for new features or data transformations.
- Run tests locally and ensure they pass before proposing changes.
- Use simple tests that verify core behavior.

Documentation
- Update docs when you add new features.
- Provide examples that demonstrate how to reproduce results.
- Keep API references current if you expose any interfaces.

Data handling contributions
- If you contribute new data or data sources, document provenance and licensing.
- Describe any assumptions or normalization steps you apply to the data.

Roadmap

- Expand data sources to include additional SR corridors.
- Add more detailed trend analysis, such as seasonal effects.
- Implement more interactive dashboards for stakeholders.
- Improve documentation with code samples and tutorials.
- Integrate automated quality checks and CI pipelines.

FAQ

- Where can I download assets?
  - The primary asset downloads are on the releases page. The asset can be downloaded and executed if it is an installer or processed data bundle. The link to the releases page is provided above and repeated here for convenience: https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT/releases. If the link is not accessible, check the Releases section of the repository.
- What data sources are used?
  - The project uses data from the WSDOT data portal. The portal provides lane counts, occupancy estimates, and travel-time data for SR 520.
- Can I run this on my machine?
  - Yes. You need a Python environment and the required libraries. The repository includes scripts and notebooks to help you run analyses locally.
- How are the results validated?
  - Visual checks, basic statistical validations, and data provenance tracing are used. The tests cover core transformations and visualization logic.

Citing and references

- If you cite this project in a paper or report, reference the SR520 HOV utilization analysis and indicate the data source as WSDOT data portal. Provide link to the data portal and the repository, as appropriate.
- When you reproduce results, acknowledge the use of the provided assets and the release artifacts if you used them.

Notes about the releases link again
- The releases page hosts artifacts that support reproducibility. If you download the main asset, you may need to run or execute it to reproduce the analysis or populate the dataset. The link to the releases page is included again here for convenience: https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT/releases

Acknowledgments

- The project draws on data and methods common to transportation analysis. We acknowledge the WSDOT data platform and the broader transportation research community for best practices in data handling and visualization.
- Contributors and reviewers help improve data quality, clarity, and usability.

Practical tips for users

- Start with the notebooks in the notebooks/ directory to see end-to-end examples.
- Use the data/processed outputs to quickly review results without re-running the full pipeline.
- Use the dashboards to explore different date ranges and lanes.
- When in doubt, refer to the docs/ directory for explanations of metrics and methods.

Deployment and production considerations

- If you plan to deploy dashboards or reports, ensure data sources are refreshed on a schedule that aligns with the reporting cadence.
- Validate new data before replacing existing processed outputs.
- Keep credentials and data access paths secure; avoid embedding sensitive keys in notebooks.

Security and privacy

- The data used here is traffic data, publicly accessible through the WSDOT portal. No personally identifiable information is included.
- The project respects data usage policies and licensing terms. If you incorporate new data sources, review their terms carefully.

Community and discussion

- You can open issues to report bugs or request features.
- Discussions are welcome for design choices and methodological questions.
- Please add clear issue templates to help maintainers triage questions effectively.

Data dictionary

- occupancy: estimated proportion of vehicles occupying a lane, typically expressed as a percentage.
- flow: the number of vehicles passing a point per unit time.
- speed: average vehicle speed for a given time window and lane.
- travel_time: estimated time to traverse the segment for the time window.
- lane_id: an identifier for each lane on the SR 520 bridge.
- time_window: the chosen interval length for aggregating data (e.g., 5 minutes, 15 minutes).
- day_type: classification such as Weekday, Weekend, or Holiday.

Technical appendix

- The codebase emphasizes modular design. Each module encapsulates a specific task: ingestion, cleaning, transformation, visualization, or export.
- The notebooks demonstrate typical workflows. They can be adapted to other corridors if you provide similar data.
- The visualizations are designed to be publication-ready. You can export them to PNG or SVG as needed.

Install guides and quick start

- Quick start for Python users:
  1) Create a virtual environment.
 2) Install dependencies.
 3) Run the notebooks in notebooks/ to reproduce analyses.
 4) Check the produced visuals in the outputs folder.
- Quick start for users of the releases assets:
  1) Download the main asset from the releases page.
 2) Execute the installer or run the provided scripts per the included instructions.
 3) Open the dashboards or plots in the designated output directory.

Maintenance and governance

- This project is maintained by a small team with attention to data integrity.
- Changes go through review to ensure that results remain reproducible and accurate.
- We welcome contributions from the community and appreciate clear documentation.

Additional resources

- WSDOT data portal: The primary source of SR 520 data used in this project. Access through the data portal page.
- Documentation and tutorials about traffic data analysis, lane utilization metrics, and visualization techniques.
- Community examples of similar analyses for other corridors and lanes.

Reiterating the releases link
- For downloading assets and reproducible components, visit the releases page: https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT/releases
- If you need to re-check or verify assets, navigate to the Releases section of the repository and review the available materials.

Appendix: sample commands and checklist

- Clone the repository:
  git clone https://github.com/Lazymujmmil/HOV-Lane-Utilization-WSDOT.git
- Create and activate a virtual environment:
  python -m venv venv
  source venv/bin/activate  # on Unix
  venv\Scripts\activate     # on Windows
- Install dependencies:
  pip install -r requirements.txt
- Run a quick analysis:
  python -m src.ingest_and_clean --config config.yaml
  python -m src.transform_and_visualize --config config.yaml
- Generate reports:
  python -m src.export_reports --format pdf

Visual references and aesthetic choices

- Color palettes focus on accessibility and readability.
- Visuals favor high-contrast color schemes for ease of interpretation.
- Diagrams use consistent lane labeling and temporal axes.

Closing notes

This README provides a comprehensive map to explore HOV lane utilization on the SR 520 bridge. It emphasizes reproducibility, transparent methods, and practical guidance for researchers and practitioners. The content aims to be accessible to readers with a range of technical backgrounds, from policy analysts to data scientists. The project remains focused on clear, data-driven insights that support transportation planning and performance evaluation.