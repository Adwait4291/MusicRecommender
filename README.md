# Music Recommender App

## Overview

This application helps you discover new music based on lyrical similarity. Simply choose a song you enjoy from the list, and the app will recommend other songs that have similar lyrics. It uses natural language processing techniques (TF-IDF and Cosine Similarity) to compare song texts and find matches.

## Technologies Used

* **Python:** The core language for the project.
* **Streamlit:** Used to create the interactive web interface.
* **Pandas:** For handling and managing the song data.
* **Scikit-learn:** Provides tools for TF-IDF vectorization and similarity calculations.
* **NLTK:** Used for essential text processing steps like tokenization and removing common words (stopwords).
* **Joblib:** For efficiently saving and loading the processed data needed for recommendations.

## How It Works

The process involves two main parts:

1.  **Preprocessing (Offline):** A script (`preprocess.py`) first analyzes the lyrics from a dataset of songs. It cleans the text, converts lyrics into numerical vectors (TF-IDF), calculates how similar each song is to every other song based on these vectors (Cosine Similarity), and saves this information.
2.  **Recommendation App (Online):** The Streamlit app (`app.py`) loads the pre-calculated similarity information. When you select a song, it quickly looks up the most similar songs based on the saved data and displays them to you.

## Setup and Usage

1.  **Get the Code:**
    ```bash
    git clone <your-repository-url>
    cd <repository-directory>
    ```

2.  **Install Libraries:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Download Language Data:**
    If you haven't used NLTK before, download necessary data:
    ```python
    # Run this in a Python interpreter
    import nltk
    nltk.download('punkt')
    nltk.download('stopwords')
    ```

4.  **Get the Song Data:**
    * Download the `spotify_millsongdata.csv` dataset (available on [Kaggle](https://www.kaggle.com/datasets/notshrirang/spotify-million-song-dataset/data)).
    * Place this CSV file in the main project folder.

5.  **Prepare for Recommendations:**
    Run the preprocessing script once. This creates files needed by the app.
    ```bash
    python preprocess.py
    ```

6.  **Launch the App:**
    ```bash
    streamlit run app.py
    ```
    Open the URL shown in your terminal (usually `http://localhost:8501`) in your browser. Select a song and click the button to get recommendations!

## Example Usage

Inside the app:

1.  Find the dropdown menu labeled "Type or select a song from the list:".
2.  Select a song you like (e.g., "Bohemian Rhapsody").
3.  Click the "🚀 Find Similar Songs!" button.
4.  The app will display a table with recommended songs and their artists. If the selected song isn't found in the processed data, it will show a message indicating that.

## Future Ideas

* Add options to filter recommendations by artist or genre.
* Explore using more advanced NLP models for similarity.
* Allow users to input custom lyrics to find similar songs.

## License

This project uses the MIT License. Check the `LICENSE` file if included.

