notepad README.md

\# Medical Insurance Charges Prediction



Predicting a customer's \*\*annual medical charges\*\* from age, sex, BMI, number of children, smoking status and region, using linear regression. The notebook starts from the basic idea of fitting a line and builds up to a model with categorical features, scaling and a train/test split.



\## Dataset



1,338 customers and 7 columns: `age`, `sex`, `bmi`, `children`, `smoker`, `region` and the target `charges`. The notebook downloads it automatically in its first cells, so you need an internet connection the first time you run it.



\## What the notebook covers



| Part | Topics |

|---|---|

| Exploratory analysis | Distributions of age, BMI and charges; charges by smoker, sex and region; scatter plots (Plotly) |

| Correlation | Pearson correlation, correlation vs causation |

| Linear regression from first principles | Line equation, parameters `w` and `b`, RMSE loss, optimizers (OLS vs gradient descent) |

| Scikit-learn | `LinearRegression`, `SGDRegressor`, single and multiple features |

| Categorical features | Binary encoding, one-hot encoding |

| Improving the model | Separate models for smokers and non-smokers, feature scaling, comparing feature weights |

| Evaluation | Train/test split, training vs test loss |



\## Key findings



\- \*\*Smoking status is the strongest driver of charges.\*\* Its correlation with charges is about 0.79, versus about 0.30 for age and 0.20 for BMI.

\- Smokers pay nearly \*\*4× more\*\* on average than non-smokers.

\- For smokers, charges rise sharply once BMI exceeds 30. For non-smokers, BMI has little effect.

\- After scaling, the most important features are \*\*smoker, age, then BMI\*\*.



\## Results



RMSE on the training data (lower is better):



| Model | RMSE ($) |

|---|---|

| Non-smokers, age only | 4,662 |

| Non-smokers, age + BMI + children | 4,608 |

| All customers, age + BMI + children | 11,355 |

| All customers, + smoker | 6,056 |

| All customers, all features (incl. sex and region) | 6,042 |

| Separate models for smokers and non-smokers | 4,856 |



Adding the categorical `smoker` feature cut the error by almost half (11,355 to 6,056). A model that fits smokers and non-smokers separately beat the single model that includes smoker status as a feature (4,856 vs 6,042).



\## Run it



```bash

pip install -r requirements.txt

jupyter notebook MedExp\_Pred.ipynb

```



\*\*Note:\*\* the Plotly charts are interactive, and GitHub's notebook preview often doesn't display them. Open the notebook in Jupyter (or through nbviewer) to see them.



\## Credits



This project follows the structure of Jovian's \*Machine Learning with Python: Zero to GBMs\* linear regression lesson. The dataset is loaded from Jovian's `opendatasets` repository.



