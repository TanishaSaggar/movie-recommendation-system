```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```


```python
credits=pd.read_csv("tmdb_5000_credits.csv")
movies=pd.read_csv("tmdb_5000_movies.csv")
```


```python
movies
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>budget</th>
      <th>genres</th>
      <th>homepage</th>
      <th>id</th>
      <th>keywords</th>
      <th>original_language</th>
      <th>original_title</th>
      <th>overview</th>
      <th>popularity</th>
      <th>production_companies</th>
      <th>production_countries</th>
      <th>release_date</th>
      <th>revenue</th>
      <th>runtime</th>
      <th>spoken_languages</th>
      <th>status</th>
      <th>tagline</th>
      <th>title</th>
      <th>vote_average</th>
      <th>vote_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>237000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.avatarmovie.com/</td>
      <td>19995</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>en</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>150.437577</td>
      <td>[{"name": "Ingenious Film Partners", "id": 289...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2009-12-10</td>
      <td>2787965087</td>
      <td>162.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}, {"iso...</td>
      <td>Released</td>
      <td>Enter the World of Pandora.</td>
      <td>Avatar</td>
      <td>7.2</td>
      <td>11800</td>
    </tr>
    <tr>
      <th>1</th>
      <td>300000000</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>http://disney.go.com/disneypictures/pirates/</td>
      <td>285</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>en</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>139.082615</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}, {"...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2007-05-19</td>
      <td>961000000</td>
      <td>169.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>At the end of the world, the adventure begins.</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>6.9</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>245000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.sonypictures.com/movies/spectre/</td>
      <td>206647</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>en</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>107.376788</td>
      <td>[{"name": "Columbia Pictures", "id": 5}, {"nam...</td>
      <td>[{"iso_3166_1": "GB", "name": "United Kingdom"...</td>
      <td>2015-10-26</td>
      <td>880674609</td>
      <td>148.0</td>
      <td>[{"iso_639_1": "fr", "name": "Fran\u00e7ais"},...</td>
      <td>Released</td>
      <td>A Plan No One Escapes</td>
      <td>Spectre</td>
      <td>6.3</td>
      <td>4466</td>
    </tr>
    <tr>
      <th>3</th>
      <td>250000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>http://www.thedarkknightrises.com/</td>
      <td>49026</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>en</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>112.312950</td>
      <td>[{"name": "Legendary Pictures", "id": 923}, {"...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2012-07-16</td>
      <td>1084939099</td>
      <td>165.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>The Legend Ends</td>
      <td>The Dark Knight Rises</td>
      <td>7.6</td>
      <td>9106</td>
    </tr>
    <tr>
      <th>4</th>
      <td>260000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://movies.disney.com/john-carter</td>
      <td>49529</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>en</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>43.926995</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}]</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2012-03-07</td>
      <td>284139100</td>
      <td>132.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>Lost in our world, found in another.</td>
      <td>John Carter</td>
      <td>6.1</td>
      <td>2124</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4798</th>
      <td>220000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>NaN</td>
      <td>9367</td>
      <td>[{"id": 5616, "name": "united states\u2013mexi...</td>
      <td>es</td>
      <td>El Mariachi</td>
      <td>El Mariachi just wants to play his guitar and ...</td>
      <td>14.269792</td>
      <td>[{"name": "Columbia Pictures", "id": 5}]</td>
      <td>[{"iso_3166_1": "MX", "name": "Mexico"}, {"iso...</td>
      <td>1992-09-04</td>
      <td>2040920</td>
      <td>81.0</td>
      <td>[{"iso_639_1": "es", "name": "Espa\u00f1ol"}]</td>
      <td>Released</td>
      <td>He didn't come looking for trouble, but troubl...</td>
      <td>El Mariachi</td>
      <td>6.6</td>
      <td>238</td>
    </tr>
    <tr>
      <th>4799</th>
      <td>9000</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 10749, "...</td>
      <td>NaN</td>
      <td>72766</td>
      <td>[]</td>
      <td>en</td>
      <td>Newlyweds</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
      <td>0.642552</td>
      <td>[]</td>
      <td>[]</td>
      <td>2011-12-26</td>
      <td>0</td>
      <td>85.0</td>
      <td>[]</td>
      <td>Released</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
      <td>Newlyweds</td>
      <td>5.9</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4800</th>
      <td>0</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 18, "nam...</td>
      <td>http://www.hallmarkchannel.com/signedsealeddel...</td>
      <td>231617</td>
      <td>[{"id": 248, "name": "date"}, {"id": 699, "nam...</td>
      <td>en</td>
      <td>Signed, Sealed, Delivered</td>
      <td>"Signed, Sealed, Delivered" introduces a dedic...</td>
      <td>1.444476</td>
      <td>[{"name": "Front Street Pictures", "id": 3958}...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2013-10-13</td>
      <td>0</td>
      <td>120.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>NaN</td>
      <td>Signed, Sealed, Delivered</td>
      <td>7.0</td>
      <td>6</td>
    </tr>
    <tr>
      <th>4801</th>
      <td>0</td>
      <td>[]</td>
      <td>http://shanghaicalling.com/</td>
      <td>126186</td>
      <td>[]</td>
      <td>en</td>
      <td>Shanghai Calling</td>
      <td>When ambitious New York attorney Sam is sent t...</td>
      <td>0.857008</td>
      <td>[]</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2012-05-03</td>
      <td>0</td>
      <td>98.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>A New Yorker in Shanghai</td>
      <td>Shanghai Calling</td>
      <td>5.7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>4802</th>
      <td>0</td>
      <td>[{"id": 99, "name": "Documentary"}]</td>
      <td>NaN</td>
      <td>25975</td>
      <td>[{"id": 1523, "name": "obsession"}, {"id": 224...</td>
      <td>en</td>
      <td>My Date with Drew</td>
      <td>Ever since the second grade when he first saw ...</td>
      <td>1.929883</td>
      <td>[{"name": "rusty bear entertainment", "id": 87...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2005-08-05</td>
      <td>0</td>
      <td>90.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>NaN</td>
      <td>My Date with Drew</td>
      <td>6.3</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
<p>4803 rows × 20 columns</p>
</div>




```python
movies.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>budget</th>
      <th>genres</th>
      <th>homepage</th>
      <th>id</th>
      <th>keywords</th>
      <th>original_language</th>
      <th>original_title</th>
      <th>overview</th>
      <th>popularity</th>
      <th>production_companies</th>
      <th>production_countries</th>
      <th>release_date</th>
      <th>revenue</th>
      <th>runtime</th>
      <th>spoken_languages</th>
      <th>status</th>
      <th>tagline</th>
      <th>title</th>
      <th>vote_average</th>
      <th>vote_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>237000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.avatarmovie.com/</td>
      <td>19995</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>en</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>150.437577</td>
      <td>[{"name": "Ingenious Film Partners", "id": 289...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2009-12-10</td>
      <td>2787965087</td>
      <td>162.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}, {"iso...</td>
      <td>Released</td>
      <td>Enter the World of Pandora.</td>
      <td>Avatar</td>
      <td>7.2</td>
      <td>11800</td>
    </tr>
    <tr>
      <th>1</th>
      <td>300000000</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>http://disney.go.com/disneypictures/pirates/</td>
      <td>285</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>en</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>139.082615</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}, {"...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2007-05-19</td>
      <td>961000000</td>
      <td>169.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>At the end of the world, the adventure begins.</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>6.9</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>245000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.sonypictures.com/movies/spectre/</td>
      <td>206647</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>en</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>107.376788</td>
      <td>[{"name": "Columbia Pictures", "id": 5}, {"nam...</td>
      <td>[{"iso_3166_1": "GB", "name": "United Kingdom"...</td>
      <td>2015-10-26</td>
      <td>880674609</td>
      <td>148.0</td>
      <td>[{"iso_639_1": "fr", "name": "Fran\u00e7ais"},...</td>
      <td>Released</td>
      <td>A Plan No One Escapes</td>
      <td>Spectre</td>
      <td>6.3</td>
      <td>4466</td>
    </tr>
    <tr>
      <th>3</th>
      <td>250000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>http://www.thedarkknightrises.com/</td>
      <td>49026</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>en</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>112.312950</td>
      <td>[{"name": "Legendary Pictures", "id": 923}, {"...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2012-07-16</td>
      <td>1084939099</td>
      <td>165.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>The Legend Ends</td>
      <td>The Dark Knight Rises</td>
      <td>7.6</td>
      <td>9106</td>
    </tr>
    <tr>
      <th>4</th>
      <td>260000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://movies.disney.com/john-carter</td>
      <td>49529</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>en</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>43.926995</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}]</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2012-03-07</td>
      <td>284139100</td>
      <td>132.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>Lost in our world, found in another.</td>
      <td>John Carter</td>
      <td>6.1</td>
      <td>2124</td>
    </tr>
  </tbody>
</table>
</div>




```python
credits.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
credits.head(1)['crew'].values
```




    array(['[{"credit_id": "52fe48009251416c750aca23", "department": "Editing", "gender": 0, "id": 1721, "job": "Editor", "name": "Stephen E. Rivkin"}, {"credit_id": "539c47ecc3a36810e3001f87", "department": "Art", "gender": 2, "id": 496, "job": "Production Design", "name": "Rick Carter"}, {"credit_id": "54491c89c3a3680fb4001cf7", "department": "Sound", "gender": 0, "id": 900, "job": "Sound Designer", "name": "Christopher Boyes"}, {"credit_id": "54491cb70e0a267480001bd0", "department": "Sound", "gender": 0, "id": 900, "job": "Supervising Sound Editor", "name": "Christopher Boyes"}, {"credit_id": "539c4a4cc3a36810c9002101", "department": "Production", "gender": 1, "id": 1262, "job": "Casting", "name": "Mali Finn"}, {"credit_id": "5544ee3b925141499f0008fc", "department": "Sound", "gender": 2, "id": 1729, "job": "Original Music Composer", "name": "James Horner"}, {"credit_id": "52fe48009251416c750ac9c3", "department": "Directing", "gender": 2, "id": 2710, "job": "Director", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750ac9d9", "department": "Writing", "gender": 2, "id": 2710, "job": "Writer", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca17", "department": "Editing", "gender": 2, "id": 2710, "job": "Editor", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca29", "department": "Production", "gender": 2, "id": 2710, "job": "Producer", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca3f", "department": "Writing", "gender": 2, "id": 2710, "job": "Screenplay", "name": "James Cameron"}, {"credit_id": "539c4987c3a36810ba0021a4", "department": "Art", "gender": 2, "id": 7236, "job": "Art Direction", "name": "Andrew Menzies"}, {"credit_id": "549598c3c3a3686ae9004383", "department": "Visual Effects", "gender": 0, "id": 6690, "job": "Visual Effects Producer", "name": "Jill Brooks"}, {"credit_id": "52fe48009251416c750aca4b", "department": "Production", "gender": 1, "id": 6347, "job": "Casting", "name": "Margery Simkin"}, {"credit_id": "570b6f419251417da70032fe", "department": "Art", "gender": 2, "id": 6878, "job": "Supervising Art Director", "name": "Kevin Ishioka"}, {"credit_id": "5495a0fac3a3686ae9004468", "department": "Sound", "gender": 0, "id": 6883, "job": "Music Editor", "name": "Dick Bernstein"}, {"credit_id": "54959706c3a3686af3003e81", "department": "Sound", "gender": 0, "id": 8159, "job": "Sound Effects Editor", "name": "Shannon Mills"}, {"credit_id": "54491d58c3a3680fb1001ccb", "department": "Sound", "gender": 0, "id": 8160, "job": "Foley", "name": "Dennie Thorpe"}, {"credit_id": "54491d6cc3a3680fa5001b2c", "department": "Sound", "gender": 0, "id": 8163, "job": "Foley", "name": "Jana Vance"}, {"credit_id": "52fe48009251416c750aca57", "department": "Costume & Make-Up", "gender": 1, "id": 8527, "job": "Costume Design", "name": "Deborah Lynn Scott"}, {"credit_id": "52fe48009251416c750aca2f", "department": "Production", "gender": 2, "id": 8529, "job": "Producer", "name": "Jon Landau"}, {"credit_id": "539c4937c3a36810ba002194", "department": "Art", "gender": 0, "id": 9618, "job": "Art Direction", "name": "Sean Haworth"}, {"credit_id": "539c49b6c3a36810c10020e6", "department": "Art", "gender": 1, "id": 12653, "job": "Set Decoration", "name": "Kim Sinclair"}, {"credit_id": "570b6f2f9251413a0e00020d", "department": "Art", "gender": 1, "id": 12653, "job": "Supervising Art Director", "name": "Kim Sinclair"}, {"credit_id": "54491a6c0e0a26748c001b19", "department": "Art", "gender": 2, "id": 14350, "job": "Set Designer", "name": "Richard F. Mays"}, {"credit_id": "56928cf4c3a3684cff0025c4", "department": "Production", "gender": 1, "id": 20294, "job": "Executive Producer", "name": "Laeta Kalogridis"}, {"credit_id": "52fe48009251416c750aca51", "department": "Costume & Make-Up", "gender": 0, "id": 17675, "job": "Costume Design", "name": "Mayes C. Rubeo"}, {"credit_id": "52fe48009251416c750aca11", "department": "Camera", "gender": 2, "id": 18265, "job": "Director of Photography", "name": "Mauro Fiore"}, {"credit_id": "5449194d0e0a26748f001b39", "department": "Art", "gender": 0, "id": 42281, "job": "Set Designer", "name": "Scott Herbertson"}, {"credit_id": "52fe48009251416c750aca05", "department": "Crew", "gender": 0, "id": 42288, "job": "Stunts", "name": "Woody Schultz"}, {"credit_id": "5592aefb92514152de0010f5", "department": "Costume & Make-Up", "gender": 0, "id": 29067, "job": "Makeup Artist", "name": "Linda DeVetta"}, {"credit_id": "5592afa492514152de00112c", "department": "Costume & Make-Up", "gender": 0, "id": 29067, "job": "Hairstylist", "name": "Linda DeVetta"}, {"credit_id": "54959ed592514130fc002e5d", "department": "Camera", "gender": 2, "id": 33302, "job": "Camera Operator", "name": "Richard Bluck"}, {"credit_id": "539c4891c3a36810ba002147", "department": "Art", "gender": 2, "id": 33303, "job": "Art Direction", "name": "Simon Bright"}, {"credit_id": "54959c069251417a81001f3a", "department": "Visual Effects", "gender": 0, "id": 113145, "job": "Visual Effects Supervisor", "name": "Richard Martin"}, {"credit_id": "54959a0dc3a3680ff5002c8d", "department": "Crew", "gender": 2, "id": 58188, "job": "Visual Effects Editor", "name": "Steve R. Moore"}, {"credit_id": "52fe48009251416c750aca1d", "department": "Editing", "gender": 2, "id": 58871, "job": "Editor", "name": "John Refoua"}, {"credit_id": "54491a4dc3a3680fc30018ca", "department": "Art", "gender": 0, "id": 92359, "job": "Set Designer", "name": "Karl J. Martin"}, {"credit_id": "52fe48009251416c750aca35", "department": "Camera", "gender": 1, "id": 72201, "job": "Director of Photography", "name": "Chiling Lin"}, {"credit_id": "52fe48009251416c750ac9ff", "department": "Crew", "gender": 0, "id": 89714, "job": "Stunts", "name": "Ilram Choi"}, {"credit_id": "54959c529251416e2b004394", "department": "Visual Effects", "gender": 2, "id": 93214, "job": "Visual Effects Supervisor", "name": "Steven Quale"}, {"credit_id": "54491edf0e0a267489001c37", "department": "Crew", "gender": 1, "id": 122607, "job": "Dialect Coach", "name": "Carla Meyer"}, {"credit_id": "539c485bc3a368653d001a3a", "department": "Art", "gender": 2, "id": 132585, "job": "Art Direction", "name": "Nick Bassett"}, {"credit_id": "539c4903c3a368653d001a74", "department": "Art", "gender": 0, "id": 132596, "job": "Art Direction", "name": "Jill Cormack"}, {"credit_id": "539c4967c3a368653d001a94", "department": "Art", "gender": 0, "id": 132604, "job": "Art Direction", "name": "Andy McLaren"}, {"credit_id": "52fe48009251416c750aca45", "department": "Crew", "gender": 0, "id": 236696, "job": "Motion Capture Artist", "name": "Terry Notary"}, {"credit_id": "54959e02c3a3680fc60027d2", "department": "Crew", "gender": 2, "id": 956198, "job": "Stunt Coordinator", "name": "Garrett Warren"}, {"credit_id": "54959ca3c3a3686ae300438c", "department": "Visual Effects", "gender": 2, "id": 957874, "job": "Visual Effects Supervisor", "name": "Jonathan Rothbart"}, {"credit_id": "570b6f519251412c74001b2f", "department": "Art", "gender": 0, "id": 957889, "job": "Supervising Art Director", "name": "Stefan Dechant"}, {"credit_id": "570b6f62c3a3680b77007460", "department": "Art", "gender": 2, "id": 959555, "job": "Supervising Art Director", "name": "Todd Cherniawsky"}, {"credit_id": "539c4a3ac3a36810da0021cc", "department": "Production", "gender": 0, "id": 1016177, "job": "Casting", "name": "Miranda Rivers"}, {"credit_id": "539c482cc3a36810c1002062", "department": "Art", "gender": 0, "id": 1032536, "job": "Production Design", "name": "Robert Stromberg"}, {"credit_id": "539c4b65c3a36810c9002125", "department": "Costume & Make-Up", "gender": 2, "id": 1071680, "job": "Costume Design", "name": "John Harding"}, {"credit_id": "54959e6692514130fc002e4e", "department": "Camera", "gender": 0, "id": 1177364, "job": "Steadicam Operator", "name": "Roberto De Angelis"}, {"credit_id": "539c49f1c3a368653d001aac", "department": "Costume & Make-Up", "gender": 2, "id": 1202850, "job": "Makeup Department Head", "name": "Mike Smithson"}, {"credit_id": "5495999ec3a3686ae100460c", "department": "Visual Effects", "gender": 0, "id": 1204668, "job": "Visual Effects Producer", "name": "Alain Lalanne"}, {"credit_id": "54959cdfc3a3681153002729", "department": "Visual Effects", "gender": 0, "id": 1206410, "job": "Visual Effects Supervisor", "name": "Lucas Salton"}, {"credit_id": "549596239251417a81001eae", "department": "Crew", "gender": 0, "id": 1234266, "job": "Post Production Supervisor", "name": "Janace Tashjian"}, {"credit_id": "54959c859251416e1e003efe", "department": "Visual Effects", "gender": 0, "id": 1271932, "job": "Visual Effects Supervisor", "name": "Stephen Rosenbaum"}, {"credit_id": "5592af28c3a368775a00105f", "department": "Costume & Make-Up", "gender": 0, "id": 1310064, "job": "Makeup Artist", "name": "Frankie Karena"}, {"credit_id": "539c4adfc3a36810e300203b", "department": "Costume & Make-Up", "gender": 1, "id": 1319844, "job": "Costume Supervisor", "name": "Lisa Lovaas"}, {"credit_id": "54959b579251416e2b004371", "department": "Visual Effects", "gender": 0, "id": 1327028, "job": "Visual Effects Supervisor", "name": "Jonathan Fawkner"}, {"credit_id": "539c48a7c3a36810b5001fa7", "department": "Art", "gender": 0, "id": 1330561, "job": "Art Direction", "name": "Robert Bavin"}, {"credit_id": "539c4a71c3a36810da0021e0", "department": "Costume & Make-Up", "gender": 0, "id": 1330567, "job": "Costume Supervisor", "name": "Anthony Almaraz"}, {"credit_id": "539c4a8ac3a36810ba0021e4", "department": "Costume & Make-Up", "gender": 0, "id": 1330570, "job": "Costume Supervisor", "name": "Carolyn M. Fenton"}, {"credit_id": "539c4ab6c3a36810da0021f0", "department": "Costume & Make-Up", "gender": 0, "id": 1330574, "job": "Costume Supervisor", "name": "Beth Koenigsberg"}, {"credit_id": "54491ab70e0a267480001ba2", "department": "Art", "gender": 0, "id": 1336191, "job": "Set Designer", "name": "Sam Page"}, {"credit_id": "544919d9c3a3680fc30018bd", "department": "Art", "gender": 0, "id": 1339441, "job": "Set Designer", "name": "Tex Kadonaga"}, {"credit_id": "54491cf50e0a267483001b0c", "department": "Editing", "gender": 0, "id": 1352422, "job": "Dialogue Editor", "name": "Kim Foscato"}, {"credit_id": "544919f40e0a26748c001b09", "department": "Art", "gender": 0, "id": 1352962, "job": "Set Designer", "name": "Tammy S. Lee"}, {"credit_id": "5495a115c3a3680ff5002d71", "department": "Crew", "gender": 0, "id": 1357070, "job": "Transportation Coordinator", "name": "Denny Caira"}, {"credit_id": "5495a12f92514130fc002e94", "department": "Crew", "gender": 0, "id": 1357071, "job": "Transportation Coordinator", "name": "James Waitkus"}, {"credit_id": "5495976fc3a36811530026b0", "department": "Sound", "gender": 0, "id": 1360103, "job": "Supervising Sound Editor", "name": "Addison Teague"}, {"credit_id": "54491837c3a3680fb1001c5a", "department": "Art", "gender": 2, "id": 1376887, "job": "Set Designer", "name": "C. Scott Baker"}, {"credit_id": "54491878c3a3680fb4001c9d", "department": "Art", "gender": 0, "id": 1376888, "job": "Set Designer", "name": "Luke Caska"}, {"credit_id": "544918dac3a3680fa5001ae0", "department": "Art", "gender": 0, "id": 1376889, "job": "Set Designer", "name": "David Chow"}, {"credit_id": "544919110e0a267486001b68", "department": "Art", "gender": 0, "id": 1376890, "job": "Set Designer", "name": "Jonathan Dyer"}, {"credit_id": "54491967c3a3680faa001b5e", "department": "Art", "gender": 0, "id": 1376891, "job": "Set Designer", "name": "Joseph Hiura"}, {"credit_id": "54491997c3a3680fb1001c8a", "department": "Art", "gender": 0, "id": 1376892, "job": "Art Department Coordinator", "name": "Rebecca Jellie"}, {"credit_id": "544919ba0e0a26748f001b42", "department": "Art", "gender": 0, "id": 1376893, "job": "Set Designer", "name": "Robert Andrew Johnson"}, {"credit_id": "54491b1dc3a3680faa001b8c", "department": "Art", "gender": 0, "id": 1376895, "job": "Assistant Art Director", "name": "Mike Stassi"}, {"credit_id": "54491b79c3a3680fbb001826", "department": "Art", "gender": 0, "id": 1376897, "job": "Construction Coordinator", "name": "John Villarino"}, {"credit_id": "54491baec3a3680fb4001ce6", "department": "Art", "gender": 2, "id": 1376898, "job": "Assistant Art Director", "name": "Jeffrey Wisniewski"}, {"credit_id": "54491d2fc3a3680fb4001d07", "department": "Editing", "gender": 0, "id": 1376899, "job": "Dialogue Editor", "name": "Cheryl Nardi"}, {"credit_id": "54491d86c3a3680fa5001b2f", "department": "Editing", "gender": 0, "id": 1376901, "job": "Dialogue Editor", "name": "Marshall Winn"}, {"credit_id": "54491d9dc3a3680faa001bb0", "department": "Sound", "gender": 0, "id": 1376902, "job": "Supervising Sound Editor", "name": "Gwendolyn Yates Whittle"}, {"credit_id": "54491dc10e0a267486001bce", "department": "Sound", "gender": 0, "id": 1376903, "job": "Sound Re-Recording Mixer", "name": "William Stein"}, {"credit_id": "54491f500e0a26747c001c07", "department": "Crew", "gender": 0, "id": 1376909, "job": "Choreographer", "name": "Lula Washington"}, {"credit_id": "549599239251412c4e002a2e", "department": "Visual Effects", "gender": 0, "id": 1391692, "job": "Visual Effects Producer", "name": "Chris Del Conte"}, {"credit_id": "54959d54c3a36831b8001d9a", "department": "Visual Effects", "gender": 2, "id": 1391695, "job": "Visual Effects Supervisor", "name": "R. Christopher White"}, {"credit_id": "54959bdf9251412c4e002a66", "department": "Visual Effects", "gender": 0, "id": 1394070, "job": "Visual Effects Supervisor", "name": "Dan Lemmon"}, {"credit_id": "5495971d92514132ed002922", "department": "Sound", "gender": 0, "id": 1394129, "job": "Sound Effects Editor", "name": "Tim Nielsen"}, {"credit_id": "5592b25792514152cc0011aa", "department": "Crew", "gender": 0, "id": 1394286, "job": "CG Supervisor", "name": "Michael Mulholland"}, {"credit_id": "54959a329251416e2b004355", "department": "Crew", "gender": 0, "id": 1394750, "job": "Visual Effects Editor", "name": "Thomas Nittmann"}, {"credit_id": "54959d6dc3a3686ae9004401", "department": "Visual Effects", "gender": 0, "id": 1394755, "job": "Visual Effects Supervisor", "name": "Edson Williams"}, {"credit_id": "5495a08fc3a3686ae300441c", "department": "Editing", "gender": 0, "id": 1394953, "job": "Digital Intermediate", "name": "Christine Carr"}, {"credit_id": "55402d659251413d6d000249", "department": "Visual Effects", "gender": 0, "id": 1395269, "job": "Visual Effects Supervisor", "name": "John Bruno"}, {"credit_id": "54959e7b9251416e1e003f3e", "department": "Camera", "gender": 0, "id": 1398970, "job": "Steadicam Operator", "name": "David Emmerichs"}, {"credit_id": "54959734c3a3686ae10045e0", "department": "Sound", "gender": 0, "id": 1400906, "job": "Sound Effects Editor", "name": "Christopher Scarabosio"}, {"credit_id": "549595dd92514130fc002d79", "department": "Production", "gender": 0, "id": 1401784, "job": "Production Supervisor", "name": "Jennifer Teves"}, {"credit_id": "549596009251413af70028cc", "department": "Production", "gender": 0, "id": 1401785, "job": "Production Manager", "name": "Brigitte Yorke"}, {"credit_id": "549596e892514130fc002d99", "department": "Sound", "gender": 0, "id": 1401786, "job": "Sound Effects Editor", "name": "Ken Fischer"}, {"credit_id": "549598229251412c4e002a1c", "department": "Crew", "gender": 0, "id": 1401787, "job": "Special Effects Coordinator", "name": "Iain Hutton"}, {"credit_id": "549598349251416e2b00432b", "department": "Crew", "gender": 0, "id": 1401788, "job": "Special Effects Coordinator", "name": "Steve Ingram"}, {"credit_id": "54959905c3a3686ae3004324", "department": "Visual Effects", "gender": 0, "id": 1401789, "job": "Visual Effects Producer", "name": "Joyce Cox"}, {"credit_id": "5495994b92514132ed002951", "department": "Visual Effects", "gender": 0, "id": 1401790, "job": "Visual Effects Producer", "name": "Jenny Foster"}, {"credit_id": "549599cbc3a3686ae1004613", "department": "Crew", "gender": 0, "id": 1401791, "job": "Visual Effects Editor", "name": "Christopher Marino"}, {"credit_id": "549599f2c3a3686ae100461e", "department": "Crew", "gender": 0, "id": 1401792, "job": "Visual Effects Editor", "name": "Jim Milton"}, {"credit_id": "54959a51c3a3686af3003eb5", "department": "Visual Effects", "gender": 0, "id": 1401793, "job": "Visual Effects Producer", "name": "Cyndi Ochs"}, {"credit_id": "54959a7cc3a36811530026f4", "department": "Crew", "gender": 0, "id": 1401794, "job": "Visual Effects Editor", "name": "Lucas Putnam"}, {"credit_id": "54959b91c3a3680ff5002cb4", "department": "Visual Effects", "gender": 0, "id": 1401795, "job": "Visual Effects Supervisor", "name": "Anthony \'Max\' Ivins"}, {"credit_id": "54959bb69251412c4e002a5f", "department": "Visual Effects", "gender": 0, "id": 1401796, "job": "Visual Effects Supervisor", "name": "John Knoll"}, {"credit_id": "54959cbbc3a3686ae3004391", "department": "Visual Effects", "gender": 2, "id": 1401799, "job": "Visual Effects Supervisor", "name": "Eric Saindon"}, {"credit_id": "54959d06c3a3686ae90043f6", "department": "Visual Effects", "gender": 0, "id": 1401800, "job": "Visual Effects Supervisor", "name": "Wayne Stables"}, {"credit_id": "54959d259251416e1e003f11", "department": "Visual Effects", "gender": 0, "id": 1401801, "job": "Visual Effects Supervisor", "name": "David Stinnett"}, {"credit_id": "54959db49251413af7002975", "department": "Visual Effects", "gender": 0, "id": 1401803, "job": "Visual Effects Supervisor", "name": "Guy Williams"}, {"credit_id": "54959de4c3a3681153002750", "department": "Crew", "gender": 0, "id": 1401804, "job": "Stunt Coordinator", "name": "Stuart Thorp"}, {"credit_id": "54959ef2c3a3680fc60027f2", "department": "Lighting", "gender": 0, "id": 1401805, "job": "Best Boy Electric", "name": "Giles Coburn"}, {"credit_id": "54959f07c3a3680fc60027f9", "department": "Camera", "gender": 2, "id": 1401806, "job": "Still Photographer", "name": "Mark Fellman"}, {"credit_id": "54959f47c3a3681153002774", "department": "Lighting", "gender": 0, "id": 1401807, "job": "Lighting Technician", "name": "Scott Sprague"}, {"credit_id": "54959f8cc3a36831b8001df2", "department": "Visual Effects", "gender": 0, "id": 1401808, "job": "Animation Director", "name": "Jeremy Hollobon"}, {"credit_id": "54959fa0c3a36831b8001dfb", "department": "Visual Effects", "gender": 0, "id": 1401809, "job": "Animation Director", "name": "Orlando Meunier"}, {"credit_id": "54959fb6c3a3686af3003f54", "department": "Visual Effects", "gender": 0, "id": 1401810, "job": "Animation Director", "name": "Taisuke Tanimura"}, {"credit_id": "54959fd2c3a36831b8001e02", "department": "Costume & Make-Up", "gender": 0, "id": 1401812, "job": "Set Costumer", "name": "Lilia Mishel Acevedo"}, {"credit_id": "54959ff9c3a3686ae300440c", "department": "Costume & Make-Up", "gender": 0, "id": 1401814, "job": "Set Costumer", "name": "Alejandro M. Hernandez"}, {"credit_id": "5495a0ddc3a3686ae10046fe", "department": "Editing", "gender": 0, "id": 1401815, "job": "Digital Intermediate", "name": "Marvin Hall"}, {"credit_id": "5495a1f7c3a3686ae3004443", "department": "Production", "gender": 0, "id": 1401816, "job": "Publicist", "name": "Judy Alley"}, {"credit_id": "5592b29fc3a36869d100002f", "department": "Crew", "gender": 0, "id": 1418381, "job": "CG Supervisor", "name": "Mike Perry"}, {"credit_id": "5592b23a9251415df8001081", "department": "Crew", "gender": 0, "id": 1426854, "job": "CG Supervisor", "name": "Andrew Morley"}, {"credit_id": "55491e1192514104c40002d8", "department": "Art", "gender": 0, "id": 1438901, "job": "Conceptual Design", "name": "Seth Engstrom"}, {"credit_id": "5525d5809251417276002b06", "department": "Crew", "gender": 0, "id": 1447362, "job": "Visual Effects Art Director", "name": "Eric Oliver"}, {"credit_id": "554427ca925141586500312a", "department": "Visual Effects", "gender": 0, "id": 1447503, "job": "Modeling", "name": "Matsune Suzuki"}, {"credit_id": "551906889251415aab001c88", "department": "Art", "gender": 0, "id": 1447524, "job": "Art Department Manager", "name": "Paul Tobin"}, {"credit_id": "5592af8492514152cc0010de", "department": "Costume & Make-Up", "gender": 0, "id": 1452643, "job": "Hairstylist", "name": "Roxane Griffin"}, {"credit_id": "553d3c109251415852001318", "department": "Lighting", "gender": 0, "id": 1453938, "job": "Lighting Artist", "name": "Arun Ram-Mohan"}, {"credit_id": "5592af4692514152d5001355", "department": "Costume & Make-Up", "gender": 0, "id": 1457305, "job": "Makeup Artist", "name": "Georgia Lockhart-Adams"}, {"credit_id": "5592b2eac3a36877470012a5", "department": "Crew", "gender": 0, "id": 1466035, "job": "CG Supervisor", "name": "Thrain Shadbolt"}, {"credit_id": "5592b032c3a36877450015f1", "department": "Crew", "gender": 0, "id": 1483220, "job": "CG Supervisor", "name": "Brad Alexander"}, {"credit_id": "5592b05592514152d80012f6", "department": "Crew", "gender": 0, "id": 1483221, "job": "CG Supervisor", "name": "Shadi Almassizadeh"}, {"credit_id": "5592b090c3a36877570010b5", "department": "Crew", "gender": 0, "id": 1483222, "job": "CG Supervisor", "name": "Simon Clutterbuck"}, {"credit_id": "5592b0dbc3a368774b00112c", "department": "Crew", "gender": 0, "id": 1483223, "job": "CG Supervisor", "name": "Graeme Demmocks"}, {"credit_id": "5592b0fe92514152db0010c1", "department": "Crew", "gender": 0, "id": 1483224, "job": "CG Supervisor", "name": "Adrian Fernandes"}, {"credit_id": "5592b11f9251415df8001059", "department": "Crew", "gender": 0, "id": 1483225, "job": "CG Supervisor", "name": "Mitch Gates"}, {"credit_id": "5592b15dc3a3687745001645", "department": "Crew", "gender": 0, "id": 1483226, "job": "CG Supervisor", "name": "Jerry Kung"}, {"credit_id": "5592b18e925141645a0004ae", "department": "Crew", "gender": 0, "id": 1483227, "job": "CG Supervisor", "name": "Andy Lomas"}, {"credit_id": "5592b1bfc3a368775d0010e7", "department": "Crew", "gender": 0, "id": 1483228, "job": "CG Supervisor", "name": "Sebastian Marino"}, {"credit_id": "5592b2049251415df8001078", "department": "Crew", "gender": 0, "id": 1483229, "job": "CG Supervisor", "name": "Matthias Menz"}, {"credit_id": "5592b27b92514152d800136a", "department": "Crew", "gender": 0, "id": 1483230, "job": "CG Supervisor", "name": "Sergei Nevshupov"}, {"credit_id": "5592b2c3c3a36869e800003c", "department": "Crew", "gender": 0, "id": 1483231, "job": "CG Supervisor", "name": "Philippe Rebours"}, {"credit_id": "5592b317c3a36877470012af", "department": "Crew", "gender": 0, "id": 1483232, "job": "CG Supervisor", "name": "Michael Takarangi"}, {"credit_id": "5592b345c3a36877470012bb", "department": "Crew", "gender": 0, "id": 1483233, "job": "CG Supervisor", "name": "David Weitzberg"}, {"credit_id": "5592b37cc3a368775100113b", "department": "Crew", "gender": 0, "id": 1483234, "job": "CG Supervisor", "name": "Ben White"}, {"credit_id": "573c8e2f9251413f5d000094", "department": "Crew", "gender": 1, "id": 1621932, "job": "Stunts", "name": "Min Windle"}]'],
          dtype=object)




```python
movies=movies.merge(credits,on='title')
```




```python
movies=movies[['movie_id','title','overview','genres','keywords','cast','crew']]
```


```python

```


```python
movies.isnull().sum()
```




    movie_id    0
    title       0
    overview    3
    genres      0
    keywords    0
    cast        0
    crew        0
    dtype: int64




```python
movies.dropna(inplace=True)
```


```python
movies.isnull().sum()
```




    movie_id    0
    title       0
    overview    0
    genres      0
    keywords    0
    cast        0
    crew        0
    dtype: int64




```python
movies.duplicated().sum()
```




    0




```python
movies.duplicated().sum()
```




    0




```python
movies.dropna(inplace=True)
```


```python
movies.duplicated().sum()
```




    0




```python
movies=movies.drop_duplicates(keep=False)
```


```python
movies.duplicated().sum()
```




    0



movies


```python
movies
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>9367</td>
      <td>El Mariachi</td>
      <td>El Mariachi just wants to play his guitar and ...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>[{"id": 5616, "name": "united states\u2013mexi...</td>
      <td>[{"cast_id": 1, "character": "El Mariachi", "c...</td>
      <td>[{"credit_id": "52fe44eec3a36847f80b280b", "de...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>72766</td>
      <td>Newlyweds</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 10749, "...</td>
      <td>[]</td>
      <td>[{"cast_id": 1, "character": "Buzzy", "credit_...</td>
      <td>[{"credit_id": "52fe487dc3a368484e0fb013", "de...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>231617</td>
      <td>Signed, Sealed, Delivered</td>
      <td>"Signed, Sealed, Delivered" introduces a dedic...</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 18, "nam...</td>
      <td>[{"id": 248, "name": "date"}, {"id": 699, "nam...</td>
      <td>[{"cast_id": 8, "character": "Oliver O\u2019To...</td>
      <td>[{"credit_id": "52fe4df3c3a36847f8275ecf", "de...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>126186</td>
      <td>Shanghai Calling</td>
      <td>When ambitious New York attorney Sam is sent t...</td>
      <td>[]</td>
      <td>[]</td>
      <td>[{"cast_id": 3, "character": "Sam", "credit_id...</td>
      <td>[{"credit_id": "52fe4ad9c3a368484e16a36b", "de...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>25975</td>
      <td>My Date with Drew</td>
      <td>Ever since the second grade when he first saw ...</td>
      <td>[{"id": 99, "name": "Documentary"}]</td>
      <td>[{"id": 1523, "name": "obsession"}, {"id": 224...</td>
      <td>[{"cast_id": 3, "character": "Herself", "credi...</td>
      <td>[{"credit_id": "58ce021b9251415a390165d9", "de...</td>
    </tr>
  </tbody>
</table>
<p>4806 rows × 7 columns</p>
</div>




```python
movies.duplicated().sum()
```




    0




```python
movies.iloc[0].genres
```




    '[{"id": 28, "name": "Action"}, {"id": 12, "name": "Adventure"}, {"id": 14, "name": "Fantasy"}, {"id": 878, "name": "Science Fiction"}]'




```python
def convert(obj):
    L=[]
    for i in ast.literal_eval(obj):
        L.append(i['name'])
        
    return L
```


```python
convert('[{"id": 28, "name": "Action"}, {"id": 12, "name": "Adventure"}, {"id": 14, "name": "Fantasy"}, {"id": 878, "name": "Science Fiction"}]')
```




    ['Action', 'Adventure', 'Fantasy', 'Science Fiction']




```python
import ast
```


```python
movies['genres'].apply(convert)
```




    0       [Action, Adventure, Fantasy, Science Fiction]
    1                        [Adventure, Fantasy, Action]
    2                          [Action, Adventure, Crime]
    3                    [Action, Crime, Drama, Thriller]
    4                [Action, Adventure, Science Fiction]
                                ...                      
    4804                        [Action, Crime, Thriller]
    4805                                [Comedy, Romance]
    4806               [Comedy, Drama, Romance, TV Movie]
    4807                                               []
    4808                                    [Documentary]
    Name: genres, Length: 4806, dtype: object




```python
movies['genres']=movies['genres'].apply(convert)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['keywords']=movies['keywords'].apply(convert)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies.cast[1]
```




    '[{"cast_id": 4, "character": "Captain Jack Sparrow", "credit_id": "52fe4232c3a36847f800b50d", "gender": 2, "id": 85, "name": "Johnny Depp", "order": 0}, {"cast_id": 5, "character": "Will Turner", "credit_id": "52fe4232c3a36847f800b511", "gender": 2, "id": 114, "name": "Orlando Bloom", "order": 1}, {"cast_id": 6, "character": "Elizabeth Swann", "credit_id": "52fe4232c3a36847f800b515", "gender": 1, "id": 116, "name": "Keira Knightley", "order": 2}, {"cast_id": 12, "character": "William \\"Bootstrap Bill\\" Turner", "credit_id": "52fe4232c3a36847f800b52d", "gender": 2, "id": 1640, "name": "Stellan Skarsg\\u00e5rd", "order": 3}, {"cast_id": 10, "character": "Captain Sao Feng", "credit_id": "52fe4232c3a36847f800b525", "gender": 2, "id": 1619, "name": "Chow Yun-fat", "order": 4}, {"cast_id": 9, "character": "Captain Davy Jones", "credit_id": "52fe4232c3a36847f800b521", "gender": 2, "id": 2440, "name": "Bill Nighy", "order": 5}, {"cast_id": 7, "character": "Captain Hector Barbossa", "credit_id": "52fe4232c3a36847f800b519", "gender": 2, "id": 118, "name": "Geoffrey Rush", "order": 6}, {"cast_id": 14, "character": "Admiral James Norrington", "credit_id": "52fe4232c3a36847f800b535", "gender": 2, "id": 1709, "name": "Jack Davenport", "order": 7}, {"cast_id": 13, "character": "Joshamee Gibbs", "credit_id": "52fe4232c3a36847f800b531", "gender": 2, "id": 2449, "name": "Kevin McNally", "order": 8}, {"cast_id": 11, "character": "Lord Cutler Beckett", "credit_id": "52fe4232c3a36847f800b529", "gender": 2, "id": 2441, "name": "Tom Hollander", "order": 9}, {"cast_id": 19, "character": "Tia Dalma", "credit_id": "52fe4232c3a36847f800b549", "gender": 1, "id": 2038, "name": "Naomie Harris", "order": 10}, {"cast_id": 8, "character": "Governor Weatherby Swann", "credit_id": "52fe4232c3a36847f800b51d", "gender": 2, "id": 378, "name": "Jonathan Pryce", "order": 11}, {"cast_id": 37, "character": "Captain Teague Sparrow", "credit_id": "52fe4232c3a36847f800b5b3", "gender": 2, "id": 1430, "name": "Keith Richards", "order": 12}, {"cast_id": 16, "character": "Pintel", "credit_id": "52fe4232c3a36847f800b53d", "gender": 2, "id": 1710, "name": "Lee Arenberg", "order": 13}, {"cast_id": 15, "character": "Ragetti", "credit_id": "52fe4232c3a36847f800b539", "gender": 2, "id": 1711, "name": "Mackenzie Crook", "order": 14}, {"cast_id": 18, "character": "Lieutenant Theodore Groves", "credit_id": "52fe4232c3a36847f800b545", "gender": 2, "id": 4031, "name": "Greg Ellis", "order": 15}, {"cast_id": 55, "character": "Cotton", "credit_id": "57e28d2ec3a3681a01005b5c", "gender": 2, "id": 1715, "name": "David Bailie", "order": 16}, {"cast_id": 17, "character": "Marty", "credit_id": "52fe4232c3a36847f800b541", "gender": 2, "id": 4030, "name": "Martin Klebba", "order": 17}, {"cast_id": 57, "character": "Ian Mercer", "credit_id": "57e28d78c3a36808b900bf4f", "gender": 0, "id": 939, "name": "David Schofield", "order": 18}, {"cast_id": 62, "character": "Scarlett", "credit_id": "57e28ec5c3a3681a50005855", "gender": 1, "id": 2450, "name": "Lauren Maher", "order": 19}, {"cast_id": 63, "character": "Giselle", "credit_id": "57e28ed692514123f5005635", "gender": 1, "id": 2452, "name": "Vanessa Branch", "order": 20}, {"cast_id": 60, "character": "Mullroy", "credit_id": "57e28db2c3a3681a01005bc7", "gender": 2, "id": 1714, "name": "Angus Barnett", "order": 21}, {"cast_id": 59, "character": "Murtogg", "credit_id": "57e28da192514118f7006008", "gender": 0, "id": 1713, "name": "Giles New", "order": 22}, {"cast_id": 58, "character": "Tai Huang", "credit_id": "57e28d8ec3a3681a01005bab", "gender": 2, "id": 22075, "name": "Reggie Lee", "order": 23}, {"cast_id": 64, "character": "Henry Turner", "credit_id": "57e29119925141151100a6cc", "gender": 2, "id": 61259, "name": "Dominic Scott Kay", "order": 24}, {"cast_id": 39, "character": "Mistress Ching", "credit_id": "52fe4232c3a36847f800b5bd", "gender": 1, "id": 33500, "name": "Takayo Fischer", "order": 25}, {"cast_id": 40, "character": "Lieutenant Greitzer", "credit_id": "52fe4232c3a36847f800b5c1", "gender": 2, "id": 1224149, "name": "David Meunier", "order": 26}, {"cast_id": 49, "character": "Hadras", "credit_id": "56d1871c92514174680010cf", "gender": 2, "id": 429401, "name": "Ho-Kwan Tse", "order": 27}, {"cast_id": 56, "character": "Clacker", "credit_id": "57e28d4b92514125710055cb", "gender": 0, "id": 1123, "name": "Andy Beckwith", "order": 28}, {"cast_id": 51, "character": "Penrod", "credit_id": "56ec8c14c3a3682260003c53", "gender": 2, "id": 1056117, "name": "Peter Donald Badalamenti II", "order": 29}, {"cast_id": 61, "character": "Cotton\'s Parrot (voice)", "credit_id": "57e28dcc9251412463005678", "gender": 2, "id": 21700, "name": "Christopher S. Capp", "order": 30}, {"cast_id": 65, "character": "Captain Teague", "credit_id": "58bc2a37c3a368663003740b", "gender": 2, "id": 1430, "name": "Keith Richards", "order": 31}, {"cast_id": 66, "character": "Captain Jocard", "credit_id": "58bc2a8e925141609e03a179", "gender": 2, "id": 2603, "name": "Hakeem Kae-Kazim", "order": 32}, {"cast_id": 67, "character": "Captain Ammand", "credit_id": "58e2a21ac3a36872af00f9c2", "gender": 0, "id": 70577, "name": "Ghassan Massoud", "order": 33}]'




```python
def convert3(obj):
    L=[]
    counter=0
    for i in ast.literal_eval(obj):
        if counter!=3:
            
           L.append(i['name'])
           counter+=1
            
        else:
            break
        
    return L
```


```python
movies['cast']=movies['cast'].apply(convert3)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['crew'][0]
```




    '[{"credit_id": "52fe48009251416c750aca23", "department": "Editing", "gender": 0, "id": 1721, "job": "Editor", "name": "Stephen E. Rivkin"}, {"credit_id": "539c47ecc3a36810e3001f87", "department": "Art", "gender": 2, "id": 496, "job": "Production Design", "name": "Rick Carter"}, {"credit_id": "54491c89c3a3680fb4001cf7", "department": "Sound", "gender": 0, "id": 900, "job": "Sound Designer", "name": "Christopher Boyes"}, {"credit_id": "54491cb70e0a267480001bd0", "department": "Sound", "gender": 0, "id": 900, "job": "Supervising Sound Editor", "name": "Christopher Boyes"}, {"credit_id": "539c4a4cc3a36810c9002101", "department": "Production", "gender": 1, "id": 1262, "job": "Casting", "name": "Mali Finn"}, {"credit_id": "5544ee3b925141499f0008fc", "department": "Sound", "gender": 2, "id": 1729, "job": "Original Music Composer", "name": "James Horner"}, {"credit_id": "52fe48009251416c750ac9c3", "department": "Directing", "gender": 2, "id": 2710, "job": "Director", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750ac9d9", "department": "Writing", "gender": 2, "id": 2710, "job": "Writer", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca17", "department": "Editing", "gender": 2, "id": 2710, "job": "Editor", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca29", "department": "Production", "gender": 2, "id": 2710, "job": "Producer", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca3f", "department": "Writing", "gender": 2, "id": 2710, "job": "Screenplay", "name": "James Cameron"}, {"credit_id": "539c4987c3a36810ba0021a4", "department": "Art", "gender": 2, "id": 7236, "job": "Art Direction", "name": "Andrew Menzies"}, {"credit_id": "549598c3c3a3686ae9004383", "department": "Visual Effects", "gender": 0, "id": 6690, "job": "Visual Effects Producer", "name": "Jill Brooks"}, {"credit_id": "52fe48009251416c750aca4b", "department": "Production", "gender": 1, "id": 6347, "job": "Casting", "name": "Margery Simkin"}, {"credit_id": "570b6f419251417da70032fe", "department": "Art", "gender": 2, "id": 6878, "job": "Supervising Art Director", "name": "Kevin Ishioka"}, {"credit_id": "5495a0fac3a3686ae9004468", "department": "Sound", "gender": 0, "id": 6883, "job": "Music Editor", "name": "Dick Bernstein"}, {"credit_id": "54959706c3a3686af3003e81", "department": "Sound", "gender": 0, "id": 8159, "job": "Sound Effects Editor", "name": "Shannon Mills"}, {"credit_id": "54491d58c3a3680fb1001ccb", "department": "Sound", "gender": 0, "id": 8160, "job": "Foley", "name": "Dennie Thorpe"}, {"credit_id": "54491d6cc3a3680fa5001b2c", "department": "Sound", "gender": 0, "id": 8163, "job": "Foley", "name": "Jana Vance"}, {"credit_id": "52fe48009251416c750aca57", "department": "Costume & Make-Up", "gender": 1, "id": 8527, "job": "Costume Design", "name": "Deborah Lynn Scott"}, {"credit_id": "52fe48009251416c750aca2f", "department": "Production", "gender": 2, "id": 8529, "job": "Producer", "name": "Jon Landau"}, {"credit_id": "539c4937c3a36810ba002194", "department": "Art", "gender": 0, "id": 9618, "job": "Art Direction", "name": "Sean Haworth"}, {"credit_id": "539c49b6c3a36810c10020e6", "department": "Art", "gender": 1, "id": 12653, "job": "Set Decoration", "name": "Kim Sinclair"}, {"credit_id": "570b6f2f9251413a0e00020d", "department": "Art", "gender": 1, "id": 12653, "job": "Supervising Art Director", "name": "Kim Sinclair"}, {"credit_id": "54491a6c0e0a26748c001b19", "department": "Art", "gender": 2, "id": 14350, "job": "Set Designer", "name": "Richard F. Mays"}, {"credit_id": "56928cf4c3a3684cff0025c4", "department": "Production", "gender": 1, "id": 20294, "job": "Executive Producer", "name": "Laeta Kalogridis"}, {"credit_id": "52fe48009251416c750aca51", "department": "Costume & Make-Up", "gender": 0, "id": 17675, "job": "Costume Design", "name": "Mayes C. Rubeo"}, {"credit_id": "52fe48009251416c750aca11", "department": "Camera", "gender": 2, "id": 18265, "job": "Director of Photography", "name": "Mauro Fiore"}, {"credit_id": "5449194d0e0a26748f001b39", "department": "Art", "gender": 0, "id": 42281, "job": "Set Designer", "name": "Scott Herbertson"}, {"credit_id": "52fe48009251416c750aca05", "department": "Crew", "gender": 0, "id": 42288, "job": "Stunts", "name": "Woody Schultz"}, {"credit_id": "5592aefb92514152de0010f5", "department": "Costume & Make-Up", "gender": 0, "id": 29067, "job": "Makeup Artist", "name": "Linda DeVetta"}, {"credit_id": "5592afa492514152de00112c", "department": "Costume & Make-Up", "gender": 0, "id": 29067, "job": "Hairstylist", "name": "Linda DeVetta"}, {"credit_id": "54959ed592514130fc002e5d", "department": "Camera", "gender": 2, "id": 33302, "job": "Camera Operator", "name": "Richard Bluck"}, {"credit_id": "539c4891c3a36810ba002147", "department": "Art", "gender": 2, "id": 33303, "job": "Art Direction", "name": "Simon Bright"}, {"credit_id": "54959c069251417a81001f3a", "department": "Visual Effects", "gender": 0, "id": 113145, "job": "Visual Effects Supervisor", "name": "Richard Martin"}, {"credit_id": "54959a0dc3a3680ff5002c8d", "department": "Crew", "gender": 2, "id": 58188, "job": "Visual Effects Editor", "name": "Steve R. Moore"}, {"credit_id": "52fe48009251416c750aca1d", "department": "Editing", "gender": 2, "id": 58871, "job": "Editor", "name": "John Refoua"}, {"credit_id": "54491a4dc3a3680fc30018ca", "department": "Art", "gender": 0, "id": 92359, "job": "Set Designer", "name": "Karl J. Martin"}, {"credit_id": "52fe48009251416c750aca35", "department": "Camera", "gender": 1, "id": 72201, "job": "Director of Photography", "name": "Chiling Lin"}, {"credit_id": "52fe48009251416c750ac9ff", "department": "Crew", "gender": 0, "id": 89714, "job": "Stunts", "name": "Ilram Choi"}, {"credit_id": "54959c529251416e2b004394", "department": "Visual Effects", "gender": 2, "id": 93214, "job": "Visual Effects Supervisor", "name": "Steven Quale"}, {"credit_id": "54491edf0e0a267489001c37", "department": "Crew", "gender": 1, "id": 122607, "job": "Dialect Coach", "name": "Carla Meyer"}, {"credit_id": "539c485bc3a368653d001a3a", "department": "Art", "gender": 2, "id": 132585, "job": "Art Direction", "name": "Nick Bassett"}, {"credit_id": "539c4903c3a368653d001a74", "department": "Art", "gender": 0, "id": 132596, "job": "Art Direction", "name": "Jill Cormack"}, {"credit_id": "539c4967c3a368653d001a94", "department": "Art", "gender": 0, "id": 132604, "job": "Art Direction", "name": "Andy McLaren"}, {"credit_id": "52fe48009251416c750aca45", "department": "Crew", "gender": 0, "id": 236696, "job": "Motion Capture Artist", "name": "Terry Notary"}, {"credit_id": "54959e02c3a3680fc60027d2", "department": "Crew", "gender": 2, "id": 956198, "job": "Stunt Coordinator", "name": "Garrett Warren"}, {"credit_id": "54959ca3c3a3686ae300438c", "department": "Visual Effects", "gender": 2, "id": 957874, "job": "Visual Effects Supervisor", "name": "Jonathan Rothbart"}, {"credit_id": "570b6f519251412c74001b2f", "department": "Art", "gender": 0, "id": 957889, "job": "Supervising Art Director", "name": "Stefan Dechant"}, {"credit_id": "570b6f62c3a3680b77007460", "department": "Art", "gender": 2, "id": 959555, "job": "Supervising Art Director", "name": "Todd Cherniawsky"}, {"credit_id": "539c4a3ac3a36810da0021cc", "department": "Production", "gender": 0, "id": 1016177, "job": "Casting", "name": "Miranda Rivers"}, {"credit_id": "539c482cc3a36810c1002062", "department": "Art", "gender": 0, "id": 1032536, "job": "Production Design", "name": "Robert Stromberg"}, {"credit_id": "539c4b65c3a36810c9002125", "department": "Costume & Make-Up", "gender": 2, "id": 1071680, "job": "Costume Design", "name": "John Harding"}, {"credit_id": "54959e6692514130fc002e4e", "department": "Camera", "gender": 0, "id": 1177364, "job": "Steadicam Operator", "name": "Roberto De Angelis"}, {"credit_id": "539c49f1c3a368653d001aac", "department": "Costume & Make-Up", "gender": 2, "id": 1202850, "job": "Makeup Department Head", "name": "Mike Smithson"}, {"credit_id": "5495999ec3a3686ae100460c", "department": "Visual Effects", "gender": 0, "id": 1204668, "job": "Visual Effects Producer", "name": "Alain Lalanne"}, {"credit_id": "54959cdfc3a3681153002729", "department": "Visual Effects", "gender": 0, "id": 1206410, "job": "Visual Effects Supervisor", "name": "Lucas Salton"}, {"credit_id": "549596239251417a81001eae", "department": "Crew", "gender": 0, "id": 1234266, "job": "Post Production Supervisor", "name": "Janace Tashjian"}, {"credit_id": "54959c859251416e1e003efe", "department": "Visual Effects", "gender": 0, "id": 1271932, "job": "Visual Effects Supervisor", "name": "Stephen Rosenbaum"}, {"credit_id": "5592af28c3a368775a00105f", "department": "Costume & Make-Up", "gender": 0, "id": 1310064, "job": "Makeup Artist", "name": "Frankie Karena"}, {"credit_id": "539c4adfc3a36810e300203b", "department": "Costume & Make-Up", "gender": 1, "id": 1319844, "job": "Costume Supervisor", "name": "Lisa Lovaas"}, {"credit_id": "54959b579251416e2b004371", "department": "Visual Effects", "gender": 0, "id": 1327028, "job": "Visual Effects Supervisor", "name": "Jonathan Fawkner"}, {"credit_id": "539c48a7c3a36810b5001fa7", "department": "Art", "gender": 0, "id": 1330561, "job": "Art Direction", "name": "Robert Bavin"}, {"credit_id": "539c4a71c3a36810da0021e0", "department": "Costume & Make-Up", "gender": 0, "id": 1330567, "job": "Costume Supervisor", "name": "Anthony Almaraz"}, {"credit_id": "539c4a8ac3a36810ba0021e4", "department": "Costume & Make-Up", "gender": 0, "id": 1330570, "job": "Costume Supervisor", "name": "Carolyn M. Fenton"}, {"credit_id": "539c4ab6c3a36810da0021f0", "department": "Costume & Make-Up", "gender": 0, "id": 1330574, "job": "Costume Supervisor", "name": "Beth Koenigsberg"}, {"credit_id": "54491ab70e0a267480001ba2", "department": "Art", "gender": 0, "id": 1336191, "job": "Set Designer", "name": "Sam Page"}, {"credit_id": "544919d9c3a3680fc30018bd", "department": "Art", "gender": 0, "id": 1339441, "job": "Set Designer", "name": "Tex Kadonaga"}, {"credit_id": "54491cf50e0a267483001b0c", "department": "Editing", "gender": 0, "id": 1352422, "job": "Dialogue Editor", "name": "Kim Foscato"}, {"credit_id": "544919f40e0a26748c001b09", "department": "Art", "gender": 0, "id": 1352962, "job": "Set Designer", "name": "Tammy S. Lee"}, {"credit_id": "5495a115c3a3680ff5002d71", "department": "Crew", "gender": 0, "id": 1357070, "job": "Transportation Coordinator", "name": "Denny Caira"}, {"credit_id": "5495a12f92514130fc002e94", "department": "Crew", "gender": 0, "id": 1357071, "job": "Transportation Coordinator", "name": "James Waitkus"}, {"credit_id": "5495976fc3a36811530026b0", "department": "Sound", "gender": 0, "id": 1360103, "job": "Supervising Sound Editor", "name": "Addison Teague"}, {"credit_id": "54491837c3a3680fb1001c5a", "department": "Art", "gender": 2, "id": 1376887, "job": "Set Designer", "name": "C. Scott Baker"}, {"credit_id": "54491878c3a3680fb4001c9d", "department": "Art", "gender": 0, "id": 1376888, "job": "Set Designer", "name": "Luke Caska"}, {"credit_id": "544918dac3a3680fa5001ae0", "department": "Art", "gender": 0, "id": 1376889, "job": "Set Designer", "name": "David Chow"}, {"credit_id": "544919110e0a267486001b68", "department": "Art", "gender": 0, "id": 1376890, "job": "Set Designer", "name": "Jonathan Dyer"}, {"credit_id": "54491967c3a3680faa001b5e", "department": "Art", "gender": 0, "id": 1376891, "job": "Set Designer", "name": "Joseph Hiura"}, {"credit_id": "54491997c3a3680fb1001c8a", "department": "Art", "gender": 0, "id": 1376892, "job": "Art Department Coordinator", "name": "Rebecca Jellie"}, {"credit_id": "544919ba0e0a26748f001b42", "department": "Art", "gender": 0, "id": 1376893, "job": "Set Designer", "name": "Robert Andrew Johnson"}, {"credit_id": "54491b1dc3a3680faa001b8c", "department": "Art", "gender": 0, "id": 1376895, "job": "Assistant Art Director", "name": "Mike Stassi"}, {"credit_id": "54491b79c3a3680fbb001826", "department": "Art", "gender": 0, "id": 1376897, "job": "Construction Coordinator", "name": "John Villarino"}, {"credit_id": "54491baec3a3680fb4001ce6", "department": "Art", "gender": 2, "id": 1376898, "job": "Assistant Art Director", "name": "Jeffrey Wisniewski"}, {"credit_id": "54491d2fc3a3680fb4001d07", "department": "Editing", "gender": 0, "id": 1376899, "job": "Dialogue Editor", "name": "Cheryl Nardi"}, {"credit_id": "54491d86c3a3680fa5001b2f", "department": "Editing", "gender": 0, "id": 1376901, "job": "Dialogue Editor", "name": "Marshall Winn"}, {"credit_id": "54491d9dc3a3680faa001bb0", "department": "Sound", "gender": 0, "id": 1376902, "job": "Supervising Sound Editor", "name": "Gwendolyn Yates Whittle"}, {"credit_id": "54491dc10e0a267486001bce", "department": "Sound", "gender": 0, "id": 1376903, "job": "Sound Re-Recording Mixer", "name": "William Stein"}, {"credit_id": "54491f500e0a26747c001c07", "department": "Crew", "gender": 0, "id": 1376909, "job": "Choreographer", "name": "Lula Washington"}, {"credit_id": "549599239251412c4e002a2e", "department": "Visual Effects", "gender": 0, "id": 1391692, "job": "Visual Effects Producer", "name": "Chris Del Conte"}, {"credit_id": "54959d54c3a36831b8001d9a", "department": "Visual Effects", "gender": 2, "id": 1391695, "job": "Visual Effects Supervisor", "name": "R. Christopher White"}, {"credit_id": "54959bdf9251412c4e002a66", "department": "Visual Effects", "gender": 0, "id": 1394070, "job": "Visual Effects Supervisor", "name": "Dan Lemmon"}, {"credit_id": "5495971d92514132ed002922", "department": "Sound", "gender": 0, "id": 1394129, "job": "Sound Effects Editor", "name": "Tim Nielsen"}, {"credit_id": "5592b25792514152cc0011aa", "department": "Crew", "gender": 0, "id": 1394286, "job": "CG Supervisor", "name": "Michael Mulholland"}, {"credit_id": "54959a329251416e2b004355", "department": "Crew", "gender": 0, "id": 1394750, "job": "Visual Effects Editor", "name": "Thomas Nittmann"}, {"credit_id": "54959d6dc3a3686ae9004401", "department": "Visual Effects", "gender": 0, "id": 1394755, "job": "Visual Effects Supervisor", "name": "Edson Williams"}, {"credit_id": "5495a08fc3a3686ae300441c", "department": "Editing", "gender": 0, "id": 1394953, "job": "Digital Intermediate", "name": "Christine Carr"}, {"credit_id": "55402d659251413d6d000249", "department": "Visual Effects", "gender": 0, "id": 1395269, "job": "Visual Effects Supervisor", "name": "John Bruno"}, {"credit_id": "54959e7b9251416e1e003f3e", "department": "Camera", "gender": 0, "id": 1398970, "job": "Steadicam Operator", "name": "David Emmerichs"}, {"credit_id": "54959734c3a3686ae10045e0", "department": "Sound", "gender": 0, "id": 1400906, "job": "Sound Effects Editor", "name": "Christopher Scarabosio"}, {"credit_id": "549595dd92514130fc002d79", "department": "Production", "gender": 0, "id": 1401784, "job": "Production Supervisor", "name": "Jennifer Teves"}, {"credit_id": "549596009251413af70028cc", "department": "Production", "gender": 0, "id": 1401785, "job": "Production Manager", "name": "Brigitte Yorke"}, {"credit_id": "549596e892514130fc002d99", "department": "Sound", "gender": 0, "id": 1401786, "job": "Sound Effects Editor", "name": "Ken Fischer"}, {"credit_id": "549598229251412c4e002a1c", "department": "Crew", "gender": 0, "id": 1401787, "job": "Special Effects Coordinator", "name": "Iain Hutton"}, {"credit_id": "549598349251416e2b00432b", "department": "Crew", "gender": 0, "id": 1401788, "job": "Special Effects Coordinator", "name": "Steve Ingram"}, {"credit_id": "54959905c3a3686ae3004324", "department": "Visual Effects", "gender": 0, "id": 1401789, "job": "Visual Effects Producer", "name": "Joyce Cox"}, {"credit_id": "5495994b92514132ed002951", "department": "Visual Effects", "gender": 0, "id": 1401790, "job": "Visual Effects Producer", "name": "Jenny Foster"}, {"credit_id": "549599cbc3a3686ae1004613", "department": "Crew", "gender": 0, "id": 1401791, "job": "Visual Effects Editor", "name": "Christopher Marino"}, {"credit_id": "549599f2c3a3686ae100461e", "department": "Crew", "gender": 0, "id": 1401792, "job": "Visual Effects Editor", "name": "Jim Milton"}, {"credit_id": "54959a51c3a3686af3003eb5", "department": "Visual Effects", "gender": 0, "id": 1401793, "job": "Visual Effects Producer", "name": "Cyndi Ochs"}, {"credit_id": "54959a7cc3a36811530026f4", "department": "Crew", "gender": 0, "id": 1401794, "job": "Visual Effects Editor", "name": "Lucas Putnam"}, {"credit_id": "54959b91c3a3680ff5002cb4", "department": "Visual Effects", "gender": 0, "id": 1401795, "job": "Visual Effects Supervisor", "name": "Anthony \'Max\' Ivins"}, {"credit_id": "54959bb69251412c4e002a5f", "department": "Visual Effects", "gender": 0, "id": 1401796, "job": "Visual Effects Supervisor", "name": "John Knoll"}, {"credit_id": "54959cbbc3a3686ae3004391", "department": "Visual Effects", "gender": 2, "id": 1401799, "job": "Visual Effects Supervisor", "name": "Eric Saindon"}, {"credit_id": "54959d06c3a3686ae90043f6", "department": "Visual Effects", "gender": 0, "id": 1401800, "job": "Visual Effects Supervisor", "name": "Wayne Stables"}, {"credit_id": "54959d259251416e1e003f11", "department": "Visual Effects", "gender": 0, "id": 1401801, "job": "Visual Effects Supervisor", "name": "David Stinnett"}, {"credit_id": "54959db49251413af7002975", "department": "Visual Effects", "gender": 0, "id": 1401803, "job": "Visual Effects Supervisor", "name": "Guy Williams"}, {"credit_id": "54959de4c3a3681153002750", "department": "Crew", "gender": 0, "id": 1401804, "job": "Stunt Coordinator", "name": "Stuart Thorp"}, {"credit_id": "54959ef2c3a3680fc60027f2", "department": "Lighting", "gender": 0, "id": 1401805, "job": "Best Boy Electric", "name": "Giles Coburn"}, {"credit_id": "54959f07c3a3680fc60027f9", "department": "Camera", "gender": 2, "id": 1401806, "job": "Still Photographer", "name": "Mark Fellman"}, {"credit_id": "54959f47c3a3681153002774", "department": "Lighting", "gender": 0, "id": 1401807, "job": "Lighting Technician", "name": "Scott Sprague"}, {"credit_id": "54959f8cc3a36831b8001df2", "department": "Visual Effects", "gender": 0, "id": 1401808, "job": "Animation Director", "name": "Jeremy Hollobon"}, {"credit_id": "54959fa0c3a36831b8001dfb", "department": "Visual Effects", "gender": 0, "id": 1401809, "job": "Animation Director", "name": "Orlando Meunier"}, {"credit_id": "54959fb6c3a3686af3003f54", "department": "Visual Effects", "gender": 0, "id": 1401810, "job": "Animation Director", "name": "Taisuke Tanimura"}, {"credit_id": "54959fd2c3a36831b8001e02", "department": "Costume & Make-Up", "gender": 0, "id": 1401812, "job": "Set Costumer", "name": "Lilia Mishel Acevedo"}, {"credit_id": "54959ff9c3a3686ae300440c", "department": "Costume & Make-Up", "gender": 0, "id": 1401814, "job": "Set Costumer", "name": "Alejandro M. Hernandez"}, {"credit_id": "5495a0ddc3a3686ae10046fe", "department": "Editing", "gender": 0, "id": 1401815, "job": "Digital Intermediate", "name": "Marvin Hall"}, {"credit_id": "5495a1f7c3a3686ae3004443", "department": "Production", "gender": 0, "id": 1401816, "job": "Publicist", "name": "Judy Alley"}, {"credit_id": "5592b29fc3a36869d100002f", "department": "Crew", "gender": 0, "id": 1418381, "job": "CG Supervisor", "name": "Mike Perry"}, {"credit_id": "5592b23a9251415df8001081", "department": "Crew", "gender": 0, "id": 1426854, "job": "CG Supervisor", "name": "Andrew Morley"}, {"credit_id": "55491e1192514104c40002d8", "department": "Art", "gender": 0, "id": 1438901, "job": "Conceptual Design", "name": "Seth Engstrom"}, {"credit_id": "5525d5809251417276002b06", "department": "Crew", "gender": 0, "id": 1447362, "job": "Visual Effects Art Director", "name": "Eric Oliver"}, {"credit_id": "554427ca925141586500312a", "department": "Visual Effects", "gender": 0, "id": 1447503, "job": "Modeling", "name": "Matsune Suzuki"}, {"credit_id": "551906889251415aab001c88", "department": "Art", "gender": 0, "id": 1447524, "job": "Art Department Manager", "name": "Paul Tobin"}, {"credit_id": "5592af8492514152cc0010de", "department": "Costume & Make-Up", "gender": 0, "id": 1452643, "job": "Hairstylist", "name": "Roxane Griffin"}, {"credit_id": "553d3c109251415852001318", "department": "Lighting", "gender": 0, "id": 1453938, "job": "Lighting Artist", "name": "Arun Ram-Mohan"}, {"credit_id": "5592af4692514152d5001355", "department": "Costume & Make-Up", "gender": 0, "id": 1457305, "job": "Makeup Artist", "name": "Georgia Lockhart-Adams"}, {"credit_id": "5592b2eac3a36877470012a5", "department": "Crew", "gender": 0, "id": 1466035, "job": "CG Supervisor", "name": "Thrain Shadbolt"}, {"credit_id": "5592b032c3a36877450015f1", "department": "Crew", "gender": 0, "id": 1483220, "job": "CG Supervisor", "name": "Brad Alexander"}, {"credit_id": "5592b05592514152d80012f6", "department": "Crew", "gender": 0, "id": 1483221, "job": "CG Supervisor", "name": "Shadi Almassizadeh"}, {"credit_id": "5592b090c3a36877570010b5", "department": "Crew", "gender": 0, "id": 1483222, "job": "CG Supervisor", "name": "Simon Clutterbuck"}, {"credit_id": "5592b0dbc3a368774b00112c", "department": "Crew", "gender": 0, "id": 1483223, "job": "CG Supervisor", "name": "Graeme Demmocks"}, {"credit_id": "5592b0fe92514152db0010c1", "department": "Crew", "gender": 0, "id": 1483224, "job": "CG Supervisor", "name": "Adrian Fernandes"}, {"credit_id": "5592b11f9251415df8001059", "department": "Crew", "gender": 0, "id": 1483225, "job": "CG Supervisor", "name": "Mitch Gates"}, {"credit_id": "5592b15dc3a3687745001645", "department": "Crew", "gender": 0, "id": 1483226, "job": "CG Supervisor", "name": "Jerry Kung"}, {"credit_id": "5592b18e925141645a0004ae", "department": "Crew", "gender": 0, "id": 1483227, "job": "CG Supervisor", "name": "Andy Lomas"}, {"credit_id": "5592b1bfc3a368775d0010e7", "department": "Crew", "gender": 0, "id": 1483228, "job": "CG Supervisor", "name": "Sebastian Marino"}, {"credit_id": "5592b2049251415df8001078", "department": "Crew", "gender": 0, "id": 1483229, "job": "CG Supervisor", "name": "Matthias Menz"}, {"credit_id": "5592b27b92514152d800136a", "department": "Crew", "gender": 0, "id": 1483230, "job": "CG Supervisor", "name": "Sergei Nevshupov"}, {"credit_id": "5592b2c3c3a36869e800003c", "department": "Crew", "gender": 0, "id": 1483231, "job": "CG Supervisor", "name": "Philippe Rebours"}, {"credit_id": "5592b317c3a36877470012af", "department": "Crew", "gender": 0, "id": 1483232, "job": "CG Supervisor", "name": "Michael Takarangi"}, {"credit_id": "5592b345c3a36877470012bb", "department": "Crew", "gender": 0, "id": 1483233, "job": "CG Supervisor", "name": "David Weitzberg"}, {"credit_id": "5592b37cc3a368775100113b", "department": "Crew", "gender": 0, "id": 1483234, "job": "CG Supervisor", "name": "Ben White"}, {"credit_id": "573c8e2f9251413f5d000094", "department": "Crew", "gender": 1, "id": 1621932, "job": "Stunts", "name": "Min Windle"}]'




```python
def fetch_director(obj):
    L=[]
    for i in ast.literal_eval(obj):
        if i['job']=='Director':
            
           L.append(i['name'])
           break
        
    return L
```


```python
movies['crew']=movies['crew'].apply(fetch_director)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[James Cameron]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[Gore Verbinski]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[Sam Mendes]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[Christopher Nolan]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[Andrew Stanton]</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['overview']=movies['overview'].apply(lambda x:x.split())
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[James Cameron]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[Gore Verbinski]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[Sam Mendes]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[Christopher Nolan]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[Andrew Stanton]</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['genres']=movies['genres'].apply(lambda x:[i.replace(" ","") for i in x])
```


```python
movies['keywords']=movies['keywords'].apply(lambda x:[i.replace(" ","") for i in x])
```


```python
movies['cast']=movies['cast'].apply(lambda x:[i.replace(" ","") for i in x])
```


```python
movies['crew']=movies['crew'].apply(lambda x:[i.replace(" ","") for i in x])
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
      <td>[Action, Adventure, Fantasy, ScienceFiction]</td>
      <td>[cultureclash, future, spacewar, spacecolony, ...</td>
      <td>[SamWorthington, ZoeSaldana, SigourneyWeaver]</td>
      <td>[JamesCameron]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drugabuse, exoticisland, eastindiatrad...</td>
      <td>[JohnnyDepp, OrlandoBloom, KeiraKnightley]</td>
      <td>[GoreVerbinski]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, basedonnovel, secretagent, sequel, mi6, ...</td>
      <td>[DanielCraig, ChristophWaltz, LéaSeydoux]</td>
      <td>[SamMendes]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dccomics, crimefighter, terrorist, secretiden...</td>
      <td>[ChristianBale, MichaelCaine, GaryOldman]</td>
      <td>[ChristopherNolan]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
      <td>[Action, Adventure, ScienceFiction]</td>
      <td>[basedonnovel, mars, medallion, spacetravel, p...</td>
      <td>[TaylorKitsch, LynnCollins, SamanthaMorton]</td>
      <td>[AndrewStanton]</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['tags']=movies['overview']+movies['genres']+movies['keywords']+movies['cast']+movies['crew']
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
      <td>[Action, Adventure, Fantasy, ScienceFiction]</td>
      <td>[cultureclash, future, spacewar, spacecolony, ...</td>
      <td>[SamWorthington, ZoeSaldana, SigourneyWeaver]</td>
      <td>[JamesCameron]</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drugabuse, exoticisland, eastindiatrad...</td>
      <td>[JohnnyDepp, OrlandoBloom, KeiraKnightley]</td>
      <td>[GoreVerbinski]</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, basedonnovel, secretagent, sequel, mi6, ...</td>
      <td>[DanielCraig, ChristophWaltz, LéaSeydoux]</td>
      <td>[SamMendes]</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dccomics, crimefighter, terrorist, secretiden...</td>
      <td>[ChristianBale, MichaelCaine, GaryOldman]</td>
      <td>[ChristopherNolan]</td>
      <td>[Following, the, death, of, District, Attorney...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
      <td>[Action, Adventure, ScienceFiction]</td>
      <td>[basedonnovel, mars, medallion, spacetravel, p...</td>
      <td>[TaylorKitsch, LynnCollins, SamanthaMorton]</td>
      <td>[AndrewStanton]</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
    </tr>
  </tbody>
</table>
</div>




```python
new_df=movies[['movie_id','title','tags']]
```


```python
new_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>9367</td>
      <td>El Mariachi</td>
      <td>[El, Mariachi, just, wants, to, play, his, gui...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>72766</td>
      <td>Newlyweds</td>
      <td>[A, newlywed, couple's, honeymoon, is, upended...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>231617</td>
      <td>Signed, Sealed, Delivered</td>
      <td>["Signed,, Sealed,, Delivered", introduces, a,...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>126186</td>
      <td>Shanghai Calling</td>
      <td>[When, ambitious, New, York, attorney, Sam, is...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>25975</td>
      <td>My Date with Drew</td>
      <td>[Ever, since, the, second, grade, when, he, fi...</td>
    </tr>
  </tbody>
</table>
<p>4806 rows × 3 columns</p>
</div>




```python
new_df['tags']=new_df['tags'].apply(lambda x:" ".join(x))
```

    C:\Users\DELL\AppData\Local\Temp/ipykernel_8792/487797088.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      new_df['tags']=new_df['tags'].apply(lambda x:" ".join(x))
    


```python
new_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>9367</td>
      <td>El Mariachi</td>
      <td>El Mariachi just wants to play his guitar and ...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>72766</td>
      <td>Newlyweds</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>231617</td>
      <td>Signed, Sealed, Delivered</td>
      <td>"Signed, Sealed, Delivered" introduces a dedic...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>126186</td>
      <td>Shanghai Calling</td>
      <td>When ambitious New York attorney Sam is sent t...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>25975</td>
      <td>My Date with Drew</td>
      <td>Ever since the second grade when he first saw ...</td>
    </tr>
  </tbody>
</table>
<p>4806 rows × 3 columns</p>
</div>




```python
new_df['tags']=new_df['tags'].apply(lambda x:x.lower())
```

    C:\Users\DELL\AppData\Local\Temp/ipykernel_8792/4224080999.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      new_df['tags']=new_df['tags'].apply(lambda x:x.lower())
    


```python
from sklearn.feature_extraction.text import CountVectorizer
cv=CountVectorizer(max_features=5000,stop_words='english')
```


```python
vectors=cv.fit_transform(new_df['tags']).toarray()
```


```python
vectors
```




    array([[0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           ...,
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0]], dtype=int64)




```python
vectors[0]
```




    array([0, 0, 0, ..., 0, 0, 0], dtype=int64)




```python
cv.get_feature_names()
```

    C:\Users\DELL\anaconda3\lib\site-packages\sklearn\utils\deprecation.py:87: FutureWarning: Function get_feature_names is deprecated; get_feature_names is deprecated in 1.0 and will be removed in 1.2. Please use get_feature_names_out instead.
      warnings.warn(msg, category=FutureWarning)
    




    ['000',
     '007',
     '10',
     '100',
     '11',
     '12',
     '13',
     '14',
     '15',
     '16',
     '17',
     '18',
     '18th',
     '19',
     '1930s',
     '1940s',
     '1950',
     '1950s',
     '1960s',
     '1970s',
     '1980',
     '1980s',
     '1985',
     '1990s',
     '1999',
     '19th',
     '19thcentury',
     '20',
     '200',
     '2009',
     '20th',
     '24',
     '25',
     '30',
     '300',
     '3d',
     '40',
     '50',
     '500',
     '60',
     '60s',
     '70',
     '70s',
     'aaron',
     'aaroneckhart',
     'abandoned',
     'abducted',
     'abigailbreslin',
     'abilities',
     'ability',
     'able',
     'aboard',
     'abuse',
     'abusive',
     'academy',
     'accept',
     'accepted',
     'accepts',
     'access',
     'accident',
     'accidental',
     'accidentally',
     'accompanied',
     'accomplish',
     'account',
     'accountant',
     'accused',
     'ace',
     'achieve',
     'act',
     'acting',
     'action',
     'actionhero',
     'actions',
     'activist',
     'activities',
     'activity',
     'actor',
     'actors',
     'actress',
     'acts',
     'actual',
     'actually',
     'adam',
     'adams',
     'adamsandler',
     'adamshankman',
     'adaptation',
     'adapted',
     'addict',
     'addicted',
     'addiction',
     'adolescence',
     'adolescent',
     'adopt',
     'adopted',
     'adoption',
     'adopts',
     'adrienbrody',
     'adult',
     'adultanimation',
     'adultery',
     'adulthood',
     'adults',
     'advantage',
     'adventure',
     'adventures',
     'advertising',
     'advice',
     'affair',
     'affairs',
     'affection',
     'affections',
     'afghanistan',
     'africa',
     'african',
     'africanamerican',
     'aftercreditsstinger',
     'afterlife',
     'aftermath',
     'age',
     'aged',
     'agedifference',
     'agency',
     'agenda',
     'agent',
     'agents',
     'aggressive',
     'aging',
     'ago',
     'agree',
     'agrees',
     'ahead',
     'aid',
     'aided',
     'aids',
     'ailing',
     'air',
     'airplane',
     'airplanecrash',
     'airport',
     'aka',
     'al',
     'alabama',
     'alan',
     'alaska',
     'albert',
     'alcohol',
     'alcoholic',
     'alcoholism',
     'alecbaldwin',
     'alex',
     'alfredhitchcock',
     'ali',
     'alice',
     'alien',
     'alieninvasion',
     'alienlife',
     'aliens',
     'alike',
     'alive',
     'allen',
     'alliance',
     'allied',
     'allies',
     'allow',
     'allowing',
     'allows',
     'ally',
     'alongside',
     'alpacino',
     'alpha',
     'alter',
     'alternate',
     'alternative',
     'alzheimer',
     'amanda',
     'amandapeet',
     'amandaseyfried',
     'amateur',
     'amazing',
     'ambassador',
     'ambition',
     'ambitious',
     'ambulance',
     'ambush',
     'america',
     'american',
     'americanabroad',
     'americanfootball',
     'americans',
     'amid',
     'amidst',
     'amnesia',
     'amp',
     'amsterdam',
     'amusementpark',
     'amy',
     'amyadams',
     'amysmart',
     'ana',
     'anakin',
     'analyst',
     'anarchiccomedy',
     'ancient',
     'ancientrome',
     'ancientworld',
     'anderson',
     'andiemacdowell',
     'andrew',
     'android',
     'andy',
     'andygarcía',
     'angel',
     'angelabassett',
     'angeles',
     'angelinajolie',
     'angels',
     'anger',
     'anglee',
     'angry',
     'animal',
     'animalattack',
     'animalhorror',
     'animals',
     'animated',
     'animation',
     'anna',
     'annafaris',
     'anne',
     'annehathaway',
     'annemoss',
     'annettebening',
     'annie',
     'anniversary',
     'annual',
     'answer',
     'answers',
     'ant',
     'anthology',
     'anthony',
     'anthonyanderson',
     'anthonyhopkins',
     'anthropomorphism',
     'anti',
     'antics',
     'antihero',
     'antoinefuqua',
     'antoniobanderas',
     'antonyelchin',
     'apart',
     'apartheid',
     'apartment',
     'ape',
     'apes',
     'apocalypse',
     'apocalyptic',
     'apparent',
     'apparently',
     'appear',
     'appears',
     'apple',
     'appointed',
     'apprentice',
     'approach',
     'approaches',
     'approaching',
     'april',
     'aquarium',
     'arab',
     'arch',
     'archaeologist',
     'architect',
     'arctic',
     'area',
     'aren',
     'arena',
     'argument',
     'arise',
     'aristocrat',
     'armed',
     'arms',
     'army',
     'arnold',
     'arnoldschwarzenegger',
     'arrangedmarriage',
     'arrest',
     'arrested',
     'arrival',
     'arrive',
     'arrives',
     'arriving',
     'arrogant',
     'art',
     'arthur',
     'artificialintelligence',
     'artist',
     'artistic',
     'artists',
     'arts',
     'ashley',
     'ashleyjudd',
     'ashtonkutcher',
     'asia',
     'asian',
     'aside',
     'ask',
     'asked',
     'asking',
     'asks',
     'aspirations',
     'aspiring',
     'assassin',
     'assassinate',
     'assassination',
     'assassins',
     'assault',
     'assigned',
     'assignment',
     'assistant',
     'assumes',
     'asteroid',
     'astronaut',
     'astronauts',
     'asylum',
     'athlete',
     'atomicbomb',
     'attack',
     'attacked',
     'attacks',
     'attempt',
     'attempting',
     'attempts',
     'attending',
     'attends',
     'attention',
     'attitude',
     'attorney',
     'attracted',
     'attraction',
     'attractive',
     'audience',
     'audiences',
     'audition',
     'august',
     'aunt',
     'austin',
     'australia',
     'australian',
     'author',
     'authorities',
     'authority',
     'autism',
     'auto',
     'automobileracing',
     'avenge',
     'average',
     'avoid',
     'awaits',
     'awakens',
     'award',
     'away',
     'awry',
     'ax',
     'babe',
     'baby',
     'bachelor',
     'backdrop',
     'backed',
     'background',
     'backgrounds',
     'bad',
     'badly',
     'bag',
     'bahamas',
     'bail',
     'balance',
     'ball',
     'ballet',
     'baltimore',
     'band',
     'bandits',
     'bangkok',
     'banished',
     'bank',
     'banker',
     'bankrobber',
     'bankrobbery',
     'bar',
     'barely',
     'bargained',
     'barn',
     'barney',
     'barry',
     'barrylevinson',
     'bars',
     'base',
     'baseball',
     'based',
     'basedoncomicbook',
     'basedongraphicnovel',
     'basedonnovel',
     'basedonplay',
     'basedonstagemusical',
     'basedontrueevents',
     'basedontruestory',
     'basedontvseries',
     'basedonvideogame',
     'basedonyoungadultnovel',
     'basement',
     'basketball',
     'batman',
     'battle',
     'battlefield',
     'battles',
     'battling',
     'bay',
     'beach',
     'bear',
     'bears',
     'beast',
     'beasts',
     'beat',
     'beating',
     'beautiful',
     'beautifulwoman',
     'beauty',
     'becky',
     'becominganadult',
     'bed',
     'bedroom',
     'beer',
     'befriends',
     'began',
     'begin',
     'beginning',
     'begins',
     'behavior',
     'beings',
     'beliefs',
     'believe',
     'believed',
     'believes',
     'believing',
     'beloved',
     'ben',
     'benaffleck',
     'beneath',
     'benfoster',
     'beniciodeltoro',
     'benjamin',
     'benjaminbratt',
     'benkingsley',
     'bennett',
     'benstiller',
     'bent',
     'berlin',
     'best',
     'bestfriend',
     'bestfriendsinlove',
     'bet',
     'beth',
     'betrayal',
     'betrayed',
     'bettemidler',
     'better',
     'betty',
     'beverly',
     'bible',
     'big',
     'bigger',
     'biggest',
     'biker',
     'bikini',
     'billhader',
     'billionaire',
     'billmurray',
     'billnighy',
     'billpaxton',
     'billpullman',
     'billy',
     'billybobthornton',
     'billycrudup',
     'billycrystal',
     'biography',
     'bird',
     'birth',
     'birthday',
     'bisexual',
     'bishop',
     'bit',
     'bite',
     'bitter',
     'bizarre',
     'black',
     'blackmagic',
     'blackmail',
     'blackpeople',
     'blacksmith',
     'blade',
     'blame',
     'blind',
     'bliss',
     'block',
     'blonde',
     'blood',
     'bloodsplatter',
     'bloodthirsty',
     'bloody',
     'blow',
     'blue',
     'board',
     'boarding',
     'boardingschool',
     'boat',
     'bob',
     'bobby',
     'bobbyfarrelly',
     'bobhoskins',
     'bodies',
     'body',
     'bodyguard',
     'bold',
     'bollywood',
     'bomb',
     'bombing',
     'bond',
     'bonds',
     'bone',
     'book',
     'books',
     'border',
     'bored',
     'boredom',
     'boring',
     'born',
     'boss',
     'boston',
     'botched',
     'bound',
     'boundaries',
     'bounty',
     'bountyhunter',
     'bourne',
     'box',
     'boxer',
     'boxing',
     'boy',
     'boyfriend',
     'boys',
     'bradleycooper',
     'bradpitt',
     'brain',
     'brand',
     'brave',
     'bravery',
     'brazil',
     'brazilian',
     'break',
     'breakdown',
     'breaking',
     'breaks',
     'brendanfraser',
     'brendangleeson',
     'brent',
     'brettratner',
     'brian',
     'briandepalma',
     'bride',
     'bridesmaid',
     'bridge',
     'brief',
     'brielarson',
     'brien',
     'bright',
     'brilliant',
     'bring',
     'bringing',
     'brings',
     'brink',
     'britain',
     'british',
     'britishsecretservice',
     'brittanymurphy',
     'broadway',
     'broke',
     'broken',
     'broker',
     'bronx',
     'brooklyn',
     'brooks',
     'broom',
     'brothel',
     'brother',
     'brotherbrotherrelationship',
     'brothers',
     'brothersisterrelationship',
     'brought',
     'brown',
     'bruce',
     'brucegreenwood',
     'brucewillis',
     'brutal',
     'brutality',
     'brutally',
     'bryansinger',
     'buck',
     'buddies',
     'buddy',
     'buddycomedy',
     'budget',
     'build',
     'building',
     'built',
     'bully',
     'bullying',
     'bumbling',
     'bunny',
     'burglar',
     'buried',
     'bus',
     'bush',
     'business',
     'businessman',
     'bust',
     'busy',
     'butcher',
     'butler',
     'buy',
     'cabin',
     'caesar',
     'cage',
     'cairo',
     'cal',
     'california',
     'called',
     'calls',
     'calvin',
     'camcorder',
     'came',
     'camera',
     'cameraman',
     'cameras',
     'camerondiaz',
     'camp',
     'campaign',
     'campbell',
     'camping',
     'campus',
     'canada',
     'canadian',
     'cancer',
     'candidate',
     'candy',
     'cannibal',
     'capable',
     'capital',
     'capitalism',
     'capt',
     'captain',
     'captive',
     'capture',
     'captured',
     'captures',
     'car',
     'caraccident',
     'carchase',
     'carcrash',
     'card',
     'care',
     'career',
     'carefree',
     'caretaker',
     'caribbean',
     'carjourney',
     'carl',
     'carlagugino',
     'carmen',
     'carol',
     'carolina',
     'carrace',
     'carrie',
     'carry',
     'carrying',
     'cars',
     'cartel',
     'carter',
     'cartoon',
     'caryelwes',
     'case',
     'caseyaffleck',
     'cash',
     'casino',
     'cast',
     'castle',
     'cat',
     'cataclysm',
     'catastrophe',
     'catch',
     'catches',
     'cateblanchett',
     'catherinedeneuve',
     'catherinekeener',
     'catherinezeta',
     'catholic',
     'catholicism',
     'cattle',
     'caught',
     'cause',
     'caused',
     'causes',
     'causing',
     'cavalry',
     'cave',
     'cavemen',
     'celebrate',
     'celebrated',
     'celebration',
     'celebrity',
     'cellphone',
     'cemetery',
     'center',
     'centered',
     'centers',
     'central',
     'centuries',
     'century',
     'ceremony',
     'certain',
     'chain',
     'chainsaw',
     'challenge',
     'challenged',
     'challenges',
     'champion',
     'championship',
     'chance',
     'change',
     'changed',
     'changes',
     'changing',
     'channingtatum',
     'chaos',
     'chaotic',
     'chapter',
     'character',
     'characters',
     'charge',
     'charged',
     'charismatic',
     'charles',
     'charlie',
     'charliesheen',
     'charlizetheron',
     'charlotte',
     'charm',
     'charming',
     'chase',
     'chased',
     'chases',
     'chauffeur',
     'chazzpalminteri',
     'cheating',
     'cheerleader',
     'chef',
     'chemical',
     'cher',
     'chicago',
     'chicken',
     'chief',
     'child',
     'childabuse',
     'childhero',
     'childhood',
     'children',
     'chilling',
     'china',
     'chinese',
     'chip',
     'chiwetelejiofor',
     'chloëgracemoretz',
     'chloësevigny',
     'chocolate',
     'choice',
     'choices',
     'choose',
     'chosen',
     'chowyun',
     'chris',
     'chriscolumbus',
     'chriscooper',
     'chrisevans',
     'chrishemsworth',
     'chrisklein',
     'chrispine',
     'chrisrock',
     'christ',
     'christian',
     'christianbale',
     'christianity',
     'christianslater',
     'christinaapplegate',
     'christinaricci',
     'christine',
     'christmas',
     'christmasparty',
     'christopher',
     'christopherlloyd',
     'christophernolan',
     'christopherplummer',
     'christopherwalken',
     'christophwaltz',
     'chrisweitz',
     'chronicle',
     'chronicles',
     'chuck',
     'church',
     'cia',
     'cigarettesmoking',
     'cillianmurphy',
     'cindy',
     'cinema',
     'circle',
     'circuit',
     'circumstances',
     'circus',
     'cities',
     'citizens',
     'city',
     'civil',
     'civilian',
     'civilization',
     'civilwar',
     'claim',
     'claims',
     'claire',
     'clairedanes',
     'clan',
     'clark',
     'clash',
     'class',
     'classes',
     'classic',
     'classmate',
     'classmates',
     'classroom',
     'claudevandamme',
     'clay',
     'clean',
     'clear',
     'clerk',
     'client',
     'clients',
     'climate',
     'climbing',
     'clinteastwood',
     'clique',
     'cliveowen',
     'clock',
     'clone',
     'cloning',
     'close',
     'closed',
     'closer',
     'club',
     'clubs',
     'clues',
     'clutches',
     'coach',
     'coast',
     'cocaine',
     'code',
     'cody',
     'coffin',
     'cohen',
     'col',
     'cold',
     'coldwar',
     'cole',
     'colin',
     'colinfarrell',
     'colinfirth',
     'collapse',
     'colleague',
     'colleagues',
     'collect',
     'collection',
     'collector',
     'college',
     'collide',
     'collision',
     'colonel',
     'colony',
     'color',
     'colorado',
     'colorful',
     'coma',
     'combat',
     'combined',
     'come',
     'comeback',
     'comedian',
     'comedic',
     'comedy',
     'comes',
     'comet',
     'comfort',
     'comic',
     'comics',
     'coming',
     'comingofage',
     'comingout',
     'command',
     'commander',
     'commercial',
     'commit',
     'commitment',
     'committed',
     'common',
     'communication',
     'community',
     'companion',
     'company',
     'compete',
     'competing',
     'competition',
     'complete',
     'completely',
     'complex',
     'complicated',
     'complications',
     'composer',
     'computer',
     'computervirus',
     'conan',
     'concert',
     'conclusion',
     'condition',
     'confederate',
     'confession',
     'confidence',
     'confident',
     'conflict',
     'confront',
     'confronted',
     'confronts',
     'confused',
     'congress',
     'conman',
     'connected',
     'connection',
     'connell',
     'connor',
     'conquer',
     'conscience',
     'consequences',
     'conservative',
     'considered',
     'conspiracy',
     'conspire',
     'constant',
     'constantly',
     'construction',
     'consumed',
     'contact',
     'contain',
     'contemporary',
     'contend',
     'contest',
     'continue',
     'continues',
     'continuing',
     'contract',
     'control',
     'controlled',
     'controlling',
     'controversial',
     'convention',
     'converge',
     'convict',
     'convicted',
     'convince',
     'convinced',
     'convinces',
     'cook',
     'cooking',
     'cool',
     'cooper',
     'cop',
     'cope',
     'cops',
     'core',
     'corner',
     'corners',
     'corporate',
     'corporation',
     'corpse',
     'corrupt',
     'corruption',
     'cost',
     ...]




```python
import nltk
```


```python
from nltk.stem.porter import PorterStemmer
```


```python
ps=PorterStemmer()
```


```python
def stem(text):
    y=[]
    for i in text.split():
        y.append(ps.stem(i))
        
    return " ".join(y)
    
```


```python
ps.stem('loveness')
```




    'love'




```python
stem('In the 22nd century, a paraplegic Marine is di...')
```




    'in the 22nd century, a parapleg marin is di...'




```python
new_df['tags']=new_df['tags'].apply(stem)
```

    C:\Users\DELL\AppData\Local\Temp/ipykernel_8792/3514595201.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      new_df['tags']=new_df['tags'].apply(stem)
    


```python
new_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>in the 22nd century, a parapleg marin is dispa...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>captain barbossa, long believ to be dead, ha c...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>a cryptic messag from bond’ past send him on a...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>follow the death of district attorney harvey d...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>john carter is a war-weary, former militari ca...</td>
    </tr>
  </tbody>
</table>
</div>




```python
from sklearn.metrics.pairwise import cosine_similarity
```


```python
similiarity=cosine_similarity(vectors)
```


```python
similiarity[1]
```




    array([0.08964215, 1.        , 0.0625    , ..., 0.02635231, 0.        ,
           0.        ])




```python
def recommend(movie):
    movie_index=new_df[new_df['title'] == movie].index[0]
    distance=similiarity[movie_index]
    movie_list=sorted(list(enumerate(distance)),reverse=True,key=lambda x:x[1])[1:6]
    for i in movie_list:
        print(new_df.iloc[i[0]].title)
```


```python
recommend('Avatar')
```

    Titan A.E.
    Small Soldiers
    Independence Day
    Ender's Game
    Aliens vs Predator: Requiem
    


```python
recommend('Batman')
```

    Batman
    Batman & Robin
    The Dark Knight Rises
    Batman Begins
    Batman Returns
    


```python
import pickle 
```


```python
pickle.dump(new_df,open('movies_pkl','wb'))
```


```python
pickle.dump(new_df.to_dict(),open('movies_dicts.pkl','wb'))
```


```python
pickle.dump(similiarity,open('similiarity.pkl','wb'))
```


```python

```


```python

```


```python

```
