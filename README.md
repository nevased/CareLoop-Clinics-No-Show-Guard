
# Healthcare Appointment No-Show Prediction and Follow-up Analysis

**GitHub Repository:** ADD_YOUR_PUBLIC_GITHUB_REPOSITORY_LINK_HERE

## Project Summary

- **Part 1 – Data cleaning:** https://github.com/nevased/CareLoop-Clinics-No-Show-Guard/blob/main/01_ingest_clean.ipynb.
- **Part 2 – SQL analysis:** [ADD YOUR ACTUAL SQL FINDING AND NUMBER HERE].
- **Part 3 – Machine learning:** Logistic Regression achieved a test ROC-AUC of 0.7889; the selected classification threshold was 0.35.
- **Part 4 – GenAI analysis:** Analysed 10 follow-up notes; 5 records (50.00%) had no reminder recorded.

## Business Recommendation

The appointment dataset contained 990 records, with an overall no-show rate of approximately 22%. The Logistic Regression model was selected because it achieved a cross-validation ROC-AUC of 0.7737, compared with 0.7673 for the tuned Random Forest. On the test set, Logistic Regression achieved a ROC-AUC of 0.7889. A threshold of 0.35 was selected because its out-of-fold F1 score was 0.4892, compared with 0.3471 at the default threshold of 0.50. At the selected threshold, test precision and recall were both 0.5714, and 49 appointments were flagged. The clinic should use these risk scores to prioritise follow-up calls and reminders, while treating the GenAI analysis of 10 notes as an initial illustration rather than a definitive explanation of clinic-wide no-shows. The clinic should monitor call capacity and model performance before using the threshold operationally.

## Selected Model and Threshold

**Selected model:** Logistic Regression

**Reason for selection:** Logistic Regression achieved the highest cross-validation ROC-AUC among the compared models.

| Metric | Result |
|---|---:|
| Logistic Regression CV ROC-AUC | 0.7737 |
| Tuned Random Forest CV ROC-AUC | 0.7673 |
| Test ROC-AUC | 0.7889 |
| Selected threshold | 0.35 |
| Test precision at 0.35 | 0.5714 |
| Test recall at 0.35 | 0.5714 |
| Appointments flagged on test set | 49 |
| Out-of-fold F1 at threshold 0.35 | 0.4892 |
| Out-of-fold F1 at threshold 0.50 | 0.3471 |

The threshold of 0.35 improves the balance between precision and recall compared with the default 0.50 threshold. The clinic should adjust it according to the number of follow-up calls it can handle.

## Part 4: Root Cause and Reminder Analysis

The following table compares the GenAI-classified root causes with whether a reminder was recorded.

| root_cause   |   No |   All |
|:-------------|-----:|------:|
| other        |    1 |     1 |
| All          |    1 |     1 |

## Business Interpretation

The cross-tabulation helps identify whether particular reported reasons for missed appointments appear alongside missing reminders. These are descriptive associations, not proof that reminders caused or prevented no-shows. The clinic should investigate the patterns and test targeted interventions.

## Limitations

1. Only 10 follow-up notes were analysed. They are an illustration and cannot establish the real reasons for no-shows across the entire clinic.
2. The data split was random rather than past-to-future, so the evaluation may not reflect performance on future appointments.
3. The data are observational, so associations between reminders, patient characteristics and no-shows do not prove cause and effect.

## Project Files

- `appointments_clean.csv`
- `notes_analysed.csv`
- `merged_notes_appointments.csv`
- `root_cause_reminder_crosstab.csv`
- `appointments_clean.sql`
- Your notebook(s) containing the data cleaning, SQL, machine learning and GenAI analysis.

## Security

No API key or other secret credentials should be included in this public repository.
