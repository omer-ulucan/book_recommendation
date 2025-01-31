# Book Recommendation System

A sophisticated book recommendation system built with Python that uses Natural Language Processing (NLP) and Machine Learning techniques to provide personalized book recommendations based on content similarity.

## Features

- Text preprocessing using NLTK for enhanced accuracy
- TF-IDF vectorization for feature extraction
- Cosine similarity-based recommendation generation
- Model persistence capabilities
- Memory-efficient processing using garbage collection
- Customizable number of recommendations

## Prerequisites

```bash
python >= 3.7
pandas
numpy
scikit-learn
nltk
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/book-recommender.git
cd book-recommender
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Download required NLTK data:
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
```

## Usage

1. Basic usage:

```python
from book_recommender import BookRecommender

# Load your dataset
df = pd.read_csv('path/to/your/books.csv')

# Initialize and train the recommender
recommender = BookRecommender()
recommender.fit(df)

# Get recommendations
recommendations = recommender.get_recommendations("The Hobbit")
```

2. Save and load the model:

```python
# Save the model
recommender.save_model('./ml_model/book_recommender.pkl')

# Load a saved model
loaded_recommender = BookRecommender.load_model('./ml_model/book_recommender.pkl')
```

## Dataset Requirements

Your dataset should include the following columns:
- `Title`: Book title
- `Authors`: Book author(s)
- `Description`: Book description/summary
- `Category`: Book category/genre

## Example Output

```python
recommendations = recommender.get_recommendations("The Hobbit")
# Returns:
[
    {
        'Title': 'The Lord of the Rings',
        'Author': 'J.R.R. Tolkien',
        'Category': 'Fantasy',
        'Similarity Score': 0.876
    },
    # ... more recommendations
]
```

## How It Works

1. **Text Preprocessing**:
   - Converts text to lowercase
   - Removes numbers and punctuation
   - Eliminates stop words
   - Applies lemmatization

2. **Feature Extraction**:
   - Uses TF-IDF vectorization
   - Processes title, description, and category information
   - Creates a feature matrix for similarity computation

3. **Recommendation Generation**:
   - Computes cosine similarity between books
   - Ranks similar books by similarity score
   - Returns top N recommendations

## Configuration

You can customize the following parameters:
- Number of recommendations (default: 5)
- Maximum features for TF-IDF vectorization (default: 5000)
- Text preprocessing options in the `_clean_text` method

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Acknowledgments

- NLTK for natural language processing capabilities
- scikit-learn for machine learning functionality
- pandas and numpy for data manipulation

## Future Improvements

- Add collaborative filtering
- Implement user feedback system
- Add support for multiple languages
- Enhance preprocessing techniques
- Add API endpoints for web service integration
