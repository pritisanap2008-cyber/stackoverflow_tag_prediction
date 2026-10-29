1. StackOverflow Tag Prediction

Predicts the tags of a StackOverflow question from its title and body (multi-label classification).

2. Data
- Dataset: mikex86/stackoverflow-posts (Hugging Face), read with streaming
- First 30,000 questions that have tags
- Kept the 50 most common tags, which left 23,432 questions
- Split: 80% train (18,745), 20% test (4,687)

3. Method
- Text cleaning: removed code blocks, HTML tags and links, lowercased, kept # and + so c# and c++ stay intact
- Features: TF-IDF (20,000 features, single words and word pairs)
- Model: One-vs-Rest Logistic Regression (one model per tag)
- Metrics: micro F1, macro F1, precision, recall, hamming loss

4. Results

| Metric | Threshold 0.5 | Threshold 0.3 |
|---|---|---|
| Micro F1 | 0.5889 | 0.6459 |
| Macro F1 | 0.5574 | 0.6209 |
| Precision | 0.8138 | 0.7416 |
| Recall | 0.4614 | 0.5721 |
| Hamming loss | 0.01952 | 0.01901 |

Best setting: threshold 0.3, micro F1 0.6459.

5. Limitations
- Early StackOverflow posts only, so c# and .net are very common
- Only 30,000 questions and only the top 50 tags
- Threshold chosen using the test set
- Some code can remain in the text

6.  Tools
Python, pandas, scikit-learn, Hugging Face datasets, Google Colab
