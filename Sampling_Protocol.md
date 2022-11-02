# Sampling protocol for Dark Genes Meta Analysis

## Overview:
1. [**Confirm study is appropriate**](#confirm)
2. [**Locate files and metadata**](#locate)
3. [**Input comparison metadata into “RNAseq_Data” spreadsheet**](#data)
4. [**Input sample metadata into “RNAseq_Samples” spreadsheet**](#samples)

## <a name="confirm"></a> Step 1: Confirm study is appropriate

1. Pull data from [this spreadsheet](https://docs.google.com/spreadsheets/d/1ScX6AoRWQlxoszbX36I-pMBD5XGWKrxVqukirGzGOcI/edit#gid=0) on the "Studies" tab
2. Confirm it has not been completed (cells are not colored)
3. Search and download the paper from [Google Scholar](https://scholar.google.com/)
4. Once you have the paper open, make sure it completes **ALL** of the following criteria:
  * Includes corals or other cnidarians
  * Uses RNA-seq methods (not tag-seq or microsatellites)
  * Has a clear experimental “control” and “heated” sample comparison
5. If it **does not** meet the above criteria, highlight the whole row red and move on to the next study
6. If it **does** meet the above criteria, move on to Step 2!

## <a name="locate"></a> Step 2: Locate files and metadata

* For each study in the *Methods* or *Data Availability* sections there should be statements relating to where the RNA-seq data can be located.
* We are interested in taking data from [NCBI](https://www.ncbi.nlm.nih.gov/). You can retrieve this data by searching for the *BioProject* or *Accession Number*.
* Once you have found the correct BioProject, use the following steps to find the metadata sheet:
  1. Under "Project Data", click **SRA Experiments**
![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/BioProject_Example.png)

  2. Click **Send to:**
  ![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/SRA_Example.png)

  3. Choose Destination: **File**
  4. Format: **RunInfo**
![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/RunInfo_Example.png)


This `SraRunInfo.csv` file will provide you with most (but maybe not all) of the information needed for the following steps. In this file, make sure you filter for only RNA-seq data and delete any other sequence data that is not relevant (e.g. amplicon sequencing)


## <a name="data"></a> Step 3: Input comparison metadata into “RNAseq_Data” spreadsheet

* Next, you will need to be a detective and piece together all of the available information to fill the columns in [this spreadsheet](https://docs.google.com/spreadsheets/d/1ScX6AoRWQlxoszbX36I-pMBD5XGWKrxVqukirGzGOcI/edit#gid=0) under the appropriate “RNAseq_Data” tab
  * i.e. RNAseq_Data_GH or RNAseq_Data_ED
* This spreadsheet is designed to have each row as a comparison between heated and control samples, therefore one study may have **multiple** comparisons.
  * For example, if a study had an experimental design by comparing ambient temperatures (30&deg;C) to medium (33&deg;C) and high (36&deg;C) temperatures, there would be a row for each comparison (in this case; 2).
* Below I have provided a brief description of each column and potential ways on how to locate this information.
* **NOTE:** If you are unsure about anything, please do not enter in the data. Just fill what you can and make a comment in the "Other_comments" column. Make a note of it and tell Kevin or Natalia.


### DOI

* DOI stands for Digital Object Identifier. All publications have this and should be
* This is usually located underneath the author list on the publication
* Just include everything after doi.org/
* Example: "10.1111/mec.16064"

### Reference

* Please insert the reference with the first author, et al. (if there are co-authors), and the date
* Example: Voolstra et al. 2021

### Comparison_ID

* Each comparison ID should be unique to each row. The comparison ID is comparing TWO groups within the study (i.e. heated vs control), thus one study can have more than one comparison ID
* Each comparison within a study should start with A. If a study has more than one comparison, continue in alphabetical order.
* The format for this column should be the following: **"Reference Name"-"Date"-"Comparison Letter"**
  * Example: "Voolstra-2021-A"
* In a special case where a first author has more than one published relevant study in the same year, you can denote this by adding a "_2" after the year
  * Example: "Voolstra-2021_2-A"

### Species

* Use the full latin name of the species
* Example: Stylophora pistillata

### Sample_Location

* Be as specific as you can, but at least input the country it was sampled from.
* If you can, input it as the following: "reef name", "State", "Country"
  * Leave any blank if you cannot find all of this information

### Coordinates

* Coordinates can usually be found in the methods section. If you cannot find it, input "NA".

### Life Stage

* Input this as the following options:
  * Adult
  * Juvenile (newly settled recruits)
  * Larvae
  * Eggs
  * Sperm

### High_temp

* This is the experimental temperature of the "heat stress" treatment.
* Enter this number in Celsius

![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/High_temp_Example.png)

### Control_Temp

* This is the experimental temperature of the "control" or "ambient" treatment.
* Enter this number in Celsius

![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/Control_Example.png)

### Ramp_up_rate

* Ramping rate is the rate of temperature increase to achieve experimental temperatures (typically the high temperature)
* This can be found in Methods section of the paper
* This format can be inputted as a temperature (Celcius) per time (hour)
  * Example: 2 per hour

![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/Ramp_Example.png)

### Acclimation_Period

* Acclimation period refers to how long the corals were in the tank prior to any experimental manipulation
* This can be inputted in "days" format

![ ](https://github.com/kevinhwong1/DarkGenes_MetaAnalysis/blob/main/images/Acclimation_Example.png)

### Duration_inDay

* This refers to how long the temperature treatment lasted in days
* If the study refers to hours, calculate this into decimal days (i.e. 3 hours/24 hours = 0.125 days)

### Replicates

* This refers to how many replicates there are per treatment condition (i.e. heated or ambient)
* This number should also match how many samples there are per treatment group in the "RNAseq_Samples" tab

### NCBI_BioProject

* Here add the NCBI BioProject number

### Data_File_Link

* Here add the link to the NCBI BioProject

### Paper_Link

* Here add the link to the manuscript

### Other_Comments

* Here add any comments that should be noted about this comparison or if you had troubles with retrieving any of this data

## <a name="samples"></a> Step 4: Input sample metadata into “RNAseq_Samples” spreadsheet

* Next, we will address the samples corresponding to each Comparison_ID and you will find of the available information to fill the columns in [this spreadsheet](https://docs.google.com/spreadsheets/d/1ScX6AoRWQlxoszbX36I-pMBD5XGWKrxVqukirGzGOcI/edit#gid=0) under the appropriate “RNAseq_Samples” tab
  * i.e. RNAseq_Samples_GH or RNAseq_Samples_ED
* This spreadsheet is designed to have each row as a samples (i.e. ONE file)
  * For example, if a study had an experimental design by comparing ambient temperatures (30&deg;C) to high (33&deg;C) with three samples per treatment group, there should be six samples (i.e. six rows) for this comparison.
* Below I have provided a brief description of each column and potential ways on how to locate this information.
* **NOTE:** If you are unsure about anything, please do not enter in the data. Just fill what you can and make a comment in the "Other_comments" column. Make a note of it and tell Kevin or Natalia.

### Treatment_ID

* Treatment_ID is something that you can come up with that relates to that specific group within a comparison.
* It should always start with the treatment (i.e. "HighTemp" or "Control") then any specific comparison descriptor (i.e. location)
* Be consistent, name this logically, and do not include any spaces or special characters

### Comparison_ID

* This should match the rows in the “RNAseq_Data” tab
* The controls will likely be compared to more than one group if the study has multiple comparisons.
  * If this occurs, then input the ID of the second comparison in the Comparison_ID_2 column. This will help us understand that this specific sample is used in multiple comparisons
  * Rememeber that this should only be applied for the controls!

### DOI

* See Step #3

### Reference

* See Step #3

### Species

* See Step #3

### TaxID

* This numeric code is the taxonomic ID of the species on NCBI
* This can be found on the NCBI BioProject web page and in the `SraRunInfo.csv` under the "TaxID" column

### Sample_Location

* The can just be the specific reef site where the corals were collected from

### Life_Stage

* See Step #3

### Library_Name

* Each samples (i.e. row) should have a unique library name
* You can copy this data over from the `SraRunInfo.csv` data sheet you downloaded from Step #2
  * Ensure you are only copying over the RNAseq data and nothing other (e.g. amplicon seq data)

### Accession_Experiment

* Each samples (i.e. row) should have a unique Experiment Accession
* You can copy this data over from the `SraRunInfo.csv` data sheet you downloaded from Step #2
  * Ensure you are only copying over the RNAseq data and nothing other (e.g. amplicon seq data)

### Temp

* This refers to the specific temperature this sample experienced in Celsius

### Symbiont_Type

* If available, input the symbiont type that these corals harbored
* Put NA if not clear

### Download_path

* Each sample (i.e. row) should have a separate download path
* Copy the contents of 'download_path' in the `SraRunInfo.csv` file
  * Ensure you are only copying over the RNAseq data and nothing other (e.g. amplicon seq data)
