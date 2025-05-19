
# PDF Document Layout Analysis

A powerful tool for automatically detecting and analyzing the structural layout of PDF documents using deep learning.

## Overview

This project provides a set of tools for analyzing PDF documents to identify different layout elements like text blocks, titles, tables, figures, and lists. It leverages computer vision and pre-trained models to extract document structure without manual annotation.

## Features

- **Automated layout detection** using state-of-the-art deep learning models
- **Support for multiple document types** with specialized models
- **Flexible page processing** for single or batch page analysis
- **Visualization tools** to display detected layout elements
- **Structured data export** in JSON format
- **Adjustable detection parameters** to optimize for different document types

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/document-layout.git
cd document-layout

# Install dependencies
pip install -r requirements.txt
```

### Requirements

- Python 3.7+
- LayoutParser
- PyMuPDF (fitz)
- OpenCV
- Matplotlib
- NumPy
- Detectron2
- PyTorch

## Usage

### Google Colab Notebook

The easiest way to use this tool is through our Google Colab notebook, which provides an interactive interface with form widgets for all parameters.

[Open in Google Colab](https://colab.research.google.com/github/yourusername/document-layout/blob/main/document_layout_analysis.ipynb)

### Local Python Script

Alternatively, you can run the tool locally:

```python
# Example usage
import main

# Configure parameters
pdf_path = "your_document.pdf"
output_dir = "output"
page_to_process = None  # For single page processing
start_page = 0          # For multi-page processing
end_page = 5            # For multi-page processing
model_type = "PubLayNet"
threshold = 0.8
dpi_setting = 300
display_plots = True
export_json_data = True

# Create args object
args = main.Args(
    pdf_path,
    output_dir,
    page_to_process,
    start_page,
    end_page,
    model_type,
    threshold,
    dpi_setting,
    not display_plots,
    export_json_data
)

# Run analysis
main.main(args)
```

## Available Models

The tool supports the following pre-trained models:

1. **PubLayNet** (default) - Trained on scientific publications, optimized for academic papers
2. **PrimaLayout** - General document layout model, suitable for a wide range of documents
3. **HJDataset** - Specialized for historical Japanese documents

## Output

The tool generates two types of output:

1. **Visualizations** - PNG images showing the detected layout elements with bounding boxes and labels
2. **JSON data** - Structured data containing coordinates and types of all detected elements

Example JSON structure:

```json
{
  "0": [
    {
      "type": "Title",
      "confidence": 0.998,
      "coordinates": {
        "x1": 50,
        "y1": 100,
        "x2": 550,
        "y2": 150
      }
    },
    {
      "type": "Text",
      "confidence": 0.985,
      "coordinates": {
        "x1": 50,
        "y1": 200,
        "x2": 550,
        "y2": 400
      }
    }
  ]
}
```

## Applications

- Document understanding and digitization
- Preparing data for OCR and text extraction
- Information retrieval from document collections
- Document structure analysis
- Building document databases

## License

MIT

## Acknowledgements

This project uses [LayoutParser](https://layout-parser.github.io/) and builds upon research from the following papers:
- [PubLayNet](https://github.com/ibm-aur-nlp/PubLayNet)
- [PRImA Layout Analysis Dataset](https://www.primaresearch.org/datasets/)
