# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Double Voice Explorer is a single-file HTML web application for analyzing emotional patterns and "Double Voice" phenomena in colonial Lagos newspapers (1882-1921). It's a standalone visualization tool that runs entirely in the browser with no build process or server requirements.

## Key Commands

### Local Development
```bash
# Simply open the HTML file in any modern browser
open index.html
# or navigate to file in browser

# For GitHub Pages deployment
git add .
git commit -m "Update application"
git push origin main
```

### File Preparation for GitHub
```bash
# Files are already renamed to GitHub standards:
# index.html (main application)
# LICENSE (license file) 
# .gitignore (git ignore rules)
# README.md (documentation)

# Create sample data directory
mkdir sample-data
mv lwr-editorial-sample.txt sample-data/sample_lwr_editorial.csv
```

## Application Architecture

### Core Technologies
- **Pure HTML/CSS/JavaScript**: No build process, framework, or dependencies
- **Chart.js 3.9.1**: Interactive scatter plots and time series visualizations
- **Papa Parse 5.3.0**: Client-side CSV file parsing
- **Responsive Design**: Mobile and tablet compatible

### Data Processing Pipeline
1. **CSV Upload**: Users upload emotion analysis data files
2. **Automatic Detection**: Recognizes Lagos Observer (LO) vs Lagos Weekly Record (LWR) data
3. **Real-time Analysis**: Calculates Double Voice metrics on-the-fly
4. **Interactive Visualization**: Updates charts based on user filters
5. **Export Functionality**: Downloads processed results as CSV

### Double Voice Metrics
- **DV Score (Geometric Mean)**: √(Emotion1 × Emotion2) - synergistic strength
- **Balance**: 1 - |Emotion1 - Emotion2| - emotional equilibrium
- **Intensity**: (Emotion1 + Emotion2) / 2 - average emotional strength
- **Valid DV**: Boolean flag when both emotions exceed threshold (default 0.5)

## Data Format Requirements

### Required CSV Columns
- `id`: Unique article identifier
- `year` or `Year`: Publication year (1882-1921)
- Emotion columns: `Trust`, `Disgust`, `Joy`, `Sadness`, `Fear`, `Anger`, `Anticipation`, `Surprise` (values 0-1)

### Supported Emotion Pairs
- Trust ↔ Disgust (default)
- Joy ↔ Sadness
- Anticipation ↔ Surprise
- Anger ↔ Fear

## Deployment Strategy

### GitHub Pages Setup
1. Repository must contain `index.html` as main file
2. Enable GitHub Pages in repository settings
3. Application will be available at `https://username.github.io/repository-name/`

### Single-File Architecture Benefits
- No build process required
- Easy deployment and sharing
- Self-contained with external CDN dependencies
- Works offline once loaded

## Research Context

This tool analyzes emotional expression in colonial African newspapers, specifically:
- **Lagos Observer** (1882-1888): Editorials and correspondence
- **Lagos Weekly Record** (1891-1921): Editorial content
- **4-Category Analysis**: Editorial vs Correspondence × LO vs LWR comparison
- **Double Voice Theory**: Based on W.E.B. Du Bois's double consciousness concept

## Development Notes

### Code Organization
The application follows a single-file structure with clearly separated sections:
- CSS styling (responsive design with gradient themes)
- HTML structure (upload interface, controls, visualization containers)
- JavaScript modules (data processing, visualization, export functionality)

### Key JavaScript Functions
- `loadCSVData()`: Handles file upload and parsing
- `calculateDoubleVoice()`: Computes DV metrics
- `updateAnalysis()`: Refreshes visualizations based on filters
- `compareEditorialReader()`: Launches 4-category comparison mode
- `exportResults()`: Downloads analysis results

### Customization Points
- Emotion pair definitions can be extended
- Threshold ranges are configurable
- Chart styling follows Chart.js theming
- Export formats can be modified

## Academic Usage

The tool supports digital humanities research with:
- Citation format provided in README
- Exportable results for statistical analysis
- Configurable thresholds for different research questions
- Time series analysis for historical progression