# Knee_Data: Carbon estimation of old-growth bald cypress knees using mobile LiDAR

Data and code accompanying:

> Tajudeen, T. T., Rathbun, L. C., Ardón, M., & Mitasova, H. (2025). Carbon estimation of old-growth bald cypress knees using mobile LiDAR. *Frontiers in Forests and Global Change*, 8, 1427376. https://doi.org/10.3389/ffgc.2025.1427376

## Overview

Bald cypress (*Taxodium distichum*) knees (pneumatophores) are woody, roughly conical structures that rise from the roots, and their contribution to wetland carbon stocks is poorly understood. This study used the LiDAR sensor of an Apple iPad Pro 12.9" to capture 3D point clouds of individual knees in the Three Sisters Swamp (Black River Reserve, Bladen County, North Carolina, USA). Knee volume was estimated with two point-cloud algorithms and compared against the traditional cone-based allometric estimate from field measurements.

**Methods compared**

- **C-hbS**: convex hull by slicing
- **CSH**: canopy surface height (grid-based)
- **Allometric**: cone volume from field-measured radius and slant height

**Key findings**

- LiDAR-derived knee height closely matched field-derived height (r = 0.98).
- Allometric volume was highly correlated with C-hbS (r = 0.90) and CSH (r = 0.88), but both algorithms gave larger volumes, especially for tall knees and knees with concavities or large basal buttresses.
- Mean knee wood density was 0.32 g/cm³ (SE 0.02).
- Estimated aboveground knee biomass was 61.9 ± 23.4 Mg ha⁻¹ and carbon was 32.83 ± 12.38 Mg C ha⁻¹ (carbon assumed to be 53.1% of biomass), at about 8,175 knees ha⁻¹.

## Data collection summary

Three non-overlapping scans were collected on 24 May 2023 (822.1 m² total) using the Polycam app (v3.0.1) and exported as LAS files. Each scan used three ground control points. In the field, 55 knees were measured (basal radius and slant height), and 15 knees were cored for wood density.

| Scan | Area (m²) | Points | Knees measured in field |
|------|-----------|-----------|-------------------------|
| A | 150 | 6,540,000 | 16 |
| B | 353 | 6,560,000 | 22 |
| C | 319 | 6,980,000 | 17 |

## Processing workflow

1. **Registration**: point clouds aligned to ground control points in CloudCompare (WGS84 / UTM Zone 17N).
2. **Ground classification**: Cloth Simulation Filter (CSF) in R, separating ground from above-ground points.
3. **Segmentation**: DBSCAN (scikit-learn) to isolate individual knees.
4. **Volume estimation**: C-hbS and CSH algorithms in Python (Jupyter Notebook).
5. **Biomass and carbon**: volume × wood density, scaled by knee density per hectare, with carbon at 53.1% of biomass.

## Repository contents

<!-- TODO: replace with the actual files and folders in this repo. Example structure: -->

```
Knee_Data/
├── point_clouds/     # LiDAR scans (.las), scans A-C
├── field_data/       # Field measurements of knees (radius, slant height)
├── wood_density/     # Core measurements for wood density
├── notebooks/        # Python/Jupyter notebooks (segmentation, C-hbS, CSH)
├── scripts/          # R script for CSF ground classification
└── README.md
```

## Software

- Polycam v3.0.1 (iPad Pro scanning)
- CloudCompare v2.13 alpha (registration)
- R (CSF ground filtering)
- Python with Jupyter Notebook and scikit-learn (segmentation and volume estimation)

## Citation

If you use these data or code, please cite the paper:

```bibtex
@article{tajudeen2025knees,
  author  = {Tajudeen, Titilayo T. and Rathbun, Leah C. and Ard{\'o}n, Marcelo and Mitasova, Helena},
  title   = {Carbon estimation of old-growth bald cypress knees using mobile {LiDAR}},
  journal = {Frontiers in Forests and Global Change},
  volume  = {8},
  pages   = {1427376},
  year    = {2025},
  doi     = {10.3389/ffgc.2025.1427376}
}
```

## Funding

Summerville Family Forest Research Award (2021) and the Department of Forestry and Environmental Resources, College of Natural Resources, North Carolina State University.

## Contact

Titilayo T. Tajudeen, Department of Forestry and Environmental Resources, North Carolina State University.

## License

<!-- TODO: add a license (e.g., CC BY 4.0 for data, MIT for code). -->

