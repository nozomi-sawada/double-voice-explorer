# Double Voice Explorer

*English | [日本語](README.ja.md)*

A web-based tool for analyzing emotional patterns and "Double Voice" phenomena in colonial Lagos newspapers (1882-1921).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Quick Start

1. **Open the tool**:
    * **Online (Recommended)**: Visit the [live demo](https://nozomi-sawada.github.io/double-voice-explorer/)
    * **Offline / Locally (Ensuring Reproducibility)**:
        1. Download the following **three essential files** to the **same folder** on your computer:
            * **`index.html`**
            * **`chart.min.js`**
            * **`papaparse.min.js`**
        2. Open the downloaded `index.html` file in your browser.
            (*This ensures the tool runs securely in an environment without external dependencies.*)

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
- **Visualization**: Chart.js 3.9.1 (local library)
- **Data Processing**: Papa Parse 5.3.0 (local library)
- **Deployment**: GitHub Pages

## Security and Reproducibility

This tool was designed with a strong emphasis on security and long-term academic reproducibility, based on a comprehensive security review.

1. **Security**:
   * **XSS Prevention**: All `.innerHTML` operations have been replaced with safe `.textContent` methods to prevent DOM-based XSS attacks from user-uploaded data.
   * **CSV Formula Injection**: All exported string data is sanitized via `sanitizeForCSV()` to prevent malicious formula execution in spreadsheet software.
   * **Event Handlers**: All inline `onclick` attributes were removed and replaced with secure `addEventListener` methods.

2. **Reproducibility**:
   * **Local Libraries**: This tool **intentionally bundles local copies** of `Chart.js` and `Papa Parse` (`./chart.min.js`, `./papaparse.min.js`) instead of using external CDNs.
   * **Why**: This approach guarantees long-term functionality (even if CDNs change) and ensures the tool runs in offline environments or on networks (proxies, etc.) that might otherwise block SRI verification.
   * **Timestamps**: Exported filenames use the user's local date (`localDateStamp()`) to prevent timezone ambiguity in research data.

## Sample Data

- `sample_lo_editorial.csv`: Lagos Observer editorial content
- `sample_lo_correspondence.csv`: Lagos Observer reader submissions  
- `sample_lwr_editorial.csv`: Lagos Weekly Record editorial content

## Research Applications

- **Colonial Studies**: Analysis of emotional labor and resistance strategies
- **Digital Humanities**: Computational approaches to historical newspaper analysis
- **African Studies**: Early African journalism and public sphere formation
- 
## Development Acknowledgments

This tool was developed by Nozomi Sawada. Portions of this repository were drafted with AI assistance (e.g., Claude Code Sonnet 4.5, Gemini 2.5 Pro, GPT-5 Thinking) for code implementation and debugging. All academic content, methodological decisions, and validation were reviewed and remain the sole responsibility of the human researcher.

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
