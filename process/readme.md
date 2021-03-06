# Running the Process
Please follow the instructions below to run the process.

## Run the Python Scripts

### 1. Fork the Repo
- Make sure that you have forked the repo onto your own GitHub account and that the repository is cloned onto your machine.
- Additionally, to make sure that your branch is up to date run the following in your command prompt / terminal window
    1. Change directory to the **global-indicators** folder on your machine
    1. Type the following:
        ```
        git pull upstream master
        ```

### 2. Download and Organize the Data
1.  Download the global input data from the cloudstor data folder. You can find the links to this data [HERE](https://docs.google.com/document/d/1NnV3g8uj0OnOQFkFIR5IbT60HO2PiF3SLoZpUUTL3B0/edit?ts=5ecc5e75).
1.  Rename the folder to **input** and place the folder of data in **global-indicators/process/data**.
1.  Create a second subfolder (this will be empty initially) named **output** in **global-indicators/process/data**.

### 3. Run Docker
1.  In the command prompt / terminal window, change your directory to the **global-indicators** folder. Then type the following
    ```
    Docker pull gboeing/global-indicators:latest
    ```
1.  Start running docker in your machine
    - On Windows:
        ```
        docker run --rm -it -v "%cd%":/home/jovyan/work gboeing/global-indicators /bin/bash
        ```
    - On Mac/Linux:
        ```
        docker run --rm -it -v "$PWD":/home/jovyan/work gboeing/global-indicators /bin/bash
        ```
1. Change directory to **global-indicators/process**

### 4. Run the Python Scripts
1.  Run scripts using the following code
    1.  ```python setup_config.py```
        1. Make sure to check on the list of cities within the ``setup_config.py``, it should include cities that you plan to analyze  
            1. You could either delete or add a pound sign (#) before each city you would NOT include in your analysis
    1.  ```python sp.py [SPECIFIC CITY NAME]```
        1.  Use the file name that can be found under the **process/configuration** folder for each city. Example: For Adelaide, type ```python sp.py adelaide```
        1.  Alternatively, a shell script wrapper **process_regions.sh** exists to run all study regions at once in sequence, and can be run using ```bash process_region.sh``` followed by a list of region names. For example,  ```bash process_region.sh adelaide hong_kong vic```
        1.  Make sure to run this line of code for every city that you wish to include before running ``aggr.py`` script
    1.  ```python aggr.py```
        1. If you do not wish to find the aggregate of all cities, make sure to ``setup_config.py`` is updated to reflect the cities that you would like to include. 
        1. Notice that you will get the final indicator geopackadge in **global-indicators/process/data/output** only after you run this ``aggr.py`` script

Note that it will take several hours to run these scripts, depending on the size of the study city.


## Run the Jupyter Notebooks (TODO)

1. Follow steps 1 and 2 from the instructions above
1. Run docker:
    1. In the command prompt / terminal window, change your directory to the global-indicators folder. Then type the following
         ```
         docker run --rm -it --name global-indicators -p 8888:8888 -v "$PWD":/home/jovyan/work gboeing/global-indicators
        ```
2. Open a web browser and visit http://localhost:8888
3. Run the Jupyter Notebooks

Note that it will take several hours to several days to run these scripts, depending on the size of the study city.


## Run the Jupyter Notebooks (TODO)

1. Follow steps 1 and 2 from the instructions above
1. Run docker:
    1. In the command prompt / terminal window, change your directory to the global-indicators folder. Then type the following
         ```
         docker run --rm -it --name global-indicators -p 8888:8888 -v "$PWD":/home/jovyan/work gboeing/global-indicators
        ```
2. Open a web browser and visit http://localhost:8888
3. Run the Jupyter Notebooks

