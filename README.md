# pdf2gif

A Python library and command-line tool for converting PDF files to animated GIFs with customizable frame delays and slide multipliers.

## Features

- Convert PDF files to animated GIFs
- Customizable frame delay (in milliseconds)
- Configurable first slide multiplier (repeats the first slide multiple times)
- Automatic downsampling for better performance
- Simple command-line interface
- Python library for programmatic use

## Installation

### From PyPI (Recommended)

```bash
pip install pdf2gif
```

- **Poppler** installation as required by `pdf2image` for PDF processing
  - **Windows**: Download from [poppler releases](https://github.com/oschwartz10612/poppler-windows/releases/)
  - **macOS**: `brew install poppler`
  - **Linux**: `sudo apt-get install poppler-utils` (Ubuntu/Debian) or `sudo yum install poppler-utils` (CentOS/RHEL)

## Usage

### Command Line Interface

The simplest way to use pdf2gif is through the command line:

```bash
# Basic usage
pdf2gif presentation.pdf

# Custom frame delay (200ms)
pdf2gif document.pdf --frame-delay 200

# Custom first slide multiplier (5 times)
pdf2gif slides.pdf --first-slide-multiplier 5

# Both custom parameters
pdf2gif slides.pdf --frame-delay 100 --first-slide-multiplier 3
```

#### Command Line Options

- `pdf_filename`: Path to the input PDF file (required)
- `--frame-delay`: Frame delay in milliseconds (default: 150)
- `--first-slide-multiplier`: Number of times to repeat the first slide (default: 10)

### Python Library

You can also use pdf2gif as a Python library:

```python
from pdf2gif import convert_pdf_to_gif

# Basic conversion
gif_path = convert_pdf_to_gif("presentation.pdf")

# Custom parameters
gif_path = convert_pdf_to_gif(
    "document.pdf",
    frame_delay=200,
    first_slide_multiplier=5
)

print(f"GIF created at: {gif_path}")
```

## How It Works

1. **PDF Conversion**: Uses `pdf2image` to convert each PDF page to a PIL Image
2. **Downsampling**: Reduces image size by 50% for better performance and smaller file sizes
3. **First Slide Repetition**: Repeats the first slide according to the multiplier setting
4. **GIF Creation**: Uses `stackview` and `PIL` to create an animated GIF with the specified frame delay

## License

This project is licensed under the BSD-3 License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [pdf2image](https://github.com/Belval/pdf2image) for PDF to image conversion
- [stackview](https://github.com/haesleinhuepf/stackview) for GIF animation creation
- [Pillow](https://python-pillow.org/) for image processing
- [NumPy](https://numpy.org/) for array operations

## Troubleshooting

### Common Issues

1. **"poppler not found" error**: Install poppler utilities (see Dependencies section)
2. **Memory issues with large PDFs**: Consider processing PDFs with fewer pages or lower resolution

### Getting Help

- Check the [Issues](https://github.com/haesleinhuepf/pdf2gif/issues) page
- Create a new issue with detailed error information
- Include your operating system and Python version 