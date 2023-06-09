# ImmunoViewer

Explore and annotate your multi-channel large TIF files with this user-friendly viewer.

## Table of Contents

* [About ImmunoViewer](#about-immunoviewer)  
* [Installation](#installation)  
    * [Install OpenSlide](#install-openslide)
    * [Install from GitHub](#install-from-github)
    * [Install from pip](#install-from-pip)
* [Usage](#usage)  
    * [Folder structure](#folder-structure)
    * [Generate tiles](#generate-tiles)
    * [Run the viewer](#run-the-viewer)
* [Acknowledgements](#acknowledgements)


## About ImmunoViewer

ImmunoViewer is a convenient tool for viewing scanned TIF files, particularly those generated by the Keyence Immuno Fluorescence scanner. The viewer allows you to add annotations to the images and supports multi-channel images by saving channels as separate big TIF files. You can customize the color and signal intensity for each channel. We welcome your suggestions for additional features.

<img src="https://github.com/davidvi/ImmunoViewer/raw/main/img/screenshot.jpg" height="500">  

## Installation

### Install OpenSlide

ImmunoViewer requires OpenSlide to generate tiled images (not necessary for the viewer). If you use Conda to install ImmunoViewer, it will automatically install OpenSlide.

To install OpenSlide using a Conda environment, run this command:

```bash
conda install -c conda-forge openslide
```

For installation instructions on other operating systems, visit the OpenSlide download page: [OpenSlide](https://openslide.org/download/)

### Install from github

Ensure that you have also installed OpenSlide.

```bash
git clone https://github.com/davidvi/ImmunoViewer.git
cd ImmunoViewer
python setup.py install
```

### Install from pip 

Ensure that you have also installed OpenSlide.

```bash
pip install ImmunoViewer
```

## Usage

### Folder structure

Organize your TIF files in a folder using one of the following structures:

* data_directory/sample_name/sample_file.tif
* data_directory/project_name/sample_name/sample_file.tif
* data_directory/project_name/sample_name/[ch1.tif, ch2.tif, chN.tif]

### Generate tiles

To generate the tiles, execute the following command:

```bash
ImmunoViewerProcess -t [number of threads] [data_directory]
```

### Run the viewer

To start the viewer, run the following command: 

```bash
ImmunoViewerServer -p [port (default is 5000)] -l [IP address (default = 0.0.0.0)] [data_directory]
```

Now you can navigate to http://[IP address]:[port] in your web browser to access ImmunoViewer.

If you leave the IP address to default (0.0.0.0) and the port is exposed to the network other people can also view your slides.  

## Acknowledgements 

The script to tile big TIF files was adapted from the [OpenSlide-python repo](https://github.com/openslide/openslide-python). 