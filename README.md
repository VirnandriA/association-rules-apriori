# Association Rules Analysis using Apriori

This project applies the **Apriori algorithm** to analyze purchasing patterns in a grocery transaction dataset. The analysis focuses on identifying frequent itemsets and exploring **negative association rules**, which describe relationships where the presence of one item is associated with the absence of another item within a transaction.

The project was developed using Python, with data processing performed using Pandas and association rule mining using the `mlxtend` library.

## Project Overview

Association Rule Mining is a data mining technique used to discover relationships and patterns among items within transactional data.

In this project, grocery transaction data is processed and transformed into a suitable format for association rule mining. The Apriori algorithm is then used to identify frequent itemsets, followed by an analysis of non-trivial negative association rules.

The main objectives of this project are:

- Prepare and transform grocery transaction data.
- Identify frequent itemsets using the Apriori algorithm.
- Analyze relationships between frequently purchased items.
- Identify non-trivial negative association rules.
- Calculate support, confidence, and negative lift.
- Visualize the discovered negative association rules.

## Dataset

The dataset contains grocery transaction records with the following columns:

| Column | Description |
|---|---|
| `Member_number` | Unique identifier for the customer |
| `Date` | Transaction date |
| `itemDescription` | Item purchased in the transaction |

The dataset contains:

- **38,765 transaction records**
- **14,963 unique transactions**
- **167 unique items**

Transactions are identified using a combination of `Member_number` and `Date`.

## Methodology

The analysis consists of several stages.

### 1. Data Loading and Preparation

The dataset is loaded using Pandas and the `itemDescription` column is cleaned by removing unnecessary spaces.

The data is then grouped using `Member_number` and `Date` to create a list of items belonging to each unique transaction.

### 2. Transaction Encoding

The transaction data is converted into a binary representation using `TransactionEncoder`.

Each row represents a transaction, while each item becomes a column.

### 3. Frequent Itemset Mining

The **Apriori algorithm** is applied with a minimum support threshold of `0.01`.

The analysis identified **69 frequent itemsets**.

Some of the most frequent individual items include:

| Item | Support |
|---|---:|
| whole milk | 0.157923 |
| other vegetables | 0.122101 |
| rolls/buns | 0.110005 |
| soda | 0.097106 |
| yogurt | 0.085879 |
| root vegetables | 0.069572 |
| tropical fruit | 0.067767 |
| bottled water | 0.060683 |
| sausage | 0.060349 |
| citrus fruit | 0.053131 |

### 4. Negative Association Rules

After identifying frequent itemsets, the project explores **negative association rules**.

A negative association rule can be represented as:

**A → ~B**

where `A` represents the presence of an item and `~B` represents the absence of another item.

For example:

**whole milk → ~yogurt**

The analysis uses a minimum confidence threshold of `0.50`.

Pairs that never occur together are excluded from the analysis to focus on non-trivial negative associations.

## Results

The analysis identified **10 negative association rules** with confidence greater than or equal to `0.50`.

| Antecedent | Consequent | Support | Confidence | Negative Lift |
|---|---|---:|---:|---:|
| whole milk | ~yogurt | 0.1468 | 0.9293 | 1.0166 |
| whole milk | ~soda | 0.1463 | 0.9264 | 1.0260 |
| other vegetables | ~rolls/buns | 0.1115 | 0.9135 | 1.0264 |
| whole milk | ~rolls/buns | 0.1440 | 0.9116 | 1.0242 |
| whole milk | ~other vegetables | 0.1431 | 0.9061 | 1.0321 |
| rolls/buns | ~other vegetables | 0.0994 | 0.9040 | 1.0297 |
| soda | ~whole milk | 0.0855 | 0.8802 | 1.0453 |
| other vegetables | ~whole milk | 0.1073 | 0.8785 | 1.0432 |
| rolls/buns | ~whole milk | 0.0960 | 0.8730 | 1.0368 |
| yogurt | ~whole milk | 0.0747 | 0.8700 | 1.0332 |

The discovered rules show several high-confidence negative associations among frequently purchased grocery items. These relationships can be further explored to understand purchasing behavior and potential product combinations or exclusions.

## Visualization

The project includes visualization of the discovered negative association rules.

The visualization is used to compare the confidence values of the identified rules and make the results easier to interpret.

## Technologies

- Python
- Pandas
- mlxtend
- Matplotlib
- Google Colab
- Jupyter Notebook

## Project Structure

association-rules-apriori/
├── README.md
├── Groceries_dataset.csv
└── association_rules.ipynb

## How to Run

1. Clone the repository:

git clone https://github.com/VirnandriA/association-rules-apriori.git

2. Navigate to the project directory:

cd association-rules-apriori

3. Install the required libraries:

pip install pandas mlxtend matplotlib

4. Open `association_rules.ipynb` using Jupyter Notebook or Google Colab.

Make sure `Groceries_dataset.csv` is available in the same directory as the notebook.

## Key Parameters

The main parameters used in the analysis are:

- Minimum support: `0.01`
- Minimum confidence: `0.50`

These parameters determine the minimum frequency of itemsets and the minimum confidence required for a negative association rule to be included in the results.

## Key Findings

Using a minimum support of `0.01`, the Apriori algorithm identified **69 frequent itemsets**.

The subsequent negative association analysis identified **10 non-trivial negative association rules** that satisfied the minimum confidence threshold of `0.50`.

The project demonstrates how transactional grocery data can be transformed and analyzed using association rule mining to discover relationships between purchased and non-purchased items.

## Author

**Virnandri Andira**
