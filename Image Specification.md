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
### The correspondence between channels and bases
    Y5:A FAM:T TXR:C Y3:G

### Format requirements for images
    It can be a TIFF image in RGB or grayscale format, but it must be an 8-bit bitmap

### Barcode file format requirements
    Special characters such as/, spaces, etc. are not allowed in barcode files and can be replaced with underscores
