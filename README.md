# Data-Driven Habitat Suitability Analysis of Hornbills Using Machine Learning Techniques

## Overview

This project employs innovative machine learning approaches to analyze habitat suitability for various hornbill species using environmental data from NASA, Sentinel-1B, and multiple environmental variables. The research focuses on hornbill conservation in Assam, India, using autoencoder-based deep learning techniques for ecological modeling.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Data Sources](#data-sources)
- [Methodology](#methodology)
- [Usage](#usage)
- [Results](#results)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Features

### Core Functionality
- **Autoencoder-based habitat modeling**: Deep learning approach for unsupervised feature extraction
- **Multi-metric similarity analysis**: Combines cosine similarity, Euclidean distance, and MSE
- **Movement pattern analysis**: Tracking and clustering of hornbill telemetry data
- **Environmental feature importance**: SHAP-based analysis of habitat variables
- **Spatial visualization**: Geographic mapping of habitat suitability

### Key Capabilities
- Dimensionality reduction of high-dimensional ecological data
- Real-time habitat suitability prediction
- Individual hornbill movement tracking and analysis
- Clustering-based habitat zone identification
- Conservation priority area mapping

## Installation

### Prerequisites
```bash
Python 3.8+
```

### Required Dependencies
```bash
pip install numpy pandas matplotlib seaborn plotly
pip install scikit-learn tensorflow keras
pip install folium geopandas rasterio
pip install shap earthengine-api
pip install movebank-api
```

### Google Earth Engine Setup
1. Create a Google Earth Engine account
2. Install the Earth Engine Python API
3. Authenticate your account:
```python
import ee
ee.Authenticate()
ee.Initialize()
```

## Data Sources

### Primary Data
- **Movebank Repository**: Hornbill telemetry data from Dr. Rohit Naniwadekar
- **Citizen Science Platforms**: 
  - eBird observations
  - iNaturalist sightings
  - MoveBird records

### Environmental Data
- **Satellite Imagery**: Sentinel-2 data via Google Earth Engine
- **Climate Data**: Temperature, humidity, precipitation, wind speed
- **Topographic Data**: Digital elevation models, terrain features
- **Vegetation Indices**: NDVI, Chlorophyll Index

### Study Area
- **Primary Focus**: Assam, India
- **Species**: Buceros bicornis (Great Hornbill), Rhyticeros undulatus (Wreathed Hornbill)
- **Protected Areas**: Kaziranga National Park and surrounding regions

## Methodology

### 1. Data Preprocessing
- Outlier removal (6 standard deviations threshold)
- Missing value handling
- Feature normalization using StandardScaler
- Dimensionality preparation for autoencoder input

### 2. Autoencoder Architecture
```
Encoder: 256 → 128 → 64 → 32 (bottleneck)
Decoder: 32 → 64 → 128 → 256 → output
```
- **Activation**: Leaky ReLU with L2 regularization
- **Training**: 250 epochs, batch size 64
- **Optimization**: Adam optimizer with adaptive learning rate

### 3. Similarity Metrics
- **Cosine Similarity**: Directional alignment in latent space
- **Euclidean Distance**: Spatial separation measurement
- **Mean Squared Error**: Reconstruction error analysis
- **Combined Score**: Normalized aggregation of all metrics

### 4. Evaluation Methods
- **Clustering**: K-means and OPTICS algorithms
- **Dimensionality Reduction**: PCA and t-SNE visualization
- **Performance Metrics**: Accuracy, Precision, Recall, F1-Score

## Usage

### Basic Habitat Suitability Analysis
```python
from hornbill_analysis import HabitatSuitabilityModel

# Initialize model
model = HabitatSuitabilityModel()

# Load environmental data
model.load_environmental_data('path/to/environmental_data.csv')

# Train autoencoder
model.train_autoencoder(epochs=250, batch_size=64)

# Predict habitat suitability
suitability_scores = model.predict_suitability(new_locations)
```

### Movement Pattern Analysis
```python
from hornbill_analysis import MovementAnalyzer

# Load telemetry data
analyzer = MovementAnalyzer()
analyzer.load_telemetry_data('path/to/movebank_data.csv')

# Analyze movement patterns
clusters = analyzer.perform_clustering(method='kmeans', n_clusters=4)
migration_paths = analyzer.analyze_migration_patterns()
```

### Visualization
```python
from hornbill_analysis import Visualizer

viz = Visualizer()

# Create habitat suitability map
viz.plot_habitat_suitability(suitability_scores, coordinates)

# Visualize movement patterns
viz.plot_movement_patterns(telemetry_data, clusters)

# Generate feature importance plot
viz.plot_shap_importance(model, features)
```

## Results

### Model Performance
- **Autoencoder Accuracy**: 83.3%
- **Precision**: 87.5%
- **Recall**: 87.5%
- **F1-Score**: 87.5%

### Key Findings
1. **Environmental Factors**: Humidity (most influential), dewpoint, and temperature are primary drivers
2. **Movement Patterns**: 6 tracked individuals showed diverse strategies (site fidelity vs. migration)
3. **Habitat Clusters**: 4 distinct habitat zones identified (core, transitional, seasonal)
4. **Conservation Areas**: High-priority regions mapped in Northeast India

### Individual Hornbill Behaviors
- **Site Fidelity**: 3 individuals (1_bill, 4_godfather, 5_rifle) showed strong territorial behavior
- **Migration**: 3 individuals exhibited complex seasonal movement patterns
- **Activity Patterns**: Peak activity during crepuscular hours (dawn/dusk)


## Environmental Variables

The model incorporates the following environmental predictors:

### Climate Variables
- Temperature (°C)
- Humidity (%)
- Precipitation (mm)
- Wind Speed (m/s)
- Solar Radiation (W/m²)
- Sunshine Duration (hours)

### Vegetation Indices
- **NDVI**: (NIR - Red) / (NIR + Red)
- **Chlorophyll Index**: (NIR - Red) / (Green + Red)

### Topographic Features
- Elevation (m)
- Slope
- Aspect

## Contributing

We welcome contributions to improve the hornbill habitat analysis toolkit:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Create a Pull Request

### Areas for Contribution
- Additional species modeling
- Improved visualization tools
- Real-time data integration
- Mobile app development for field data collection

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation

If you use this work in your research, please cite:

```bibtex
@article{nedunchezhian2024hornbill,
  title={Data-Driven Habitat Suitability Analysis of Hornbills Using Machine Learning Techniques},
  author={Nedunchezhian, R. and Pramod, P. and Mahendrian, M. and Vishal, S. and Dines, S. and Aneesh, V. and Anish, M.},
  journal={Conference Proceedings},
  year={2024},
  publisher={Coimbatore Institute of Technology}
}
```

## Acknowledgments

### Data Contributors
- **Dr. Rohit Naniwadekar**: Hornbill telemetry data from Northeast India
- **Citizen Scientists**: eBird, iNaturalist, and MoveBird contributors
- **Salim Ali Centre for Ornithology and Natural History**: Research collaboration

### Technical Support
- **Google Earth Engine**: Satellite imagery processing
- **OpenWeather**: Climate data access
- **Movebank**: Animal tracking data repository
- **Department of Forest and Wildlife, Assam**: Field research permissions

### Funding & Institutional Support
- Coimbatore Institute of Technology, Department of Computer Science and Engineering
- Salim Ali Centre for Ornithology and Natural History, Coimbatore

---

## Contact

For questions, suggestions, or collaboration opportunities:

- **Lead Author**:Vishal S (Coimbatore Institute of Technology)
- **Ecological Consultant**: Dr. R. Mahendrian (Salim Ali Centre for Ornithology and Natural History)
- **Project Repository**: [[GitHub Repository Link](https://github.com/vishals25/mini-project-2025/)]

---

*This project contributes to hornbill conservation efforts through advanced computational ecology and supports evidence-based habitat management strategies.*
