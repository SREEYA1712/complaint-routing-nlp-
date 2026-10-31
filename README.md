# Customer Complaint Classification and Routing (NLP)

Prototype for the MAAI 902 (Natural Language Processing & LLMs) NLP Solution Design assignment, University of Wollongong in Dubai.

## Purpose

Customer complaints arrive as free text and must be sent to the right team. This prototype shows the core idea: classify a complaint into one of six categories so it can be routed automatically. It trains and compares two simple classifiers and provides an interactive dashboard for testing new complaints.

It is a proof of concept supporting the design in the accompanying report, not a production system.

## How to run in Colab

1. Open the notebook in Colab: **[Colab link]** (Share > "Anyone with the link" > Viewer).
2. Choose **Runtime > Restart session and run all**.
3. The first cell installs the dependencies (equivalent to `requirements.txt`).
4. The last section launches the Gradio dashboard. Type a complaint and the predicted category and class probabilities are shown.

Note: the `gradio.live` link printed by the notebook is temporary and expires after a few days. Re-run the notebook to get a new one.

To run locally instead:

```bash
pip install -r requirements.txt
jupyter notebook
```

## Dataset

72 handwritten customer complaints, 12 for each of 6 categories. The data is small and tidy by design. It is not real customer data and contains no personal information.

Split: 57 training / 15 test (stratified).

## Method

- Text representation: TF-IDF
- Classifiers: Logistic Regression and Multinomial Naive Bayes
- Model selection: macro F1 on the held-out test set
- Interface: interactive dashboard built with Gradio

## Libraries

scikit-learn, pandas, numpy, matplotlib, seaborn, joblib, ipywidgets, gradio (see `requirements.txt`).

## Results summary

- Logistic Regression was selected on macro F1 (see the notebook for the scores).
- On six new hand-written sentences, four were routed sensibly. Two were not: a complaint about unanswered support requests and an app crash that mentioned the user's account were both sent to Account Issues.
- Predicted probabilities were low (about 20% to 31%), only slightly above the random-guess level of about 17% for six classes.

## Limitations

- Only 72 handwritten complaints and a 15-item test set, so results are not statistically firm.
- Handwritten data is cleaner and more uniform than real complaints.
- TF-IDF relies on individual keywords and misses context, which explains the misrouted examples.
- Probabilities are uncalibrated, so they should not be used as confidence scores without calibration.
- English only. No handling of Arabic, spelling errors, or mixed-language text.
- Not tested for bias across customer groups.

## Links

- Report: see the "Prototype, Repository and Demonstration" section
- Demonstration video: **[video link]**
