# 8-Band Built-up extent (protogenV2PANTEX10)

PANTEX10 is an un-supervised protocol for computing a built-up expectation layer from 8 band (optical + VNIR) image data-sets. This is a binary image in which intensity 255 indicates that it is likely that a pixel coincides with a built-up area and intensity 0 that a pixel does not coincide with a built-up area.  The building stock defining the built-up areas excludes those with roofs covered with ceramic tiles.


### Table of Contents
 * [Quickstart](#quickstart) - Get started!
 * [Inputs](#inputs) - Required and optional task inputs.
 * [Outputs](#outputs) - Task outputs and example contents.
 * [Advanced](#advanced) - Additional information for advanced users.
 * [Known Issues](#known-issues) - current or past issues known to exist.
 * [Contact Us](#contact-us) - Contact tech or document owner.

### Quickstart

**Example Script:** Run in IPython using the [GBDXTools Interface] (https://github.com/DigitalGlobe/gbdxtools)


This script gives the example of Pantex with a single tif file as input. 

```python
    from gbdxtools import Interface 
    import json
    gbdx = Interface()
    raster = 's3://gbd-customer-data/7d8cfdb6-13ee-4a2a-bf7e-0aff4795d927/PathToImage/image.tif'
    prototask = gbdx.Task("protogenV2PANTEX10", raster=raster)

    workflow = gbdx.Workflow([ prototask ])  
    workflow.savedata(prototask.outputs.data, location="protogen/BUE")
    workflow.execute()

    print workflow.id
    print workflow.status
```	
### Inputs
**Description of Input Parameters and Options for "protogenV2PANTEX10":**

WorldView 2 or WorldView 3 multi-spectral imagery (8-band optical and VNIR data sets) that has been atmospherically compensated by the AOP processor.  Supported formats are .TIF

Name                     |       Default         |        Valid Values             |   Description
-------------------------|:---------------------:|---------------------------------|-----------------
raster                   |          N/A          | S3 URL   .TIF only              | S3 location of input .tif file processed through AOP_Strip_Processor.

**REQUIRED SETTINGS AND DEFINITIONS:**

### Outputs

The following table lists the Pantex Protogen task outputs.

Name | Required |   Description
-----|:--------:|-----------------
data |     Y    | This will explain the output file location and provide the output in .TIF format.
log  |     N    | S3 location where logs are stored.

**OPTIONAL SETTINGS: Required = False**

* NA - No additional optional settings for this task exist



###Postman status @ 06/09/16

**Successful run with Tif file.  Testing additional input formats still in progress.  .VRT is currently not functioning (6/7/2016)**



**Data Structure for Expected Outputs:**

Your Processed Imagery will be written as Binary .TIF image type UINT8x1 and placed in the specified S3 Customer Location (e.g.  s3://gbd-customer-data/unique customer id/named directory/).  

**Known issues:**  Highly granular rock-covered areas might be interpreted as built-up areas.

**Limitations:** Ceramic roofs are not considered.  


For background on the development and implementation of  Protogen  [Documentation under development](Insert link here)

###Contact Us
Tech Owner - Georgios Ouzounis - gouzouni@digitalglobe.com
Document Owner - Carl Reeder - creeder@digitalglobe.com
