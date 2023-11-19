# Breast-Cancer-Survival-Prediction
## Time-related survival prediction in molecular subtypes of breast cancer using time-to-event deep-learning-based models.

We used time-to-event survival prediction models including `Nnet-survival`, `DeepHit`, `Cox-Time` and `MLTR` from [Pycox](https://github.com/havakv/pycox) package to predict breast cancer survival data. we developed the models with hyperparameter grid search and by labaling breast cancer data in four molecular subtypes, the survival probabilities were predicted in each subtype. then we figure the Kaplan-Meyer curve for each subtype in 10 time intervals to analyze the patterns of survival probabilities in each subtype.

## Background: 
> Breast cancer (BC) survival prediction can be a helpful tool for identifying important factors, selecting effective treatment, and reducing mortality rates. This study aims to predict the survival probability of BC patients in different molecular subtypes defined by estrogen receptor (ER), progesterone receptor (PR), and human epidermal growth factor receptor 2 (HER2) over 30 years of follow-up.

## Materials and Methods: 
> This is a retrospective cohort of 3580 patients diagnosed with invasive BC from 1991 to 2021 in the Cancer Research Center of Shahid Beheshti University of Medical Science. The dataset contained 20 predictor variables and two dependent variables, which referred to the survival status of patients and the time patients survived from diagnosis. The feature selection was conducted using the random forest algorithm to determine the significant prognostic factors. Time-to-event deep-learning-based models, including Nnet-survival, DeepHit, DeepSurve, NMLTR, and Cox-time, were developed by a grid search first with total variables and second with the most important variables resulting from feature selection. C-index and IBS were used as the performance metrics to find the best-performing model. The dataset was clustered based on the molecular receptor status of patients (i.e., luminal A, luminal B, HER2-enriched, and triple-negative), and the best-performing prediction model was used to predict the survival probability of patients in each molecular subtype.

## Results: 
> The random forest method identified tumor state, age at diagnosis, and lymph node status as the best subset of variables. All models yielded very close performance, with Nnet-survival (C-index=0.77, IBS=0.13) slightly higher using both the total and the three most important variables. Luminal A indicated the highest predicted BC survival probabilities among the four subtypes, whereas triple-negative and HER2-enriched showed the lowest predicted survival probabilities over time. The luminal B subtype followed a similar trend as luminal A for the first five years, after which the predicted survival probability decreased steadily in 10- and 15 years.

## Conclusion: 
> The results of this study can help healthcare providers determine patients' survival probability and prevent unnecessary medical interventions for high-risk patients based on molecular receptor status, especially for HER2-positive patients. Future clinical trials of BC treatments should investigate the response of different molecular subtypes to treatment.

## Installing Requirements

```shell
pip install -r requirements.txt
```
Use notebooks:
- [k-fold-Nnet-survival-best.ipynb](https://github.com/MehradAria/Breast-Cancer-Survival-Prediction/blob/main/k-fold-Nnet-survival-best.ipynb)
- [k-fold-cox-time-survival-best.ipynb](https://github.com/MehradAria/Breast-Cancer-Survival-Prediction/blob/main/k-fold-cox-time-survival-best.ipynb)
- [k-fold-deep-hit-single-survival-best.ipynb](https://github.com/MehradAria/Breast-Cancer-Survival-Prediction/blob/main/k-fold-deep-hit-single-survival-best.ipynb)
- [k-fold-mltr-survival-best.ipynb](https://github.com/MehradAria/Breast-Cancer-Survival-Prediction/blob/main/k-fold-mltr-survival-best.ipynb)

---
### Note
Setting  `n_jobs` to more than one is not possible due to a bug in pycox library.
We mentioned the bug in the following issue: ValueError: Need time to have the same type as self.durations and proposed a solution to the problem in the following pull request: Addressing issue #149 -> change is not to !=.

If your version of pycox is higher that `0.2.3`, and the following line in https://github.com/havakv/pycox/blob/master/pycox/preprocessing/discretization.py#L155 is as follows: `if duration.dtype != self.durations.dtype:` you can safely increase the value of `n_jobs`.

If the mentioned line is as follows:
```shell
if duration.dtype is not self.durations.dtype:
```
You should set `n_jobs` to 1, or you can open the file `pycox/preprocessing/discretization.py` and change the line to `if duration.dtype != self.durations.dtype:` and increase the value of `n_jobs`

---
### Paper / Data availability:

- Paper (Open Access): [Time-related survival prediction in molecular subtypes of breast cancer using time-to-event deep-learning-based models](https://doi.org/10.3389/fonc.2023.1147604)

- Due to the policies and guidelines of the Cancer Research Center of Shahid Beheshti University of Medical Science, data is not allowed for publication. for data access requests please visit https://crc.sbmu.ac.ir/ 

---
### Condition and terms to use any sources of this project (Codes, Datasets, etc.):

1) Please cite the following paper:
```
Zarean Shahraki, S., Azizmohammad Looha, M., Aria, M., Akbari, A., Emami, H., Asadi, F., & Akbari, M. E.
Time-related survival prediction in molecular subtypes of breast cancer using time-to-event deep-learning-based models.
Frontiers in Oncology, 13, 2292.
doi: 10.3389/fonc.2023.1147604
```

2) Please do not distribute the database or source codes to others without author authorization.
Authors’ Email: `profmeakbari[at]gmail.com` (M.E. Akbari).
