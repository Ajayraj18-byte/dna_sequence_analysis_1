# DNA Sequence Analysis and Splice Site Classification

## Project Overview

This project applies machine learning techniques to classify DNA sequences into splice-junction categories using Python and Scikit-learn.

The project uses the Molecular Biology (Splice-junction Gene Sequences) dataset to distinguish between exon-to-intron junctions, intron-to-exon junctions, and sequences that do not belong to either specified junction category.

The workflow includes data loading, data quality checks, nucleotide-level feature extraction, model training, performance evaluation, model comparison, and prediction of new DNA sequences.

## Objectives

- Analyze and clean DNA sequence data.
- Examine sequence lengths, nucleotide symbols, duplicate records, and class distribution.
- Represent each nucleotide position as a categorical feature.
- Train and compare Logistic Regression and Random Forest classifiers.
- Evaluate classification performance using accuracy, macro F1-score, and classification reports.
- Predict the splice-junction category of a new DNA sequence.

## Dataset

**Dataset:** Molecular Biology (Splice-junction Gene Sequences)

**Source:** UCI Machine Learning Repository

https://archive.ics.uci.edu/dataset/69/molecular+biology+splice+junction+gene+sequences

The dataset contains DNA sequences belonging to three classes:

- **EI:** Exon-to-intron junction (donor site)
- **IE:** Intron-to-exon junction (acceptor site)
- **N:** Neither of the specified splice-junction types

The dataset is loaded from `data/splice.data`.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Jupyter Notebook (for notebook-based execution, if applicable)

## Machine Learning Workflow

### 1. Data Loading and Cleaning

- Load the dataset using Pandas.
- Assign column names for class, instance identifier, and DNA sequence.
- Remove leading and trailing whitespace.
- Convert DNA sequences to uppercase.
- Check for missing values.
- Remove exact duplicate rows.
- Inspect sequence lengths and nucleotide symbols.

### 2. Feature Engineering

Each DNA sequence is converted into a set of nucleotide-position features. Every position is represented as a categorical variable, and `OneHotEncoder` transforms these categorical features into a numerical representation suitable for the classifiers.

### 3. Train-Test Split

The dataset is divided into:

- **80% training data**
- **20% testing data**

The split uses `random_state=42` for reproducibility and stratification to preserve class proportions.

### 4. Model Training

Two classification models are trained using Scikit-learn pipelines:

- **Logistic Regression:** Uses one-hot encoded nucleotide features and a maximum of 2,000 iterations.
- **Random Forest:** Uses 200 trees, balanced class weights, and a fixed random seed.

### 5. Model Evaluation

Both models are evaluated using:

- Accuracy
- Macro F1-score
- Precision, recall, and F1-score by class through the classification report
- Confusion matrix for Logistic Regression

The models are compared using macro F1-score, which gives equal weight to each class. The model with the higher macro F1-score is selected for subsequent predictions.

### 6. New DNA Sequence Prediction

A prediction function accepts a DNA sequence, checks its length and nucleotide symbols, and predicts its class using the selected model.

The notebook also demonstrates the prediction function using a sequence from the dataset. This is a functionality demonstration, not an independent evaluation sample.

## Project Structure

```text
dna_sequence_analysis/
├── data/
│   └── splice.data
├── Model/
├── Results/
├── dna_sequence_analysis.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

The notebook filename and folder contents should match the actual repository. The `Model/` and `Results/` folders may contain saved artifacts or outputs if these have been generated.

## Installation and Execution

### Prerequisites

- Python 3.10 or a compatible Python version
- pip
- Jupyter Notebook or VS Code with notebook support

### Setup

1. Clone or download the repository.
2. Open a terminal in the project directory.
3. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Ensure the dataset is available at `data/splice.data`.
5. Open the notebook in Jupyter Notebook or VS Code.
6. Run the notebook cells in order.

## Results

The notebook prints the following outputs:

- Dataset dimensions before and after duplicate removal
- Missing-value and sequence-length checks
- Class distribution and feature dimensions
- Training and testing record counts
- Accuracy and macro F1-score for both classifiers
- Classification reports and a Logistic Regression confusion matrix
- Model comparison and selected classifier
- Example DNA sequence prediction

Actual numerical results should be taken from the completed notebook execution.

## Limitations

- Performance depends on the dataset, feature representation, and train-test split.
- The current implementation uses nucleotide-position features and does not implement advanced biological sequence embeddings.
- The demonstration prediction uses a sequence from the dataset and should not be interpreted as evidence of generalization to an unseen external dataset.
- Model selection is performed on the same held-out test results used for reporting. A separate validation set or cross-validation would provide a more rigorous model-selection process.

## Future Improvements

- Evaluate models using cross-validation.
- Compare additional classification algorithms.
- Investigate biologically informed sequence features and alternative encoding methods.
- Improve model evaluation with per-class confusion matrices and visualizations.
- Test generalization using an independent dataset.

## Author

**Ajay Raj**  
Biomedical Engineering Student

This project demonstrates the application of Python-based machine learning to DNA sequence analysis and splice-site classification.