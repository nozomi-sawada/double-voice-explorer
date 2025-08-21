# Sample Data Files

This directory contains sample emotion analysis data for testing the Double Voice Explorer application.

## Files Overview

### Lagos Weekly Record (LWR) 1891-1921
- **`sample_lwr_editorial.csv`**: Editorial articles from Lagos Weekly Record
  - 20 sample records spanning 1891-1921
  - Includes publication dates, emotion scores, and metadata

### Lagos Observer (LO) 1882-1888
- **`sample_lo_editorial.csv`**: Editorial articles from Lagos Observer
  - 10 sample records spanning 1882-1888
  - Historical baseline for comparison with LWR

- **`sample_lo_correspondence.csv`**: Reader correspondence from Lagos Observer
  - 10 sample records spanning 1882-1888
  - Represents reader voices vs editorial perspective

## Data Format

### Required Columns
- `id`: Unique article identifier
- `year`: Publication year (for temporal analysis)
- `PublicationDate`: Full publication date (YYYY/M/D format)

### Emotion Columns (0-1 scale)
- `Trust`: Trust emotion score
- `Fear`: Fear emotion score  
- `Sadness`: Sadness emotion score
- `Anticipation`: Anticipation emotion score
- `Joy`: Joy emotion score
- `Disgust`: Disgust emotion score
- `Surprise`: Surprise emotion score
- `Anger`: Anger emotion score

### Metadata Columns
- `data_source`: Publication source (LO/LWR)
- `article_type`: Content type (Editorial/Correspondence)

## Usage

1. Open Double Voice Explorer in your browser
2. Click on newspaper cards to load sample data:
   - **Lagos Observer Editorial**: Load `sample_lo_editorial.csv`
   - **Lagos Observer Correspondence**: Load `sample_lo_correspondence.csv`
   - **Lagos Weekly Record Editorial**: Load `sample_lwr_editorial.csv`
3. Use the 4-Category Comparison mode to analyze all datasets together

## Research Context

These sample files represent emotional analysis of colonial Lagos newspapers:
- **Time Period**: 1882-1921 (40 years of colonial press)
- **Geographic Focus**: Lagos, Colonial Nigeria
- **Analysis Method**: Pre-computed emotion analysis results (methodology may vary)
- **Research Question**: How do emotional patterns differ between editorial voice and reader submissions?

## Double Voice Theory

The concept of "Double Voice" refers to:
- Simultaneous presence of opposing emotions (e.g., Trust + Disgust)
- Reflection of colonial subject's complex emotional state
- Based on W.E.B. Du Bois's theory of double consciousness

## File Preparation Notes

- All emotion scores are normalized (0-1 range)
- Publication dates are approximated for demonstration
- Real research data would contain actual historical publication dates
- Sample data maintains realistic emotional patterns observed in colonial newspaper analysis