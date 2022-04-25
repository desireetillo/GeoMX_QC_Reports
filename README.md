# GeoMX DSP initial QC reports

Rmarkdown used for rendering an initial QC report for GeoMX RNA-NGS data sets.  Uses most steps from [GeoMXWorkflows](https://www.bioconductor.org/packages/release/workflows/html/GeoMxWorkflows.html).


## Inputs
Expects input data directory to be organized as follows:


```
DATA_DIRECTORY
|-- DCC_folder
|-- pkc_file.pkc
|-- annotations.xlsx
```

Where: 

* `DCC_Folder` is the directory containing the Digital Count Conversion (*.dcc) files from the Nanostring NGS pipeline.
*  `pkc_file` is the probe-gene configuration file for the specific assay (WTA/CTA) and species (mouse/human), obtained [here] (https://nanostring.com/products/geomx-digital-spatial-profiler/geomx-dsp-configuration-files/) (select "RNA Assays").
* `annotations.xlsx` is an excel file containing metadata for each ROI.  The sheet containing this information should be named "Template", and requires these specific columns:
	*  area 
	*  nuclei 
	*  class (e.g. condition/treatment)
	*  type (e.g morphology/physiology)



## Rendering reports

### Default inputs 
```
rmarkdown::render('GeoMX_TA_InitialQC_parameterized.Rmd',
                  output_file = 'demo.html'
        )
```

### Customized inputs
```
rmarkdown::render('GeoMX_TA_InitialQC_parameterized.Rmd',
                  output_file = 'output_filename.html',
                  params=list(projectname=<YOUR_PROJECT_NAME>,
                              output_prefix=<OUTPUT_PREFIX>,
                              datadir=<DATA_DIRECTORY>,
                              DCCdir=<DCC_DIRECTORY_NAME>,
                              PKCFilename=<PKC_FILE_NAME>,
                              WorkSheet=<WORKSHEET_FILE_NAME>
                  )
)```


