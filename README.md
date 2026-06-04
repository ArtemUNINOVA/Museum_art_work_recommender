# Museum Art Work Recommender System
This repository contains Jupyter Notebook scripts for a museum artwork recommender system. It also includes a subset of the BIRD dataset 
containing the data used in this work. The complete dataset can be retrieved from the BIRD repository:

https://gitlab.univ-lorraine.fr/worm1/bird-dataset

To properly acknowledge the BIRD dataset, please cite the following publication:

Alexanne Worm, Florian Marchal, and Sylvain Castagnos. 2025. BIRD: A Museum Open Dataset Combining Behavior Patterns and Identity Types to 
Better Model Visitors’ Experience. In Adjunct Proceedings of the 33rd ACM Conference on User Modeling, Adaptation and Personalization (UMAP 
Adjunct ’25), June 16–19, 2025, New York City, NY, USA. ACM, New York, NY, USA, 5 pages. https://doi.org/10.1145/3708319.3733686


## Repository Overview
**dataset/Nancy_museum**
- Contains files from the BIRD dataset, including:
  - _start_obs_artworks_ and _end_obs_artworks_, which contain the start and end timestamps for each user and the artworks they observed.
  - _artworks_dataset_, which contains metadata describing the museum artworks.
  - _post_questionnaire_formatted_, which contains user-specific information, such as self-reported knowledge levels.

**initial_data_preprocessing** - performs the initial preprocessing steps and combines information from multiple files into a single DataFrame.

**LLM_feature_extractor** - extracts genre and style features using an LLM to enrich the original BIRD dataset and improve recommendation
performance.

**data_preprocessing_recommender** - performs the final data preparation for Machine Learning (ML), including normalization, one-hot and multi-hot
encoding, and embedding generation.

**ML_recommender** - contains the deep learning recommender model together with the auxiliary functions required for training, evaluation, and
feature-permutation analysis.

**processed_data** contains CSV files generated throughout the data-processing pipeline.

**models** - contains trained models for both experimental scenarios, together with result files and generated plots.


## Execution Order
**Run initial_data_preprocessing.** 
- generates pre_processed_ds.csv in the processed_data folder.

**Run LLM_feature_extractor.**
- Uses pre_processed_ds.csv as input.
- Generates genre and style features.
- Produces extended_paintings_dataset_BIRD.csv in the processed_data folder.

**Run data_preprocessing_recommender.**
- Uses extended_paintings_dataset_BIRD.csv and pre_processed_ds.csv as inputs.
- Produces ml_ready_dataset.csv in the processed_data folder.

**Run ML_recommender.**
- Uses ml_ready_dataset.csv as input.
- Performs hyperparameter tuning and 5-fold cross-validation.
- Saves the best-performing model in the models folder together with result files and plots.

**Run plotting.**
- Uses the generated result files.
- Computes evaluation metrics and generates box plots.


## Acknowledgment

This work was supported by the FITTER-EU project (Grant Agreement No. 101132546) and by the Portuguese Foundation for Science and Technology 
(FCT) under project UIDB/00066/2020.

The views and opinions expressed are solely those of the authors and do not necessarily reflect those of the European Union or the European 
Research Executive Agency (REA). Neither the European Union nor the granting authority can be held responsible for them.


## Citation

If you find this repository useful in your research, please cite:

Shabnam Pasandideh, Artem A. Nazarenko, Joao Sarraipa, Sofia Almeida. Digital Transformation in Museums under the Framework of Cyber-Physical-Social Systems.



## License

**Source Code**

All source code in this repository is licensed under the MIT License unless otherwise specified.

**Dataset (dataset/Nancy_museum)**

This repository contains portions of a dataset licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International 
License (CC BY-NC-SA 4.0).

Copyright remains with the original dataset authors.

**Derived Data**

The contents of the processed_data folder, as well as the files:

- test_predictions_LLM_enhanced.csv
- test_predictions_LLM_enhanced_and_user_info.csv

located in the models folder, are derived from the original dataset and are distributed under the CC BY-NC-SA 4.0 license.

**Attribution**

Please cite and attribute the original dataset in accordance with its licensing requirements.
