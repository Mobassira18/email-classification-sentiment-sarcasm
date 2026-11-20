# Email Classification with Sentiment and Sarcasm Detection

A Python project that finds spam emails, measures the mood of legitimate emails, and looks for sarcasm. It also compares my own model with OpenAI GPT-3.5.

## What the project does

1. **Spam detection.** A Complement Naive Bayes model, with TF-IDF text features, sorts emails into spam and legitimate (ham). Duplicate emails were removed first, and 20% of the data was kept for testing.
2. **Sentiment analysis.** A keyword method marks each legitimate email as positive, negative or neutral.
3. **Sarcasm detection.** A rule-based method looks for signs of sarcasm, such as ironic phrases, quotation marks, capital letters and repeated punctuation. Sarcastic emails that were marked positive are changed to negative.
4. **Model comparison.** My model and OpenAI GPT-3.5 classify the same 6 legitimate emails. I compare accuracy, false positives, confidence and speed.

## Results

**Spam detection (test set of 1,032 emails)**

| Measure | Result |
|---|---|
| Accuracy | 95.5% |
| ROC AUC | 0.989 |
| Spam recall | 0.96 |
| Spam precision | 0.77 |
| Legitimate emails marked as spam | 40 |
| Spam emails missed | 6 |

**Sentiment of 4,516 legitimate emails**

| Sentiment | Before sarcasm check | After sarcasm check |
|---|---|---|
| Positive | 786 | 773 |
| Neutral | 3,117 | 3,107 |
| Negative | 613 | 636 |

The sarcasm rules marked 25 emails (0.55%) as sarcastic and changed the sentiment of 23 of them.

**My model compared with OpenAI GPT-3.5 (6 legitimate emails)**

| Measure | Naive Bayes | OpenAI GPT-3.5 |
|---|---|---|
| Correct answers | 6 of 6 | 6 of 6 |
| False positives | 0 | 0 |
| Average confidence | 88.1% | 94.2% |
| Average time per email | 0.0038 seconds | 0.6978 seconds |

My model was about 182 times faster.

## Files

| File | Description |
|---|---|
| `Ai_project.ipynb` | The full notebook with the code and explanations |
| `mail_data.csv` | The email dataset (5,572 emails, labelled spam or ham) |
| `email_sentiment_with_sarcasm.csv` | Sentiment and sarcasm results for each legitimate email |
| `ham_classification_comparison.csv` | Results of the comparison with GPT-3.5 |

## How to run it

1. Install the libraries:
   `pip install pandas numpy scikit-learn matplotlib seaborn openai==0.28`
2. Open `Ai_project.ipynb` in Jupyter Notebook, JupyterLab or VS Code.
3. Run the cells from top to bottom.
4. Only the last part (the comparison with GPT-3.5) needs an OpenAI key. Save your own key in a setting named `OPENAI_API_KEY` on your computer. Never write the key inside the notebook.

## Limits of this project

- The comparison with GPT-3.5 uses only 6 emails, and all of them are legitimate. It does not test spam detection, so it shows a small example, not a full test.
- The sentiment and sarcasm methods are simple word rules. They can make mistakes, and some friendly messages may be marked as sarcastic. I did not measure their accuracy with labelled examples.
- The spam model has lower precision for spam (0.77), which means it sometimes marks a legitimate email as spam.

## Tools used

Python, pandas, NumPy, scikit-learn, Matplotlib, Seaborn, OpenAI API

## Author

Mobassira Nasin, Data Analyst Intern, Hamilton, New Zealand
