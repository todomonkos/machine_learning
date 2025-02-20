# Advanced Document Analysis and Summarization Tool

A robust Python-based tool for analyzing and summarizing large text documents using state-of-the-art natural language processing models. This tool combines BART-based text summarization with intelligent document chunking and comprehensive text analysis capabilities.

## Features

- Text summarization using Facebook's BART large CNN model
- Smart document chunking using DistilBERT for optimal processing of long documents
- Detailed text analysis including:
  - Basic statistics (word count, sentence count, average lengths)
  - Common words and phrases identification
  - Word cloud visualization
  - Category-based sampling for balanced analysis
- Comprehensive error handling and logging
- Progress tracking for long-running operations
- Flexible output formats (CSV, JSON) with detailed metadata

## Prerequisites

The following Python packages are required:

```bash
pip install transformers nltk pandas numpy matplotlib wordcloud tqdm torch
```

Additionally, you'll need to download the following NLTK resources:

```python
import nltk
nltk.download(['punkt', 'stopwords', 'averaged_perceptron_tagger'])
```

## Model Information

The tool uses two main models:
- Summarization: facebook/bart-large-cnn
- Document Chunking: BlueOrangeDigital/distilbert-cross-segment-document-chunking

## Usage

### Basic Usage

```python
from document_analyzer import run_analysis

results = run_analysis(
    input_file="path/to/your/file.csv",
    output_path="results"
)
```

### Advanced Configuration

You can customize the analysis by modifying the AnalysisParameters:

```python
from document_analyzer import AnalysisParameters

params = AnalysisParameters(
    input_file="path/to/your/file.csv",
    sample_size=500,              # Number of documents to sample
    text_column="content",        # Column containing text data
    wordclouds=5,                # Number of word clouds to generate
    save_wordclouds=True,        # Save word clouds to files
    output_file="results.csv",    # Output filename
    output_dir="results",         # Output directory
    debug=True,                   # Enable debug logging
    summarize=True,               # Generate summaries
    max_summary_length=70,        # Maximum summary length
    min_summary_length=30         # Minimum summary length
)
```

## Input Format

The tool expects a CSV file with at least the following columns:
- category: Document category/classification
- content: The text content to be analyzed

Additional metadata columns are supported and will be included in the summary metadata.

## Output Structure

### Analysis Results (CSV)
The tool generates a CSV file containing:
- Basic text statistics
- Word and phrase frequency analysis
- Document metadata
- Category distribution

### Summaries (JSON)
Summary output includes:
- Generated summary text
- Processing metadata
- Token counts
- Chunking statistics (for long documents)
- Source document metadata

### Visualizations
- Word clouds saved as PNG files (when enabled)
- One word cloud per sampled document

## Error Handling

The tool implements comprehensive error handling:
- Graceful handling of malformed input
- Detailed error logging
- Progress tracking with status indicators
- Automatic recovery from processing failures

## Logging

Logging can be configured using the debug parameter:
- INFO level: Basic operation logging
- DEBUG level: Detailed processing information
- Formatted output with timestamps and log levels
- Console and file output options

## Best Practices

1. Start with a small sample size for testing
2. Enable debug mode during initial setup
3. Monitor memory usage with large documents
4. Regular checkpoints for long-running processes
5. Verify input data format before processing

## Performance Considerations

- Long documents are automatically chunked for optimal processing
- Token limits are enforced to prevent memory issues
- Parallel processing for multiple documents
- Progress tracking for long-running operations

## Contributing

We welcome contributions! Please follow these steps:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request with a clear description
4. Ensure all tests pass

## License

[Insert your license information here]
