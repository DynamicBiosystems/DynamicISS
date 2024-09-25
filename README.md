# DynamicISS
DynamicISS is a command-line tool developed by DynamicBiosystems designed for processing In Situ Gene Expression data generated by InSituVision. It includes functions such as image registration, spot detection, cell segmentation, and gene decoding.


### Installation
Dowload DynamicISS from [here](https://github.com/DynamicBiosystems/DynamicISS/releases/tag/v1.0.3).

```shell
# download dynamiciss_v1.0.3.tar.gz


mkdir DynamicISS

tar -zxf dynamiciss_v1.0.3.tar.gz -C DynamicISS

Prepend the DynamicISS/dynamiciss_v1.0.3 directory to your $PATH. This will allow you to invoke the DynamicISS command.
```
### Manual

---

- count
  - `--ImagePath`: Image Path, required
  - `--bcycles`: Sequencing rounds, required
  - `--refcycle`: Sequencing rounds used as reference images,we will use the sequencing images from this round as a benchmark to register the images from other rounds. required
  - `--barcode`: Barcode2gene File,required
  - `--sample`: Sample name,required
  - `--rd`: The reference DAPI image path, when performing batch sequencing, in order to unify the coordinate system of different batches, it is necessary to specify a unified reference DAPI image for image registration, which conflicts with `--bcycles`,default:None
  - `--model`: Cell segmentation model of Cellpose,just need to fill in the corresponding model name, which can be found in the model directory under the software installation directory,default CP_20220919_134014
  - `--resolution`: Physical resolution corresponding to pixels(um/pixel),default:20X:0.324;40X:0.162
  - `--expansion`: Expansion of nuclei boundaries(um);default 10
  - `--diameter`: Cell diameter, if 0 will use the diameter of the training labels used in the model, 
                  or with built-in model will estimate diameter for each image,default:0
  - `--output`: Output Path,default:./output
  - `--splitsize`: When cutting a large image into small images, the pixel size of the small image,default:2000
  - `--extend`: Overlap pixel size between small images,default:15
  - `--cores`: Set max cores the pipeline may request at one time.;default 20



### Hardware Requirements  
---
- **CPU**: A minimum of 16 physical cores.
- **Memory (RAM)**: A minimum of 256GB. Higher memory configurations will improve operational efficiency and performance, especially when processing large datasets or performing complex calculations.  
- **Storage**: At least 1TB of available storage space.



### Quick start
---
```shell
 DynamicISS count \
 --ImagePath ./raw \
 --bcycles 1,2,3,4 \
 --refcycle 1 \
 --barcode barcode2gene.txt \
 --sample sample1 \
 --model CP_20220919_134014 \
 --resolution 0.324 
```

### Understanding DynamicISS Outputs

#### The `/outs` directory contains all the output files.
---
```shell
├── analysis
│   └── cluster.csv
├── insitufocus_lowres
│   ├── Cells.geojson
│   ├── DAPI.tif
│   ├── GeneCoord.csv
│   ├── nucleus_boundaries.geojson
│   └── seerna_iss.insitufocus
├── cell_feature_matrix
│   ├── barcodes.tsv.gz
│   ├── features.tsv.gz
│   └── matrix.mtx.gz
├── cell_feature_matrix.h5
├── cells.csv.gz
├── cells.parquet
├── DAPI.tif
├── Cells.geojson
├── GeneCoord.csv
├── nucleus_boundaries.geojson
├── seerna_iss.insitufocus
├── metrics_summary.csv
├── cells.mask.tif
├── nuclei.mask.tif
├── transcripts.csv.gz
├── transcripts.parquet
└── web_summary.html
```
|  File or Directory Name  |  Description  |
|  :--------: |  :-----:  |
|    analysis/   |   Folder containing secondary analysis data including graph-based clustering ; differential gene expression between clusters; UMAP dimensionality reduction.   |
|    insitufocus_lowres/   |   Low resolution Insitufocus input file.   |
| cell_feature_matrix/ |  Contains only non-empty cells  in MEX format.Each element of the matrix is the number of transcripts associated with a feature (row) and a cell(column). This file can be input into third-party packages and allows users to wrangle the cell-feature matrix (e.g. to filter outlier spots, run dimensionality reduction, normalize gene expression).  |
|    cell_feature_matrix.h5   |   Same information as cell_feature_matrix/ but in HDF5 format.   |
| cells.csv.gz |  The cell summary file (cells.csv.gz) is in gzipped CSV format. It contains one row for each cell, with the following columns: x_centroid, y_centroid, transcript_counts, cell_area, and nucleus_area.  |
| cells.parquet |   Same information as cells.csv.gz but in parquet format.  |
| DAPI.tif |  DAPI image, input file for insitufocus.  |
| Cells.geojson |  Geojson file for cell boundaries and types, input file for insitufocus.  |
| GeneCoord.csv |  Gene-related statistical files are required for Insitufocus,with the following columns:feature_name,y_location,x_location,cell,GeneColor. |
| seerna_iss.insitufocus |  Insitufocus startup file.  |
| metrics_summary.csv |  Run summary metrics in CSV format.  |
| cells.mask.tif |  Mask image of cells.  |
| nuclei.mask.tif |  Mask image of nuclei.  |
| transcripts.csv.gz |   The transcripts file (transcripts.csv.gz) is in gzipped CSV format. It contains one row for each decoded transcript, with the following columns: transcript_id,cell_id,overlaps_nucleus,feature_name,x_location,y_location,z_location,qv.  |
| transcripts.parquet |  Same information as transcripts.csv.gz but in parquet format.   |
| web_summary.html |  Run summary metrics and plots in HTML format.  |
### About

---

DynamicISS is developed by dynamic-biosystems Co., Ltd. The official website is [www.dynamic-biosystems](http://www.dynamic-biosystems.com/).


