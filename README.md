# Sentences Similarity Analyzer

## Overview

This project evaluates the similarity between two given text samples using multiple NLP transformer models. The similarity scores are then ranked using the TOPSIS (Technique for Order of Preference by Similarity to Ideal Solution) method to determine which model provides the most relevant similarity measure.

## Features

- Uses multiple transformer models for text similarity computation.
- Implements cosine similarity to measure sentence embeddings.
- Normalizes and ranks models based on similarity scores using the TOPSIS method.
- Outputs results into a CSV file (`results.csv`) containing model names and their ranking.

## Dependencies

Ensure you have the following Python libraries installed:

```sh
pip install torch transformers numpy scipy
```

## How It Works

1. **Text Similarity Computation**:

   - Uses pre-trained transformer models from Hugging Face.
   - Tokenizes the input text and obtains sentence embeddings via mean pooling.
   - Computes the cosine similarity between the embeddings of the two input texts.

2. **Models Used**:

   - BERT (`bert-base-uncased`)
   - RoBERTa (`roberta-base`)
   - Sentence-BERT (`sentence-transformers/bert-base-nli-mean-tokens`)
   - GPT-2 (`gpt2` as a proxy for GPT-3)
   - DistilBERT (`distilbert-base-uncased`)

3. **TOPSIS Ranking**:

   - Normalizes similarity scores.
   - Weighs and computes the ideal and anti-ideal solutions.
   - Ranks models based on their proximity to the ideal solution.

## Usage

Run the script as follows:

```sh
python script.py
```

This will generate `results.csv` containing the ranked models based on similarity scores.

## Output

The output CSV file (`results.csv`) has the following structure:

```
DistilBERT	1
RoBERTa	2
Sentence-BERT	3
BERT	4
GPT-2	5
```

Where Rank 1 indicates the best-performing model for the given input texts.

## Customization

- Modify `text1` and `text2` variables to test different text samples.
- Add more transformer models by extending the `model_ids` dictionary.
- Adjust `weights` if you have multiple criteria for ranking.

## Notes

- GPT-2 is not optimized for sentence embeddings, so its results may not be as accurate.
- Models may require additional fine-tuning for domain-specific applications.

## License

This project is open-source and available for modification and distribution.
