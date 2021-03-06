# silo - Interactive Signal Averaging App

This app takes data exported from labchart and allows the user to pull cardiovascular and respiratory data points based off physiological triggers.  It then averages the data and allows the user to export the data in either csv form or in the form of a figure. 

## Getting Started
 
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

R and RStudio installed
Required ibraries download automatically


### File Extraction from LabChart

1. Set O<sub>2</sub> and CO<sub>2</sub> delays in labchart - optional - use if you don't have Airforce auto calibrate app

#### Carviovascular and Respiratory Files

1. Set time mode to: **"Show time from start of file"**
    - right click on time scale at the bottom
    - check **"Show time as seconds"**
2. Arrange **Data Pad** columns to include channels of interest
    - Be sure to include a column for **Time**
    - Include comments channel if you want to pull manual blood pressure values for bpCorrect app
3. Setting **Event Markers**<br>
    **Respiratory** - need event markers on Volume channel 
    **Cardiovascular** - need event markers on Finometer (systolic) or ECG (R-Wave) trace
4. Add data to Data Pad - *Respiratory*
      - Highlight section to be extracted
      - Select **multi-add to Data Pad**
      - Find using: **Event Marker**
      - From channel: **Volume** for respiratory file; **BP or ECG** for cardiovascular file
      - Select: **event marker**
      - Step through: **Whole file**
      - **Add**
      - Click the **File** > **Export..**
      - Save as type: **Data Pad Only as Test File**
      - Name file based on naming convention (below)
5. Repeat step 5. for **Cardiovascular** data 
      - From channel: **ECG** or **Finometer**
      
#### MSNA Files (Optional)

1. Analyze the **MSNA integrated** channel using the **peak analysis** module in Labchart.
  - Set cutoff according to baseline noise
  - Optimize peak detection settings.
  - Setup table in peak analysis settings to include time and date, along with variables of interest. Time and date should be in the furthest right column       of your table.
  - When happy with peak detection, export in .csv format from the peak analysis table view.
2. Open in Excel and review each burst. Delete those that are not MSNA bursts.
          
### File Naming Conventions

  File name format: **typeOfData_subjectID_cond1_cond2.txt** <br>
  - typeOfData: 'breath' (Respiratory File), 'beat' (CV File) or 'burst' (MSNA File) <br>
  - SubjectID: Unique subject identifier eg.'07' <br>
  - Cond(s): Unique conditons (up to 3) eg. 'hx'; 'pre' <br>
      - eg. 'breath_07_hx_pre.txt' <br>
  - NB. Naming must be consitent

### Deployment
1. Download Zip file from Git (green button, top right)
2. Extract to folder of choice
3. load beat, breath and burst data files into **silo\rawData** folder (user must create 'rawData' folder in the silo\ directory) 
3. Open **Silo.Rproj**
4. From the file explorer in RStudio, open **Silo x.y.z.R** or **silo-bpCorrect** 
5. Click run app in the script editor (source) pane
  - be sure to run app externally (from drop down menu next to "run")

## Authors

* **Lindsey M Boulet** 

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Stuckless T
* Brown CV
* Vermeulen TD
* Foster GE

# Silo
