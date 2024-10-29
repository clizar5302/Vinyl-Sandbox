# Music Recommendation App

A Python application that recommends music albums based on user preferences and activities using the Discogs API. The app fetches the user's album collection, categorizes it by genre, and suggests albums based on the desired vibe and activity. The application also retrieves album cover art and utilizes TensorFlow for image classification.

## Features

- **Authenticate with Discogs**: Connect to your Discogs account to access your album collection.
- **Fetch Collection by Genre**: Retrieve albums organized by genre without duplicates.
- **Music Recommendations**: Suggest albums based on user-specified activities and vibes.
- **Album Cover Art Retrieval**: Fetch and display album cover art.
- **Image Classification**: Classify album art using a pre-trained TensorFlow model.

## Libraries Required

To run this application, you'll need the following libraries:

```bash
pip install discogs-client
pip install tensorflow
pip install colorthief opencv-python numpy
pip install webcolors
```

## Configuration

Before running the application, you need to set up your Discogs credentials. Create a file named `config.py` in the same directory and add the following:

```python
CONSUMER_KEY = 'your_consumer_key'
CONSUMER_SECRET = 'your_consumer_secret'
```

Replace `'your_consumer_key'` and `'your_consumer_secret'` with your actual Discogs API credentials.

## Usage

1. **Authenticate with Discogs**:
   Call the `authenticate_discogs()` function to authorize the app and retrieve the access token.

   ```python
   client = authenticate_discogs()
   ```

2. **Fetch and Display Collection**:
   Use the `get_collection_by_genre(client)` function to fetch and print your album collection organized by genre.

   ```python
   if client:
       collection_dict = get_collection_by_genre(client, print_collection=True)
   ```

3. **Generate Music Recommendations**:
   Call the `music_recommendation(client)` function to get album recommendations based on the specified activity and vibe.

   ```python
   music_recommendation(client)
   ```

4. **Fetch Album Cover Art**:
   Use the `get_album_cover(album_title, client)` function to retrieve the cover art for a specific album.

   ```python
   album_title = input("Enter the album title: ")
   get_album_cover(album_title, client)
   ```

5. **Classify Album Cover Art**:
   The application uses TensorFlow to classify album art. Ensure you have a stable internet connection to fetch and preprocess the image.

## Example Output

Upon running the `music_recommendation(client)` function, the application will prompt the user for input:

```
Welcome to the Music Recommendation Assistant!
Is this for a group event (g) or a solo/intimate session (s)? g
Choose group activity: Social Gathering, Game Night, Cooking, Creative Activities: game night
Describe the vibe you're aiming for: relaxed

For your g event (Game night) with a 'relaxed' vibe, we recommend:
Album: Cigarettes After Sex by Cigarettes After Sex
Album: Scum Fuck Flower Boy by Tyler, The Creator
Album: Voices In Song And Percussion by Hal Mooney And His Orchestra
Album: Where The Light Is (John Mayer Live In Los Angeles) by John Mayer
```

## Contribution

Feel free to fork this repository and make your contributions. You can improve the music recommendation algorithm, add new features, or optimize the code.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Discogs API](https://www.discogs.com/developers/) for providing access to a vast music database.
- [TensorFlow](https://www.tensorflow.org/) for the image classification model.
- [TextBlob](https://textblob.readthedocs.io/en/dev/) for sentiment analysis.
