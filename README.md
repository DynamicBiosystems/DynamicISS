# DynamicISS
DynamicISS is a command-line tool developed by DynamicBiosystems designed for processing In Situ Gene Expression data generated by InSituVision. It includes functions such as image registration, spot detection, cell segmentation, and gene decoding.


## Install DynamicISS 1.0.2
Dowload DynamicISS from [here](https://github.com/DynamicBiosystems/DynamicISS/releases/tag/dynamiciss-v1.0.2).

```shell
# download dynamiciss_v1.0.2.tar.gz


mkdir DynamicISS

tar -zxf dynamiciss_v1.0.2.tar.gz -C DynamicISS

Prepend the DynamicISS/dynamiciss_v1.0.2 directory to your $PATH. This will allow you to invoke the DynamicISS command.
```
### Manual

---

#### params

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

### Result file introduction
![outs](https://github.com/DynamicBiosystems/inSituFocus/blob/main/inSituFocus.png)
### About

---

DynamicISS is developed by dynamic-biosystems Co., Ltd. The official website is [www.dynamic-biosystems](http://www.dynamic-biosystems.com/).


