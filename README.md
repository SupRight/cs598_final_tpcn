
# CS598 Final report
===============================

This repository contains the code used to reproduce **Temporal Pointwise Convolutional Networks for Length of Stay Prediction in the Intensive Care Unit** (published at **ACM CHIL 2021**) and implementation instructions. 


## Pre-Processing Instructions

### eICU

1) To run the sql files you must have the eICU database set up: https://physionet.org/content/eicu-crd/2.0/. 

2) Follow the instructions: https://eicu-crd.mit.edu/tutorials/install_eicu_locally/ to ensure the correct connection configuration. 

3) Replace the eICU_path in `paths.json` to a convenient location in your computer, and do the same for `eICU_preprocessing/create_all_tables.sql` using find and replace for 
`'/Users/emmarocheteau/PycharmProjects/TPC-LoS-prediction/eICU_data/'`. Leave the extra '/' at the end.

4) In your terminal, navigate to the project directory, then type the following commands:

    ```
    psql 'dbname=eicu user=eicu options=--search_path=eicu'
    ```
    
    Inside the psql console:
    
    ```
    \i create_all_tables.sql
    ```
    
    This step might take a couple of hours.
    
    To quit the psql console:
    
    ```
    \q
    ```
    
5) Then run the pre-processing scripts in your terminal. This will need to run overnight:

    ```
    preprocess.ipynb
    ```
    
   
## Running the models
1) Once you have run the pre-processing steps you can run all the models in your notebook / google colab. run the following notebook from start to the end.

    ```
    tpcn_reproduce.ipynb
    ```