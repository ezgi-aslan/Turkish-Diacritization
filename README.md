# Turkish Diacritization 

This project focuses on restoring missing diacritics in Turkish text using deep learning techniques. Diacritics are crucial in Turkish for accurate understanding, disambiguation, and grammatical clarity. In informal text, especially online, they are often omitted—leading to ambiguity and reduced performance in natural language processing tasks.

## 📌 Project Summary

We developed and evaluated multiple deep learning architectures to automatically add missing diacritics to Turkish text. The final model leverages **Bidirectional GRUs**, achieving high accuracy and robustness.

## 📚 Dataset

The training data is a combination of:

- **Competition dataset**: 52,362 correctly written Turkish sentences.
- **YTÜ Kemik NLP Dataset** from [Kaggle](https://www.kaggle.com/datasets/oktayozturk010/42000-news-text-in-13-classes): 42,000 Turkish news sentences.

Test data consists of ASCII-form Turkish sentences without diacritics.

| Metric              | Train Set        | Test Set         |
|---------------------|------------------|------------------|
| Max Word Count      | 3997             | 149              |
| Avg Word Count      | 18.81            | 14.69            |
| Total Word Count    | 1,773,519        | 16,992           |
| Max Char Count      | 27,303           | 1,064            |

## 🔍 Preprocessing Steps

1. **Diacritic Removal**: ASCII-fied input used for training, original used as target.
2.  **Character-Level Tokenization** for fine-grained learning.
3.  **Vocabulary Indexing** and **Right Padding** for uniform input size.

## 🧠 Model Architectures Explored

Several architectures were implemented and compared:

1. **Embedding + LSTM + Dense**
2. **Embedding + Dropout + Dense + BiLSTM**
3. **Embedding + BiLSTM + Dropout + LSTM + Dropout + Dense**
4. **Final Architecture**: Embedding + **Bidirectional GRU** + Dropout + Dense (Softmax)

> The final model showed the best results with an accuracy of **0.9868** on the validation set and **0.877** on the test set.

## 🏗 Final Model Details

- **Embedding Layer** (dim=100)
- **Bidirectional GRU Layer**
- **Dropout** (rate=0.2)
- **Dense Output Layer** with softmax activation

Frameworks used: **TensorFlow**, **Keras**

## 📊 Performance Comparison

| Model Architecture                              | Train Acc. | Val Acc. | Test Score |
|--------------------------------------------------|------------|----------|------------|
| Embedding + LSTM + Dense                         | 0.963      | 0.952    | 0.741      |
| Embedding + Dropout + Dense + BiLSTM             | 0.989      | 0.971    | 0.858      |
| Embedding + BiLSTM + Dropout + LSTM + Dropout    | 0.988      | 0.981    | 0.851      |
| **Final (Embedding + BiGRU + Dropout + Dense)**  | **0.990**  | **0.987**| **0.877**  |

An additional experiment removing a previous lowercasing step achieved **0.941** accuracy, showing the importance of preprocessing decisions.

## 📌 References

- Köksal et al. (2022): Context-aware sequence to sequence Turkish diacritization.
- Adalı & Eryiğit (2014): Diacritic restoration for Turkish social media texts.
- Özer et al. (2018): Word2Vec-based model for Turkish tweets.
- Moumen et al. (2018): GRU-based Arabic diacritization.
- Yıldırım & Atık (2013): Turkish news dataset.

## 👥 Contributors

- **Beyza Nur Keskin** – [https://github.com/beyzanurbozkurt](https://github.com/beyzanurbozkurt)
- **Ezgi Aslan** – [https://github.com/ezgi-aslan](https://github.com/ezgi-aslan)

---

> This work contributes to the growing body of NLP tools tailored for Turkish and highlights the power of deep learning in language restoration tasks.