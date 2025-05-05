Half of the notebooks were made to build a dataset, the other half was used to build models
Data - some of the datasets have been zipped for github
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
Models 
    - random_forest.ipynb - dependent on test_dataset_encoded and test_dataset_label_encoded
        -  builds random_forest classifiers on both datasets
    - transformer.ipynb - dependent on test_dataset_encoded and test_dataset_label_encoded
        - builds transformer classifiers on both datasets 
