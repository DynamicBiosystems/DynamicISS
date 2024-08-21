# DynamicISS
DynamicISS is an on-instrument software pipeline that simultaneously collects and processes  In Situ Gene Expression data.


## Install DynamicISS 1.0.2
Dowload DynamicST from [here](https://github.com/DynamicBiosystems/DynamicISS/releases/tag/dynamiciss-v1.0.2).

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
  - --ImagePath:Image Path,required
  - --bcycles: Barcode Cycles,required
  - --refcycle: Reference Cycle,required
  - --barcode: Barcode2gene File,required
  - --sample: Sample name,required
  - --decode-method: decode method, IRIS or checkall,defualt:checkall
  - --error-rounds: For the checkall pipeline,allow incorrect number of rounds,defualt:0
  - --search-radius: For the checkall,the size of the search radius,defualt:3.5
  - --skip-register:Skip image registration,False or True,defualt:False
  - --rd:Dapi for other paths that are not in the rounds,default:None
  - --remove-duplicates-spots:remove duplicates spots,False or True,defualt:False
  - --model:Cell segmentation model of Cellpose,default:CP_20220919_134014
  - --resolution:Physical resolution corresponding to pixels(um/pixel),default:20X:0.324;40X:0.162
  - --expansion:Expansion of nuclei boundaries(um);default 10
  - --diameter:cell diameter, if 0 will use the diameter of the training labels used in the model, or with built-in model will estimate diameter for each image,default:0
  - --equalize:Image enhancement before cell segmentation with CellPose
  - --output:Output Path,default:./output
  - --prefix:Sample name prefix,default:sample
  - --method:Image Corrective Methods,default:SIFT
  - --splitsize:Image Segmentation Size (pixel),default:2000
  - --extend:Image Segmentation Extend Size (pixel),default:15
  - --registration-splitsize:When the row or col of the image are greater than 2**16, the cutting size during image registration,default:20000
  - --cores:set max cores the pipeline may request at one time.;default 20
 

### Hardware Requirements  
  
- **CPU**: A minimum of 16 physical cores.
- **Memory (RAM)**: A minimum of 256GB. Higher memory configurations will improve operational efficiency and performance, especially when processing large datasets or performing complex calculations.  
- **Storage**: At least 1TB of available storage space. 

