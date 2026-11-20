# Data

The datasets used in the paper are **not** included in this repository.

## ULB credit-card fraud dataset (public)

Download `creditcard.csv` from Kaggle and place it in this folder:

- https://www.kaggle.com/mlg-ulb/creditcardfraud

It contains 284,807 transactions with a 0.172 % fraud rate (features `Time`, `V1`–`V28`,
`Amount`, `Class`).

## Proprietary bank dataset (not shared)

`bank.xlsx` contains confidential transaction records and is **not** distributed.
The feature engineering that turns its raw fields into the eight numerical features used
by the models is documented in `../notebooks/01_preprocesamiento.ipynb`, so the same
pipeline can be reproduced on an equivalent, properly authorised dataset.
