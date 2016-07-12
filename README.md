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
    - There's a problem with using $offset in trying to page through sfgov.org data via API that is a work in progress. See the `notebooks/exploratory` folder for more details
  - 7/12/2016
    - new notebook 0.2 for debugging and finally solving the $offset problem
    - new notebook 0.3 for new initial exploration
    - added credentials for accessing a geo lookup via geonames.or

### Requirements

 - Python2
 - Jupyter notebook
 - Pandas library
 - For geolookup, create a free account with http://www.geonames.org/login

### Installation instructions

 - Clone this repo to your local machine
 - `cd notebooks` to get to the notebooks folder
 - run `jupyter notebook`
 - a browser window should appear, click on `exploratory`
 - click on the latest version of the notebook
 - In the root project directory, create a .env file and store your credentials
    - For instance if you want to use the geonames.org data, add a config file with your username after registering for an account at www.geonames.org/login
    - **NEVER commit the ``.env` file!**
 - have fun!

### About the .env file

The `.env` file never goes into source control. It's where your secrets live, your personal credentials.

Below is the header of the template `.env` file, so you can create your own personal one. It also includes instructions on how to import the variables into a python script

```
# Environment variables go here, can be read by `python-dotenv` package:
#
#   `src/script.py`
#   ----------------------------------------------------------------
#    import dotenv
#
#    project_dir = os.path.join(os.path.dirname(__file__), os.pardir)
#    dotenv_path = os.path.join(project_dir, '.env')
#    dotenv.load_dotenv(dotenv_path)
#   ----------------------------------------------------------------
#
# DO NOT ADD THIS FILE TO VERSION CONTROL!
#
# example .env file
DATABASE_URL=postgres://username:password@localhost:5432/dbname
AWS_ACCESS_KEY=myaccesskey
AWS_SECRET_ACCESS_KEY=mysecretkey
OTHER_VARIABLE=something
```

### TODOs and TASKS

    - PRIORITY: figure out the proper use of `$offset` for accurate pagination
    - Even though the above may only look at type=fire, in reality the non-fire emergencies calls are an input for training. Those need to be added back in
    - check how many times a code 2 turns into a code 3 as the final priority
    - sign up for an app token: https://dev.socrata.com/foundry/data.sfgov.org/enhu-st7v
