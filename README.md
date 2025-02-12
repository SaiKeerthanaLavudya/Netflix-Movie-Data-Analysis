# Netflix-Movie-Data-Analysis
This project focuses on analyzing Netflix movie data to uncover insights about movie genres, popularity, and production trends. The dataset explores genre distribution, viewer preferences, and the relationship between genres and popularity. The analysis reveals how genres like Drama dominate Netflix's library and how certain films have garnered exceptional popularity.
# Key Insights

# Most Frequent Genre:

- The Drama genre is the most common, appearing in over 14% of the dataset across 19 genres.

# Genre with Highest Votes:

Drama also holds the highest audience engagement, contributing to 18.5% of the most-voted movies, with 25.5% (6,520 movies) of the dataset being highly voted films.

# Most Popular Movie:

Spider-Man: No Way Home leads in popularity with genres Adventure and Science Fiction.

# Least Popular Movie:

The United States Thread ranks the lowest in popularity and belongs to the genres Music, Drama, War, Science Fiction, and History.

# Year with Most Film Releases:

The year 2020 had the highest number of movies released on Netflix.

# Technologies Used

- Python

- Pandas (for data manipulation)

- Matplotlib & Seaborn (for data visualization)

- Jupyter Notebook (for interactive analysis)
 # Installation 
 1. clone the Repository
    git clone <https://github.com/RamcharanSinghRamavath/Netflix-Movie-Data-Analysis/>

  2. Install required libraries:
     pip install pandas matplotlib seaborn jupyter

 3.  Run the Jupyter Notebook:
     jupyter notebook
# Code Workflow

# Load the dataset
df = pd.read_csv('netflix_movies.csv')

# Data Cleaning
# Splitting and exploding the 'Genre' column
df['Genre'] = df['Genre'].fillna('').str.split(',')
df = df.explode('Genre')
df['Genre'] = df['Genre'].str.strip()
df = df[df['Genre'] != '']

# Most Frequent Genre
most_frequent_genre = df['Genre'].value_counts().idxmax()
print(f"Most Frequent Genre: {most_frequent_genre}")

# Movie with Highest Popularity
most_popular_movie = df.loc[df['popularity'].idxmax()]
print(f"Most Popular Movie: {most_popular_movie['title']}")

# Movie with Lowest Popularity
least_popular_movie = df.loc[df['popularity'].idxmin()]
print(f"Least Popular Movie: {least_popular_movie['title']}")

# Year with Most Movie Releases
yearly_release = df['release_year'].value_counts().idxmax()
print(f"Year with Most Releases: {yearly_release}")

# Visualization of Genre Distribution
plt.figure(figsize=(10,6))
sns.countplot(y='Genre', data=df, order=df['Genre'].value_counts().index)
plt.title('Distribution of Movie Genres')
plt.xlabel('Count')
plt.ylabel('Genre')
plt.show()

## Future Improvements:
- Include TV shows in the analysis.

- Predict future genre trends using machine learning.

- Analyze user ratings and reviews for deeper insights.

# Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

# License

This project is licensed under the MIT License.


