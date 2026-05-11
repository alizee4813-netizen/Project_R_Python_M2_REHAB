# R and Python Project – Master’s Internship

# Plantar block and early gait stability after hallux valgus surgery

## 1. Scientific problem

### 1.1. Context

Hallux valgus surgery is more and more done in an outpatient setting and follows ERAS (Enhanced Recovery After Surgery) protocols. In this context, early walking is very important because it helps patients become independent again and reduces complications linked to immobility.

Peripheral nerve blocks are often used to improve pain after surgery. However, depending on how they spread, some techniques can affect sensation or motor function, which may slow down walking recovery. In particular, a loss of foot sensitivity can affect weight-bearing and gait stability.

The **plantar block** is a locoregional anesthesia technique that targets the sensory nerves of the foot. By preserving heel sensitivity and motor function, it may allow patients to walk early without affecting stability.

The question is: does the plantar block allow early walking without affecting gait stability?

---

### 1.2. Aim

The aim of this project is to compare a group with a plantar block and a control group, in order to evaluate the impact of this technique on gait stability after hallux valgus surgery.

The analysis is based on one main variable: the **mean double support time**, used as an indicator of stability.

---

### 1.3. Method

Gait data were collected using the **GAITERITE** system. Two datasets were used:

- one with gait parameters : `GAITERITE.csv`
- one with randomization data : `RANDO.csv`

These datasets were merged and cleaned using Python, then analyzed using R.

---

### 1.4. Participants

The dataset includes patients who had hallux valgus surgery.

Patients were divided into two groups:

- plantar block group  
- control group  

---

### 1.5. Outcome measure

The main variable is the **mean double support time**.

Double support is the phase of walking when both feet are on the ground. It is commonly used as an indicator of stability.

It is calculated as the average of the left and right double support times.

---

## 2. Python project

### 2.1. Aim

The objective of the Python part is to prepare a clean dataset for analysis in R.

Python was used to process the raw data. First, I imported the two datasets (`GAITERITE` and `RANDO`), checked the column names, and corrected differences in patient IDs to be able to merge the datasets.

Then, I filtered the data by keeping only the rows marked as valid (`COMMENT = "VALIDE"`), in order to work with reliable data only.

I also converted the left and right double support variables from text to numeric format so that I could use them for calculations.

Then, I created the main variable of the study, the mean double support time (`DoubleSupport_mean`), by calculating the average of the left (`DoubleSupport_G`) and right (`DoubleSupport_D`) values.

Finally, I simplified the dataset by keeping only the useful variables (patient ID, group, surgical side and double support variables), and exported the final dataset (`results.csv`), which was used in R.

---

### 2.2. Data organization

#### 2.2.1. GAITERITE data

Main variables used:

- `NumPAT`: patient ID  
- `CoteChir`: surgical side (L = left, R = right)  
- `DoubleSupport_G`: left double support time  
- `DoubleSupport_D`: right double support time  
- `COMMENT`: data validity  

Only rows marked as **VALIDE** were kept.

---

#### 2.2.2. Randomization data

Variables:

- `Numpat`: patient ID  
- `RANDOMISATION`: group  

This variable indicates the group of each patient:

- 1: experimental group (plantar block)  
- 2: control group  

This variable is important because it allows comparison between groups.

---

### 2.3. Script organization

The Python script includes:

- data import  
- cleaning and filtering  
- merging datasets  
- creation of `DoubleSupport_mean`  
- export of `results.csv`  

Variables kept:

- `NumPAT`  
- `RANDOMISATION`  
- `CoteChir`  
- `DoubleSupport_mean`  

---

## 3. RStudio Project

### 3.1. Aim

The objective of the R part is to analyze the mean double support time in order to compare gait stability between the two groups.

R was used for statistical analysis because it is well adapted for descriptive statistics, visualization and effect size calculation.

---

### 3.2. Data organization

File: `results.csv`

Variables:

- `NumPAT` : patient ID  
- `RANDOMISATION` : group (1 = plantar block, 2 = control)  
- `CoteChir` : surgical side  
- `DoubleSupport_G` : left double support time  
- `DoubleSupport_D` : right double support time  
- `DoubleSupport_mean` : mean double support time  
---

### 3.3. Script organization
``

#### 3.3.1. Descriptive analysis

- Aim: describe mean double support time by group  
- Input: `results.csv`  
- Output: mean, standard deviation, sample size  

---

#### 3.3.2. Visualization

- Aim: visualize data distribution  
- Input: `results.csv`  
- Output: boxplot  

---

#### 3.3.3. Effect size

- Aim: quantify difference between groups  
- Input: `results.csv`  
- Output: Cohen’s d  

---

### 3.4. Conclusion

The analysis of mean double support time shows a difference between the plantar block group and the control group.

The effect size is large (Cohen’s d > 0.8), which means that the difference between groups is important.

The plantar block group shows lower values of double support time, suggesting a more dynamic gait. The control group shows higher and more variable values.

These results suggest that the plantar block does not negatively affect gait stability. They also support the idea that preserving sensation and motor function helps patients recover walking more easily.

The mean double support time seems to be a good indicator to evaluate gait stability after surgery and could be useful for patient follow-up.

---

## 4. References


Herteleer, M., Choquet, O., Swisser, F., Bernard, N., Gasc, A., Canovas, F., Dagneaux, L., Bringuier, S., & Capdevila, X. (2024). *Plantar compartment block for hallux valgus surgery: A proof-of-concept anatomic and clinical study*. Regional Anesthesia and Pain Medicine. https://doi.org/10.1136/rapm-2023-105246

Swisser, F., Choquet, O., Brethe, Y., et al. (2024). *Plantar compartment block improves enhanced recovery after hallux valgus surgery: A randomized comparative double-blind study*. Anesthesiology. https://pubmed.ncbi.nlm.nih.gov/39102486/

Korwin-Kochanowska, K., et al. (2020). *PROSPECT guideline for hallux valgus repair surgery: A systematic review and procedure-specific postoperative pain management recommendations*. Regional Anesthesia and Pain Medicine, 45(9), 702–708. https://rapm.bmj.com/content/45/9/702

Mazzotti, A., et al. (2024). *Hallux valgus plantar pressure distribution before and after surgery*. Journal of Clinical Medicine, 13(6). https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10970807/

Wust, M., et al. (2025). *Pain management after hallux valgus repair surgery*. Journal of Orthopaedic Surgery and Research. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC12700695/
