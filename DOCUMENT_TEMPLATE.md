# Task Name (TaskNameInGBDX)

Complete description of task function:  

(task name) can be run with Python using   [gbdxtools](https://github.com/DigitalGlobe/gbdxtools) or through the [GBDX Web Application](https://gbdx.geobigdata.io/materials/).  

### Table of Contents
 * [Quickstart](#quickstart) - Get started!
 * [Inputs](#inputs) - Required and optional task inputs.
 * [Outputs](#outputs) - Task outputs and example contents.
 * [Advanced](#advanced) - Additional information for advanced users.
 * [Known Issues](#known-issues) - current or past issues known to exist.

### Quickstart

This script gives the example of (task name). 

```python
# Quickstart is a basic example using default parameters and input values for (task name).  
# First Initialize the Environment
	
	from gbdxtools import Interface 
    gbdx = Interface()
    raster = 's3://gbd-customer-data/PathToImage/image.tif'
    taskname = gbdx.Task("TaskNameInGBDX", raster=raster)

    workflow = gbdx.Workflow([ taskname ])  
    workflow.savedata(taskname.outputs.data, location="taskname")
    workflow.execute()

    print workflow.id
    print workflow.status
```
	
### Inputs

List input requirements or limitation and supported file formats such as: .TIF, .TIL, .VRT, .HDR.

The following table lists the (task name) task inputs.
All inputs are **required**

Name                     |       Default         |        Valid Values             |   Description
-------------------------|:---------------------:|---------------------------------|-----------------
raster                   |          N/A          | S3 URL   .TIF only              | S3 location of input .tif file processed through AOP_Strip_Processor.
data                     |         true          | Folder name in S3 location      | This will explain the output file location and provide the output in .TIF format.

**OPTIONAL SETTINGS: Required = False**

* List optional settings for the task here


### Outputs

The following table lists the (task name) task outputs.

Name | Required |   Description
-----|:--------:|-----------------
data |     Y    | This will explain the output file location and provide the output in .TIF format.
log  |     N    | S3 location where logs are stored.


### Advanced
Include a script example of a workflow with additional tasks linked together or a more complex workflow demonstrating advanced algorithm parameters
 
###Postman status @ 06/07/16

**Successful run with Tif file.  


**Data Structure for Expected Outputs:**

Explain the output format of the task (e.g. .TIF image type UINT8x1 and placed in the specified S3 Customer Location) (e.g.  s3://gbd-customer-data/unique customer id/named directory/).  

###Known Issues
1) List issues current or past with the task (e.g. Version x does not ingest vrt files)

For background on the development and implementation of (task name)  [Documentation under development](Insert link here)

