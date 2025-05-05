Half of the notebooks were made to build a dataset, the other half was used to build models

Data - some of the datasets have been zipped for github
    - MATCHIDS_PATCH13.4_NA_BR_EUW_KR
        - built from MatchIdGather
    - dataset_NA_BR_EUW_KR_section1
        - built from GameDataBuild
    - dataset_NA_BR_EUW_KR_section2
        - built from GameDataBuild
    -test_dataset_encoded
        - built from encode_data 
    -test_dataset_label_encoded
        - built from encode_data
Jupyter
    Notebooks for data - This will not run without a RIOT API Key
        - MatchIDGather.ipynb 
            - Grabs challengers and their match IDS (aka the games the played) from the regions NA1, BR1, EUW1, KR -- China was exluded because they play on a different version of the game
            - Saved to MATCHIDS_PATCH13.4_NA_BR_EUW_KR
        - GameDataBuild.ipynb - dependent on MatchIDGather data
            - Takes match IDs to get board and placement data from those matches
            - Because of call limits to API, this was pulled in multiple runs to get dataset_NA_BR_EUW_KR section 1 and 2
        - encode_data.ipynb - dependent on GameDataBuild data
            - encodes match data for models in multiple ways
            - produces test_dataset_encoded and test_dataset_label_encoded
            - one hot encoding is not succesful, takes too much memory 
    Notebooks for models - These will run with the unzipped data files
        - random_forest.ipynb - dependent on test_dataset_encoded and test_dataset_label_encoded
            -  builds random_forest classifiers on both datasets
        - transformer.ipynb - dependent on test_dataset_encoded and test_dataset_label_encoded
            - builds transformer classifiers on both datasets 
