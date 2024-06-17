## Supplementary Materials (Code) for
# "Minus-One" Data Prediction Generates Synthetic Census Data with Good Crosstabulation Fidelity

William H. Press<br>
[arXiv:2406.05264](https://arxiv.org/abs/2406.05264) [Submitted on 7 Jun 2024]

## Abstract of the Paper

We propose to capture relevant statistical associations in a dataset of categorical survey responses by a method, here termed MODP, that "learns" a probabilistic prediction function L. Specifically, L predicts each question's response based on the same respondent's answers to all the other questions. Draws from the resulting probability distribution become synthetic responses. Applying this methodology to the PUMS subset of Census ACS data, and with a learned L akin to multiple parallel logistic regression, we generate synthetic responses whose crosstabulations (two-point conditionals) are found to have a median accuracy of ~5% across all crosstabulation cells, with cell counts ranging over four orders of magnitude. We investigate and attempt to quantify the degree to which the privacy of the original data is protected. 

## U.S. Census PUMS Data Dictionary

Included as `PUMS_Data_Dictionary_2022.pdf`, this decodes the response codes to all U.S. Census PUMS questions. Note, however, that some questions are converted to deciles or remapped for this analysis in making the STUMS and STUMS-H reduced datasets.

## Provided Code

Code is provided as Jupyter notebooks intended to be executed cell by cell. Doing so for the main notebook will reproduce the figures (and thus principal conclusions) in the main paper.

### Prerequisites

- Python 3 with installed Jupyter
- Other packages as indicated by `import` statements in the notebooks
- PyTorch with an available GPU

### Notebooks

Two notebooks are provided. The notebook `Census_GitHub.ipynb` is the main one. The supplementary notebook `Census_Make_STUMS.ipynb` documents how the STUMS and STUMS-H datasets are produced from the original U.S. Census downloaded data. It does not normally need to be run, but is included to document reproducibly how some PUMS questions are converted to deciles or reduced responses.

## Included Input Data Files Used by the Notebooks

### Main Notebook

- `STUMS_df_all.pkl`: Pandas dataframe of the STUMS data (see paper). Can be read by `df = pd.read_pickle("yourpath/STUMS_df_all.pkl")`.

- `STUMS_weights_df.zip`: Zipped Pandas dataframe for the Census weights of the STUMS rows. Not used but included here for completeness.

- `STUMS-H_df_all.pkl`: Pandas dataframe of the STUMS-H data (see paper Supplementary Materials). Can be read by `df = pd.read_pickle("yourpath/STUMS-H_df_all.pkl")`.

- `STUMS-H_weights_df.zip`: Zipped Pandas dataframe for the Census weights of the STUMS-H rows. Not used but included here for completeness.

### Supplementary Notebook

- `psam_ptx.zip` and `psam_htx.zip` are respectively the U.S. Census PUMS person and housing 2022 datasets for the state of Texas, as zipped comma separate variable text files. You must unzip before using.

- `PUMS_Data_Dictionary_2022.txt` contains the contents of `PUMS_Data_Dictionary_2022.pdf` as a text file.

## Included Pre-Trained Models Used by the Main Notebook

The files `model_1_1.sav`, `model_3_10.sav`, `model_5_15.sav`, and `model_12_24.sav` are pre-trained models that can be loaded by the notebook. Here model_x_y denotes a model with x blades and y reduced features (see paper). The 5_15 model is the best.

The file `model-h_5_15.sav` is pre-trained for the STUMS-H data (see paper Supplementary Materials).












