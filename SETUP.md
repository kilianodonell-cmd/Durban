# Quick Setup Guide

## 1. Get the Code

```bash
git clone <repository-url>
cd Durban
```

## 2. Choose Your Environment

### 🌐 **Google Colab (Easiest)**
- Click the "Open in Colab" button in any notebook
- All packages install automatically
- Requires data in Google Drive at `/MyDrive/Durban/`

### 💻 **Local Machine**

**Linux/Mac:**
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**Windows (PowerShell):**
```powershell
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

**Or use Conda:**
```bash
conda create -n durban python=3.11
conda activate durban
pip install -r requirements.txt
```

## 3. Organize Your Data

```
Durban/
├── config.json
├── data/
│   ├── reference/
│   │   ├── Major_Catchments_*.gpkg
│   │   ├── eThekwini_Municipal_Boundary_*.gpkg
│   │   ├── mzinyati_buildings.gpkg
│   │   ├── Street_Address_*.gpkg
│   │   └── ...more reference layers...
│   ├── group_a_hazards/
│   │   ├── landslide_susceptibility.tif
│   │   ├── S30E030_FABDEM_V1-2.tif
│   │   ├── flood_extents.tif
│   │   └── community_hazard_map.tif
│   ├── group_b_infrastructure/
│   ├── group_c_socioeconomic/
│   ├── group_d_community/
│   └── group_d_environmental/
└── outputs/  (created automatically)
```

## 4. Run the Analysis

**Quick start (one command):**
```bash
jupyter notebook Durban_MCA.ipynb
```

**Or run specific notebook:**
```bash
jupyter notebook Field_Map.ipynb
```

## 5. Edit Configuration (Optional)

Edit `config.json` to:
- Change coordinate reference system (CRS)
- Adjust raster cell size
- Modify suitability color scheme
- Add/remove scenarios

Edit **Cell 2** in `Durban_MCA.ipynb` to:
- Add new factors
- Change AHP weights
- Adjust scoring thresholds

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `config.json not found` | Ensure it's in the same directory as the notebooks |
| `ModuleNotFoundError` | Run `pip install -r requirements.txt` |
| `FileNotFoundError: data/...` | Check that files match the structure in `config.json` |
| Slow processing | Reduce `cell_size_m` in config.json or use smaller AOI |

## Full Documentation

See [README.md](README.md) for:
- Detailed methodology
- Data source documentation
- Complete troubleshooting guide
- Citation information

---

**✓ Ready to run!** Start with `Durban_MCA.ipynb`, then `Field_Map.ipynb`
