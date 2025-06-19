# Yelp Sentiment Classification Using LSTM

## Summary

This project develops a neural network to classify the sentiment of Yelp reviews as positive or negative.

**Research Question**:  
Can the sentiment of reviews be predicted using a neural network?

A labeled dataset of 1,000 Yelp reviews was preprocessed and used to train an LSTM-based binary classifier. The model aims to help businesses identify and understand customer feedback patterns through automated sentiment analysis.

## Tools Used

- Python
- pandas, numpy, seaborn, matplotlib
- nltk, contractions, unicodedata, regex
- TensorFlow and Keras (Embedding, LSTM, Sequential model)
- scikit-learn (train_test_split, accuracy_score, f1_score)

## Preprocessing

- Removed duplicates and non-ASCII characters
- Tokenized and lemmatized text, preserving negations
- Converted tokens to sequences using Keras Tokenizer
- Used 95th percentile review length (12 words) as max sequence length for padding
- Split data into training (70%), validation (15%), and test (15%) sets

## Modeling

- Built LSTM models with various combinations of `dropout` and `recurrent_dropout`
- Best model:  
  - Dropout = 0.2  
  - Recurrent Dropout = 0.2  
  - Embedding dimension = 65  
  - LSTM units = 64
- Early stopping used to halt training after 7 epochs (best epoch = 4)
- Final model layers:
  - Embedding → LSTM → Dense (sigmoid)

## Results

- **Test Accuracy**: 0.8523  
- **Test F1 Score**: 0.8451  
- **Best Epoch**: 4  
- **Validation Loss at Best Epoch**: 0.6071  
- **Training Loss at Best Epoch**: 0.2075

The model demonstrated strong generalization and balanced precision/recall.

## Notes

- Review lengths, vocabulary size, and sequence padding were all empirically justified
- Preprocessing emphasized preserving negations for accurate sentiment interpretation
- Deployment of this model could support real-time sentiment monitoring in customer feedback systems
