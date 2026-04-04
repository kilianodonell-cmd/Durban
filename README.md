# Durban Housing Suitability Analysis

Multi-Criteria Analysis (MCA) for evaluating housing suitability in the Mzinyati Stream Catchment, eThekwini Municipality, South Africa.

**Citation Information:** Add DOI/citation here once published.

## Overview

This analysis integrates spatial data across multiple domains (hazards, infrastructure, socioeconomic factors, community input, and environmental conditions) to identify areas suitable for housing development using an Analytic Hierarchy Process (AHP) methodology.

### Key Notebooks

1. **Durban_MCA.ipynb** — Main analysis pipeline
   - Loads and processes geospatial data
   - Applies AHP weighting for multi-criteria evaluation
   - Generates suitability rasters for multiple scenarios
   - Outputs scored rasters and vector data

2. **Field_Map.ipynb** — Interactive field mapping tool
   - Generates a tablet-friendly interactive HTML map
   - Layers suitability scores with satellite imagery
   - Displays building footprints and constraint areas
   - **Requires outputs from Durban_MCA.ipynb**

## Data Requirements

### Directory Structure

```
Durban/
├── config.json                          # Configuration (paths, parameters)
├── Durban_MCA.ipynb                     # Main analysis
├── Field_Map.ipynb                      # Field mapping tool
├── README.md                            # This file
├── .gitignore                           # Git ignore patterns
├── data/
│   ├── reference/                       # Reference layers (always needed)
│   │   ├── Major_Catchments_*.gpkg
│   │   ├── eThekwini_Municipal_Boundary_*.gpkg
│   │   ├── Urban_Development_Line_*.gpkg
│   │   ├── mzinyati_buildings.gpkg
│   │   └── Street_Address_*.gpkg
│   ├── group_a_hazards/                 # Load these from Google Drive or local sources
│   │   ├── landslide_susceptibility.tif
│   │   ├── S30E030_FABDEM_V1-2.tif      # DEM for slope calculation
│   │   ├── flood_extents.tif
│   │   └── community_hazard_map.tif
│   ├── group_b_infrastructure/          # Infrastructure layers
│   │   ├── Roads_*.gpkg
│   │   ├── Fixed_Clinics_*.gpkg
│   │   ├── Mobile_Clinics_*.gpkg
│   │   ├── Hospitals_*.gpkg
│   │   ├── Fire_Stations_*.gpkg
│   │   ├── water_network.gpkg
│   │   └── electricity_network.gpkg
│   ├── group_c_socioeconomic/           # Socioeconomic layers
│   │   ├── settlements.gpkg
│   │   └── Prime_Investment_Corridor_p244.jpg
│   ├── group_d_community/               # Community input
│   │   └── community_hazard_map.tif
│   └── group_d_environmental/           # Environmental layers
│       └── [environmental data]
└── outputs/                             # Generated outputs (gitignored)
    ├── clipped/                         # Clipped input layers
    ├── rasters/                         # Scored rasters
    ├── outputs/                         # Vector outputs
    ├── field_map.html                   # Interactive map
    └── field_map_config.json            # Field map configuration
```

## Installation & Setup

### Option 1: Google Colab (Recommended for Testing)

Google Colab provides a free, pre-configured environment with all dependencies.

1. Open the notebook in Colab using the "Open in Colab" button at the top
2. Run the cells in order:
   - **Cell 1** (packages) — Installs required Python packages
   - **Cell 2** (mount drive) — Connects to your Google Drive
   - **Cell 3+** (analysis) — Run through all cells sequentially
3. Data must be organized in Google Drive at: `/MyDrive/Durban/data/` and `/MyDrive/Durban/outputs/`

### Option 2: Local Installation (Linux/Mac/Windows)

1. **Clone or download the repository:**
   ```bash
   git clone <repository-url>
   cd Durban
   ```

2. **Create a Python virtual environment:**
   ```bash
   # Using venv
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate

   # Or using conda
   conda create -n durban python=3.11
   conda activate durban
   ```

3. **Install dependencies:**
   ```bash
   pip install geopandas matplotlib contextily fiona pyproj rasterio scipy \
               matplotlib-scalebar folium pillow numpy pandas jupyter
   ```

4. **Organize data locally:**
   ```bash
   # Create data directory structure
   mkdir -p data/{reference,group_a_hazards,group_b_infrastructure,group_c_socioeconomic,group_d_community,group_d_environmental}
   mkdir -p outputs/{clipped,rasters,outputs}
   
   # Place your data files in the appropriate folders
   ```

5. **Run Jupyter:**
   ```bash
   jupyter notebook Durban_MCA.ipynb
   ```

## Running the Analysis

### Workflow

1. **Edit configuration (if needed):**
   - Open `config.json` to adjust paths, CRS, cell size, scenarios, etc.
   - Edit Cell 2 in `Durban_MCA.ipynb` when adding/removing factors

2. **Run Durban_MCA.ipynb:**
   - All intermediate outputs saved to `outputs/`
   - Final suitability rasters: `outputs/rasters/suitability_*.tif`
   - Constraint mask: `outputs/rasters/constraint_mask.tif`

3. **Run Field_Map.ipynb:**
   - Generates `outputs/field_map.html`
   - Open in a browser or transfer to a tablet for field use

## Configuration

Edit `config.json` to customize:

- **Paths**: Local vs. Colab paths are auto-detected—no manual switching needed
- **CRS**: Coordinate reference system (default: EPSG:32736 — UTM Zone 36S)
- **Cell size**: Raster resolution in meters (default: 30m)
- **Scenarios**: Add/edit scenarios and their AHP weightings in Cell 2 of Durban_MCA.ipynb
- **Colors**: Suitability color scheme (diverging red-blue by default)

## Data Sources

All reference data should be sourced from authoritative providers:

| Layer | Source | Notes |
|-------|--------|-------|
| Catchments | South African National Data Repository | [Link needed] |
| Boundary | eThekwini Municipality / National GIS Database | [Link needed] |
| Buildings | OpenStreetMap or Municipal Database | Must be georeferenced |
| DEM | FABDEM or SRTM | 30m resolution recommended |
| Landslide Susceptibility | [Source] | Pre-processed, 1-5 score |
| Flood Extents | [Source] | Pre-processed, 1-5 score |
| Infrastructure | Municipal/OpenStreetMap | Use most recent data available |

## Transparency & Reproducibility

This project follows **open science principles**:

- ✅ **All code is open source** (see LICENSE)
- ✅ **Configuration is explicit** in `config.json`
- ✅ **Data inputs are documented** (see Data Sources section)
- ✅ **Methods are transparent** (see Cell comments in notebooks)
- ✅ **Results are reproducible** with the same input data
- ⚠️ **Sample data not included** — users must obtain and organize their own

## Methodology

### Analytic Hierarchy Process (AHP)

The analysis uses AHP to combine multiple criteria into suitability scores:

1. **Factors** are grouped by domain (hazards, infrastructure, socioeconomic, etc.)
2. **Pairwise comparisons** are defined in Cell 2, establishing relative importance
3. **AHP weights** are calculated from the comparison matrix
4. **Suitability scores** (1-5) are assigned to each factor based on thresholds
5. **Scenarios** combine factors with different weightings to test sensitivity

### Scoring

Each factor is scored 1-5:
- **1** = Worst suitability (avoid if possible)
- **3** = Moderate suitability
- **5** = Best suitability (ideal)

Thresholds are editable in the `scoring` parameter of each factor definition.

## Output Files

| File | Description |
|------|-------------|
| `outputs/rasters/suitability_*.tif` | UInt8 raster, 1-5 suitability scores per scenario |
| `outputs/rasters/constraint_mask.tif` | Binary mask of excluded areas |
| `outputs/clipped/*.tif` | Individual scored factor rasters |
| `outputs/clipped/*.gpkg` | Individual clipped vector layers |
| `outputs/field_map.html` | Interactive map for field use |
| `outputs/field_map_config.json` | Configuration used by Field_Map.ipynb |

## Troubleshooting

### "FileNotFoundError: config.json not found"
- Ensure `config.json` is in the same directory as the notebook
- Check that paths in `config.json` match your actual data structure

### "google.colab module not found"
- You are running locally, which is fine
- The notebook will automatically skip Google Drive mounting
- Ensure `config.json` has correct local paths

### "ModuleNotFoundError: geopandas"
- Install missing packages: `pip install geopandas`
- Or in Colab, the first cell will install them automatically

### Slow raster processing
- Reduce `cell_size_m` in config.json for faster processing (less accurate)
- Process smaller AOI boundaries
- Use a local SSD or increase available RAM

## Contributing

To contribute improvements:

1. Fork or clone the repository
2. Create a feature branch
3. Document your changes clearly
4. Test on both Colab and local environments
5. Submit a pull request with a description

## License

[Add your license here — MIT/CC-BY/etc.]

## References

- Saaty, T. L. (1980). *The Analytic Hierarchy Process*. McGraw-Hill.
- [Add other key references]

## Contact

For questions or issues:
- **Author**: Kiliano O'Donnell
- **Institution**: [Your Institution]
- **Email**: [Your Email]

---

**Last updated**: April 2026
