# Double Voice Explorer

A web-based tool for analyzing emotional patterns and "Double Voice" phenomena in colonial Lagos newspapers (1882-1921).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Quick Start

1. **Open the tool**: Visit the [live demo](https://nozomi-sawada.github.io/double-voice-explorer/) or open `index.html` locally
2. **Load data**: Upload CSV files with emotion analysis results or use provided sample data
3. **Analyze**: Select emotion pairs, adjust thresholds, and explore visualizations
4. **Export**: Download results for further statistical analysis

### Data Format
```csv
id,year,PublicationDate,Trust,Fear,Sadness,Anticipation,Joy,Disgust,Surprise,Anger,data_source,article_type
```
Emotion values should be normalized (0-1 scale).

## Research Background

This digital humanities tool visualizes and analyzes pre-computed emotional patterns in colonial African press discourse. The project examines two major Lagos publications: *Lagos Observer* (1882-1888) and *Lagos Weekly Record* (1891-1921), comparing editorial perspectives with reader correspondence through computational text mining approaches.

Colonial newspapers present unique challenges for emotional analysis, as they often contain complex, contradictory feelings within the same texts. The "Double Voice" phenomenon refers to the simultaneous presence of opposing emotions—such as hope and despair, trust and suspicion—reflecting the intricate emotional landscapes of colonial experience. This tool provides specialized metrics and visualizations for identifying and analyzing these coexisting emotional states, contributing to computational approaches in colonial African newspaper studies.

## Features

- **Interactive Visualizations**: Scatter plots and time series analysis using Chart.js
- **4-Category Comparison**: Editorial vs Correspondence × Lagos Observer vs Lagos Weekly Record
- **Multiple Metrics**: 
  - Double Voice Score: √(Emotion₁ × Emotion₂)
  - Emotional Balance: 1 - |Emotion₁ - Emotion₂|
  - Emotional Intensity: (Emotion₁ + Emotion₂) / 2
- **Export Functionality**: CSV download for statistical analysis
- **No Installation**: Pure HTML/CSS/JavaScript, runs in browser

## Technical Details

- **Frontend**: HTML/CSS/JavaScript (no build process)
- **Visualization**: Chart.js 3.9.1
- **Data Processing**: Papa Parse 5.3.0
- **Deployment**: GitHub Pages

## Sample Data

- `sample_lo_editorial.csv`: Lagos Observer editorial content
- `sample_lo_correspondence.csv`: Lagos Observer reader submissions  
- `sample_lwr_editorial.csv`: Lagos Weekly Record editorial content

## Research Applications

- **Colonial Studies**: Analysis of emotional labor and resistance strategies
- **Digital Humanities**: Computational approaches to historical newspaper analysis
- **African Studies**: Early African journalism and public sphere formation

## Citation

```bibtex
@software{sawada2025doublevoice,
  author = {Sawada, Nozomi},
  title = {Double Voice Explorer: Analyzing Emotional Patterns in Colonial Lagos Newspapers (1882-1921)},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/nozomi-sawada/double-voice-explorer}
}
```

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Contact

**Nozomi Sawada**  
GitHub: [@nozomi-sawada](https://github.com/nozomi-sawada)