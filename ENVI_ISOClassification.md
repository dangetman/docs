# ENVI_ISODATAClassification

**ENVI_ISODATAClassification** The ISODATA method for unsupervised classification starts by calculating class means evenly distributed in the data space, then iteratively clusters the remaining pixels using minimum distance techniques. Each iteration recalculates means and reclassifies pixels with respect to the new means. This process continues until the percentage of pixels that change classes during an iteration is less than the change threshold or the maximum number of iterations is reached

### Table of Contents
 * [Quickstart](#quickstart) - Get started!
 * [Inputs](#inputs) - Required and optional task inputs.
 * [Outputs](#outputs) - Task outputs and example contents.
 * [Contact Us](#contact-us) - Contact tech or document owner.

**Example Script:** Run in IPython using the GBDXTools Interface

```python
# Quickstart **Example Script Run in Python using the gbdxTools Interface
# First Initialize the Environment 

    from gbdxtools import Interface
    import json
	
    gbdx = Interface()
	
    envitask = gbdx.Task("ENVI_ISODATAClassification")
    envitask.inputs.file_types = 'tif'
    envitask.inputs.input_raster = "s3://gbd-customer-data/pathToImage/output_raster_uri/outputfile.tif"
    envitask.outputs.output_raster = "ENVI"
	
    workflow = gbdx.Workflow([ envitask ])
	
    workflow.savedata(
        envitask.outputs.output_raster_uri,
        location="output_raster_uri"
    )
    workflow.execute()
	
    print workflow.id
	workflow.status
```	

### Inputs	

**Description of Input Parameters and Options for the "ENVI_ISODATAClassification":**
This task will function on a multi-spectral image located in the S3 location: 
Input imagery sensor types include but may not be limited to: QuickBird, WorldView 1, WorldView 2, WorldView 3 and GeoEye
Tif files from the AOP_Strip_Processor were tested with this task to confirm functionality; however, the task may ingest additional raster image file types such as: ENVI .hdr,  

The following table lists the ENVI_ISODATAClassification task:

All inputs are **required**

Name                     |       Default         |        Valid Values             |   Description
-------------------------|:---------------------:|---------------------------------|-----------------
input_raster             |          N/A          | S3 URL   .TIF only              | S3 location of input data. Specify a sieving output raster on which to perform classification clumping

### Outputs

The following table lists the Spectral Index task outputs.

Name                | Required |   Description
--------------------|:--------:|-----------------
output_raster_uri   |     Y    | This will explain the output file location and provide the output in .TIF format.


This task will function on a Sieving classification image located in the S3 location.  The file type input of the classification is preferred in the .hdr format.  An example of ENVI ISO Data Classification and Sieving are provided in the sample script above to demonstrate a full workflow. Additional options include:


**OPTIONAL SETTINGS AND DEFINITIONS:**

Name                       |       Default         |        Valid Values             |   Description
---------------------------|:---------------------:|---------------------------------|-----------------
file_types                 |          N/A          | string                          | Comma separated list of permitted file type extensions. Use this to filter input files
change_threshold_percent   |         3 X 3         | string                          | The change threshold percentage that determines when to complete the classification.  When the percentage of pixels that change classes during an iteration is less than the threshold value, the classification completes
number_of_classes          |          2            | string                          | The requested number of classes to generate
iterations                 |          N/A          | string                          | The maximum iterations to perform.  If the change threshold percent is not met before the maximum number of iterations is reached, the classification completes
task_meta_data             |          N/A          | string                          | Output location for task meta data such as execution log and output JSON
output_raster_uri_filename |         output        | Folder name in S3 location      | Specify the file name
	

**Data Structure for Expected Outputs:**

Your Processed classification file will be written to the specified S3 Customer Location in the ENVI file format and tif format(e.g.  s3://gbd-customer-data/unique customer id/named directory/classification.hdr).  


For background on the development and implementation of ISO Classification refer to the [ENVI Documentation](https://www.harrisgeospatial.com/docs/classificationtutorial.html)

###Contact Us
Document Owner - Carl Reeder - creeder@digitalglobe.com
