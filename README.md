# Language Translator

## Introduction:
Language Translation is the intricate process of seamlessly converting words or text from one language to another, ensuring cultural and linguistic nuances are accurately preserved. This project employs a Recurrent Neural Network utilizing LSTM layers to accomplish translation tasks, specifically transforming sentences from English to French.

## Dataset:
The project centers on a parallel English-French dataset, a meticulously curated corpus of aligned English and French words and sentences spanning from 1996 to 2011. Comprising around 150,000 English-French parallel sentences, due to memory constraints, the model was trained on a subset of less than 10% of the data, amounting to 10,000 sentences.

## Proposed Architecture:
- Utilizing a many-to-many model of seq2seq modeling to generate output text.
- Employing an encoder-decoder architecture to facilitate translation.
- Implementing Teacher Forcing technique, where the previous output serves as input to predict the next step, crucial for maintaining coherence.

## Teacher Forcing Example:
For instance, for the French sentence "Je déteste repasser," which translates to "I hate to iron" in English, the process involves adding start and end tokens to signify the beginning and conclusion of the sentence. This enables the model to understand sentence completion.

## Procedure:
1. **Encoder LSTM outputs:** Retaining only the state outputs of the encoder LSTM layer, as they encapsulate all pertinent information about the input data.
2. These encoder LSTM states initialize the decoder LSTM, with the [start] token serving as the initial word for teacher forcing.
3. The decoder LSTM output passes through a Dense layer to predict subsequent words.
  
## Workflow:
1. **Encoder side:** Input → Encoder LSTM → Encoder states
2. **Decoder side:**
   - Encoder states + [start] → Decoder LSTM → Word + Decoder states
   - Decoder states + Word → Decoder LSTM → Word2 + Decoder states 2
   - Word2 + Decoder states 2 → Decoder LSTM → Word3 + Decoder states 3 (continues until [end] token is predicted)

## Conclusion:
While the model's performance in translating sentences fell short, displaying repetitions of certain words, there exists potential for improvement through hyperparameter tuning. Furthermore, the limited training data hindered the model's ability to grasp word relations fully. Training the model on the entire dataset holds promise for significantly enhancing its accuracy beyond the observed 43%.
