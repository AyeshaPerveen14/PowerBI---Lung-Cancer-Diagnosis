<img width="1132" height="656" alt="image" src="https://github.com/user-attachments/assets/6579c8f0-90c1-4bf2-8a44-c9880d30a159" />


### Behavioural and Demographic Data Analysis for Early Lung Cancer Detection

# Overview
This project presents a complete end-to-end analysis of lung cancer diagnosis using behavioural, symptomatic, and demographic data. Conducted under the context of Lung Cancer Dataset from Kaggle, the goal was to uncover key risk patterns, segment participants based on risk level, and recommend early detection strategies through interactive visual storytelling using Power BI.


### Table of Contents
  -[Project Overview](#project-overview)
  
  -[Project Objectives](#project-objectives)
  
  -[Dataset Information](#dataset-information)
  
  -[Tools & Technologies](#tools-&-technologies)
  
  -[Visualizations Used](#visualizations-used)
  
  -[Supporting Tables Created](#supporting-tables-created)
  
  -[Key Observations](#key-observations)
  
  -[Recommendations](#recommendations)


### Project Overview

This project presents an end-to-end analytical study focused on early lung cancer detection using behavioural, symptomatic, and demographic data. The analysis of Lung Cancer Diagnosis Analysis aims to uncover key risk patterns, segment participants by risk level, and provide actionable insights through interactive visual storytelling in Power BI.

The project emphasizes practical healthcare analytics, combining data preparation, modelling, visualization, and interpretation to support early diagnosis and preventive public health strategies.

### Project Objectives

  * Identify the most common symptoms among diagnosed individuals
  * Discover leading behavioural risk factors associated with lung cancer
  * Segment participants into Low, Medium, and High risk categories
  * Generate actionable insights for early detection and intervention
  * Deliver a one-page interactive Power BI dashboard with clear storytelling

### Dataset Information

  **Source:** Kaggle – Lung Cancer Dataset [ClickHere for Dataset](https://www.kaggle.com/datasets/aagambshah/lung-cancer-dataset)
  
  **Records:** 309 participants
  
  **Type:** Survey-based responses

#### Data Categories

* **Demographics**: Age, Gender
* **Behavioural Indicators:** Smoking, Alcohol Consumption, Anxiety, Peer Pressure, etc.
* **Symptoms:** Fatigue, Coughing, Chest Pain, Shortness of Breath, Swallowing Difficulty, Yellow Fingers, etc.
* **Target Variable:** Lung Cancer Diagnosis (Yes / No)

### Tools & Technologies

* **Power BI** (Data Modelling, DAX, Visualization)

* **Power Query Editor** (Data Cleaning & Preprocessing)

* **DAX Measures & Calculated Tables**

* **Git & GitHub** (Version Control & Documentation)

### Dashboard Features

**Key Performance Indicators (KPIs)**

* Percentage of participants diagnosed with lung cancer

* Average age of diagnosed participants

* Leading behavioural risk factor

* Most common symptom among diagnosed individuals

## Visualizations Used

### Visual Type:

  **Treemap	Symptom** - Prevalence among diagnosed participants

  **100% Stacked Column Chart** -	Lung cancer diagnosis by smoking and alcohol usage

  **Ribbon Chart** -	Risk level distribution (Low / Medium / High)

  **Matrix Table**-	Behavioural risk factor comparison

  **Donut Chart** -	Gender distribution of diagnosed cases

  **100% Stacked Bar** - Chart	Age group vs lung cancer diagnosis

### Key DAX Measures

**LungCancerRate** =
DIVIDE(
    CALCULATE(COUNTROWS('Lung Cancer'), 'Lung Cancer'[LUNG_CANCER] = "YES"),
    COUNTROWS('Lung Cancer')
)

**AverageAgeDiagnosed** =
CALCULATE(
    AVERAGE('Lung Cancer'[AGE]),
    'Lung Cancer'[LUNG_CANCER] = "YES"
)

**LeadingBehaviorRiskFactor** =
VAR SummaryTable =
    SUMMARIZE(
        FILTER(
            'Behavioural Breakdown',
            'Behavioural Breakdown'[Presence] = "Yes" &&
            'Behavioural Breakdown'[LUNG_CANCER] = "Yes"
        ),
        'Behavioural Breakdown'[Behaviour],
        "YesCount", COUNTROWS('Behavioural Breakdown')
    )
VAR MaxCount = MAXX(SummaryTable, [YesCount])
RETURN
    MAXX(
        FILTER(SummaryTable, [YesCount] = MaxCount),
        'Behavioural Breakdown'[Behaviour]
    )


Additional DAX measures are included in the Power BI file.

## Supporting Tables Created
### Behavioural Breakdown

  **Purpose:** Unpivoted behavioural indicators into a two-column structure (Behaviour, Presence)

  **Use Case:** Behavioural risk matrix and leading behavioural risk factor identification

### Symptom Breakdown

  **Purpose:** Consolidated multiple symptom indicators into a unified structure

  **Use Case:** Symptom prevalence treemap and identification of the most common symptom

### Substance Consumption

  **Purpose:** Isolated diagnosis outcomes based on smoking and alcohol usage

  **Use Case:** 100% stacked column analysis of substance-related diagnosis trends

## Key Observations

* **Fatigue** emerged as the most common symptom among diagnosed participants

* **Smoking and alcohol consumption** were the strongest behavioural risk factors

* Diagnosis rates were slightly higher among **males**(53.7%)

* The **High-Risk segment showed a 100% diagnosis rate**, validating the segmentation model

* The **average age of diagnosis was 63 years**, with most cases occurring between ages 51–80

* The **71–80 age group** exhibited extremely high diagnosis rates (98.04%)

* **Swallowing difficulty and yellow fingers**, though less publicized, showed strong correlation with diagnosis

* Psychosocial factors such as **anxiety and peer pressure** were reported frequently among diagnosed individuals

## Recommendations

* Prioritize lung cancer screening for adults **aged 50 and above**

* **Treat fatigue** as a primary early-warning indicator when combined with other symptoms

* Strengthen **anti-smoking and alcohol awareness** programs

* Incorporate **mental health indicators** into lung cancer risk assessments

* Implement **risk-based triage** models for early intervention

* Increase awareness of **less obvious symptoms** during clinical evaluations

* Improve **sampling balance in** future studies to enhance generalizability

* Encourage **preventive health checkups** for high-risk behavioural groups
