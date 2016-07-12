fire_risk
==============================

Predict San Francisco Fire Risks


Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │   |                     the creator's initials, and a short `-` delimited description, e.g.
    │   |                     `1.0-jqp-initial-data-exploration`.
    |   |
    │   └── exploratory    <- Experimental, unrefined notebooks.
    │   └── reports        <- Polished notebooks that export html to the reports directory.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.testrun.org


## More README stuff

This file structure was created programmatically using this cookiecutter:
https://drivendata.github.io/cookiecutter-data-science/

Please take a look at the link above, and use it to follow best practices, for instance naming conventions for Notebooks etc.


### Changelog

 - 7/11/2016
    - adding the list of SFFD data from SF Open Data.gov website https://data.sfgov.org/resource/kikm-y2iv.json
    - creating first exploratory data analysis notebook using the link above with pandas
    - updating the data.sfgov.org json url to only provide fire links. After reviewing the live explorer online, it seems to make sense to make the core data for instances of fire risk prevention failure be final_priority=3 ('Emergency') and call_type_group='Fire'


### TODOs and TASKS

    - TODO: even though the above may only look at type=fire, in reality the non-fire emergencies calls are an input for training. Those need to be added back in
    - check how many times a code 2 turns into a code 3 as the final priority
    - 
