### Data storage directory structure
```
.
|—— 1
|   |-- DAPI.tif
|   |-- FAM.tif
|   |-- TXR.tif
|   |-- Y3.tif
|   |-- Y5.tif
|
|—— 2
|   |-- DAPI.tif
|   |-- FAM.tif
|   |-- TXR.tif
|   |-- Y3.tif
|   |-- Y5.tif
|
|—— 3
|   |-- DAPI.tif
|   |-- FAM.tif
|   |-- TXR.tif
|   |-- Y3.tif
|   |-- Y5.tif
|
|—— 4
    |-- DAPI.tif
    |-- FAM.tif
    |-- TXR.tif
    |-- Y3.tif
    |-- Y5.tif
    |_ _
```
### Correspondence between sequencing rounds and directory
    L2:1 L1:2 R1:3 R2:4
### Correspondence between channels and bases
    Y5:A FAM:T TXR:C Y3:G

### Format requirements for images
    The image can be in TIFF format and may be either RGB or grayscale, but it must be an 8-bit bitmap.

### Barcode file format requirements
    When creating barcode files, it is imperative to adhere to certain formatting standards to ensure compatibility and accuracy. 
    Special characters, such as slashes (/) and spaces, 
    are disallowed due to their potential to disrupt the file's integrity or cause parsing errors. 
    
    To address this, these characters should be systematically substituted with underscores, 
    which serve as a universally recognized placeholder that maintains the file's structural integrity.
    
    The file should be formatted with the barcode sequence in the first column and the gene name in the second column, without a header.
    For instance, a typical entry in this file might appear as follows:
    
        ATCG    Gene1Name1_Gene1Name2
        ACGC    Gene2Name
        ATCC    Gene3Name
