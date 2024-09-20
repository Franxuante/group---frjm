## Assignment 3

**TU Delft and WUR**<br>
**Q1 2024**<br>
**Instructor:** Theodoros Chatzivasileiadis <br>
**Instructor:** Hans Hoogenboom <br>
**TA:** Ka Yi Chua <br>
**[Metropolitan Data 1](https://jhoogenboom.github.io/spatial-data-science/_index.html)** <br>



__This homework assignment document will guide you through five tasks in cleaning your data.__

1. Reading and Summarizing the Data.
2. Subsetting the Data.
3. Manage Missing Data.
4. Shape the Data.
5. Saving the Results. 

# NB: From now on you should submit 1) your notebook with the answers, remember that comments are good practice, 2) a working Git page with your assignment

## Exercise 1: Loading the data:

- Load the `goodreads.csv` file into Python
- Explore it by looking at first and last 5 rows
- Change the column names to `["rating", 'review_count', 'isbn', 'booktype','author_url', 'year', 'genre_urls', 'dir','rating_count', 'name']`




```python
import pandas as pd

f = "C:/Users/rembr/Desktop/DATA 1 folders/Assignment 3/data/goodreads.csv"
g = "goodreads.csv"

db = pd.read_csv(f, engine="python") 
db.head() 
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
      <th>4.40</th>
      <th>136455</th>
      <th>0439023483</th>
      <th>good_reads:book</th>
      <th>https://www.goodreads.com/author/show/153394.Suzanne_Collins</th>
      <th>2008</th>
      <th>/genres/young-adult|/genres/science-fiction|/genres/dystopia|/genres/fantasy|/genres/science-fiction|/genres/romance|/genres/adventure|/genres/book-club|/genres/young-adult|/genres/teen|/genres/apocalyptic|/genres/post-apocalyptic|/genres/action</th>
      <th>dir01/2767052-the-hunger-games.html</th>
      <th>2958974</th>
      <th>The Hunger Games (The Hunger Games, #1)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4.41</td>
      <td>16648.0</td>
      <td>0439358078</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/1077326....</td>
      <td>2003.0</td>
      <td>/genres/fantasy|/genres/young-adult|/genres/fi...</td>
      <td>dir01/2.Harry_Potter_and_the_Order_of_the_Phoe...</td>
      <td>1284478.0</td>
      <td>Harry Potter and the Order of the Phoenix (Har...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3.56</td>
      <td>85746.0</td>
      <td>0316015849</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/941441.S...</td>
      <td>2005.0</td>
      <td>/genres/young-adult|/genres/fantasy|/genres/ro...</td>
      <td>dir01/41865.Twilight.html</td>
      <td>2579564.0</td>
      <td>Twilight (Twilight, #1)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.23</td>
      <td>47906.0</td>
      <td>0061120081</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/1825.Har...</td>
      <td>1960.0</td>
      <td>/genres/classics|/genres/fiction|/genres/histo...</td>
      <td>dir01/2657.To_Kill_a_Mockingbird.html</td>
      <td>2078123.0</td>
      <td>To Kill a Mockingbird</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.23</td>
      <td>34772.0</td>
      <td>0679783261</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/1265.Jan...</td>
      <td>1813.0</td>
      <td>/genres/classics|/genres/fiction|/genres/roman...</td>
      <td>dir01/1885.Pride_and_Prejudice.html</td>
      <td>1388992.0</td>
      <td>Pride and Prejudice</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4.25</td>
      <td>12363.0</td>
      <td>0446675539</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/11081.Ma...</td>
      <td>1936.0</td>
      <td>/genres/classics|/genres/historical-fiction|/g...</td>
      <td>dir01/18405.Gone_with_the_Wind.html</td>
      <td>645470.0</td>
      <td>Gone with the Wind</td>
    </tr>
  </tbody>
</table>
</div>




```python
db.tail()
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
      <th>4.40</th>
      <th>136455</th>
      <th>0439023483</th>
      <th>good_reads:book</th>
      <th>https://www.goodreads.com/author/show/153394.Suzanne_Collins</th>
      <th>2008</th>
      <th>/genres/young-adult|/genres/science-fiction|/genres/dystopia|/genres/fantasy|/genres/science-fiction|/genres/romance|/genres/adventure|/genres/book-club|/genres/young-adult|/genres/teen|/genres/apocalyptic|/genres/post-apocalyptic|/genres/action</th>
      <th>dir01/2767052-the-hunger-games.html</th>
      <th>2958974</th>
      <th>The Hunger Games (The Hunger Games, #1)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5994</th>
      <td>4.17</td>
      <td>2226.0</td>
      <td>0767913736</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/44565.Ca...</td>
      <td>2005.0</td>
      <td>/genres/history|/genres/non-fiction|/genres/bi...</td>
      <td>dir60/78508.The_River_of_Doubt.html</td>
      <td>16618.0</td>
      <td>The River of Doubt</td>
    </tr>
    <tr>
      <th>5995</th>
      <td>3.99</td>
      <td>775.0</td>
      <td>1416909427</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/151371.J...</td>
      <td>2006.0</td>
      <td>/genres/young-adult|/genres/realistic-fiction|...</td>
      <td>dir60/259068.Shug.html</td>
      <td>6179.0</td>
      <td>Shug</td>
    </tr>
    <tr>
      <th>5996</th>
      <td>3.78</td>
      <td>540.0</td>
      <td>1620612321</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/5761314....</td>
      <td>2012.0</td>
      <td>/genres/contemporary|/genres/romance|/genres/y...</td>
      <td>dir60/13503247-flawed.html</td>
      <td>2971.0</td>
      <td>Flawed</td>
    </tr>
    <tr>
      <th>5997</th>
      <td>3.91</td>
      <td>281.0</td>
      <td>NaN</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/1201952....</td>
      <td>2006.0</td>
      <td>/genres/religion|/genres/islam|/genres/religio...</td>
      <td>dir60/2750008.html</td>
      <td>3083.0</td>
      <td>Ø£Ø³Ø¹Ø¯ Ø§ÙØ±Ø£Ø© ÙÙ Ø§ÙØ¹Ø§ÙÙ</td>
    </tr>
    <tr>
      <th>5998</th>
      <td>4.35</td>
      <td>61.0</td>
      <td>0786929081</td>
      <td>good_reads:book</td>
      <td>https://www.goodreads.com/author/show/1023510....</td>
      <td>2001.0</td>
      <td>/genres/fiction|/genres/fantasy|/genres/magic|...</td>
      <td>dir60/66677.Legacy_of_the_Drow_Collector_s_Edi...</td>
      <td>3982.0</td>
      <td>Legacy of the Drow Collector's Edition (Legacy...</td>
    </tr>
  </tbody>
</table>
</div>




```python
db.columns = ["rating", 'review_count', 'isbn', 'booktype','author_url', 'year', 'genre_urls', 'dir','rating_count', 'name']
print(db)
```

          rating  review_count        isbn         booktype  \
    0       4.41       16648.0  0439358078  good_reads:book   
    1       3.56       85746.0  0316015849  good_reads:book   
    2       4.23       47906.0  0061120081  good_reads:book   
    3       4.23       34772.0  0679783261  good_reads:book   
    4       4.25       12363.0  0446675539  good_reads:book   
    ...      ...           ...         ...              ...   
    5994    4.17        2226.0  0767913736  good_reads:book   
    5995    3.99         775.0  1416909427  good_reads:book   
    5996    3.78         540.0  1620612321  good_reads:book   
    5997    3.91         281.0         NaN  good_reads:book   
    5998    4.35          61.0  0786929081  good_reads:book   
    
                                                 author_url    year  \
    0     https://www.goodreads.com/author/show/1077326....  2003.0   
    1     https://www.goodreads.com/author/show/941441.S...  2005.0   
    2     https://www.goodreads.com/author/show/1825.Har...  1960.0   
    3     https://www.goodreads.com/author/show/1265.Jan...  1813.0   
    4     https://www.goodreads.com/author/show/11081.Ma...  1936.0   
    ...                                                 ...     ...   
    5994  https://www.goodreads.com/author/show/44565.Ca...  2005.0   
    5995  https://www.goodreads.com/author/show/151371.J...  2006.0   
    5996  https://www.goodreads.com/author/show/5761314....  2012.0   
    5997  https://www.goodreads.com/author/show/1201952....  2006.0   
    5998  https://www.goodreads.com/author/show/1023510....  2001.0   
    
                                                 genre_urls  \
    0     /genres/fantasy|/genres/young-adult|/genres/fi...   
    1     /genres/young-adult|/genres/fantasy|/genres/ro...   
    2     /genres/classics|/genres/fiction|/genres/histo...   
    3     /genres/classics|/genres/fiction|/genres/roman...   
    4     /genres/classics|/genres/historical-fiction|/g...   
    ...                                                 ...   
    5994  /genres/history|/genres/non-fiction|/genres/bi...   
    5995  /genres/young-adult|/genres/realistic-fiction|...   
    5996  /genres/contemporary|/genres/romance|/genres/y...   
    5997  /genres/religion|/genres/islam|/genres/religio...   
    5998  /genres/fiction|/genres/fantasy|/genres/magic|...   
    
                                                        dir  rating_count  \
    0     dir01/2.Harry_Potter_and_the_Order_of_the_Phoe...     1284478.0   
    1                             dir01/41865.Twilight.html     2579564.0   
    2                 dir01/2657.To_Kill_a_Mockingbird.html     2078123.0   
    3                   dir01/1885.Pride_and_Prejudice.html     1388992.0   
    4                   dir01/18405.Gone_with_the_Wind.html      645470.0   
    ...                                                 ...           ...   
    5994                dir60/78508.The_River_of_Doubt.html       16618.0   
    5995                             dir60/259068.Shug.html        6179.0   
    5996                         dir60/13503247-flawed.html        2971.0   
    5997                                 dir60/2750008.html        3083.0   
    5998  dir60/66677.Legacy_of_the_Drow_Collector_s_Edi...        3982.0   
    
                                                       name  
    0     Harry Potter and the Order of the Phoenix (Har...  
    1                               Twilight (Twilight, #1)  
    2                                 To Kill a Mockingbird  
    3                                   Pride and Prejudice  
    4                                    Gone with the Wind  
    ...                                                 ...  
    5994                                 The River of Doubt  
    5995                                               Shug  
    5996                                             Flawed  
    5997              Ø£Ø³Ø¹Ø¯ Ø§ÙØ±Ø£Ø© ÙÙ Ø§ÙØ¹Ø§ÙÙ  
    5998  Legacy of the Drow Collector's Edition (Legacy...  
    
    [5999 rows x 10 columns]
    

## Exercise 2: Subsetting the data

- Subset the data by creating new dataframe only with `["rating", 'isbn', 'author_url', 'year', 'genre_urls', 'name']`


```python
db_2 = db.drop(columns = ['review_count', 'booktype', 'dir', 'rating_count'])
print(db_2) #print for check
```

          rating        isbn                                         author_url  \
    0       4.41  0439358078  https://www.goodreads.com/author/show/1077326....   
    1       3.56  0316015849  https://www.goodreads.com/author/show/941441.S...   
    2       4.23  0061120081  https://www.goodreads.com/author/show/1825.Har...   
    3       4.23  0679783261  https://www.goodreads.com/author/show/1265.Jan...   
    4       4.25  0446675539  https://www.goodreads.com/author/show/11081.Ma...   
    ...      ...         ...                                                ...   
    5994    4.17  0767913736  https://www.goodreads.com/author/show/44565.Ca...   
    5995    3.99  1416909427  https://www.goodreads.com/author/show/151371.J...   
    5996    3.78  1620612321  https://www.goodreads.com/author/show/5761314....   
    5997    3.91         NaN  https://www.goodreads.com/author/show/1201952....   
    5998    4.35  0786929081  https://www.goodreads.com/author/show/1023510....   
    
            year                                         genre_urls  \
    0     2003.0  /genres/fantasy|/genres/young-adult|/genres/fi...   
    1     2005.0  /genres/young-adult|/genres/fantasy|/genres/ro...   
    2     1960.0  /genres/classics|/genres/fiction|/genres/histo...   
    3     1813.0  /genres/classics|/genres/fiction|/genres/roman...   
    4     1936.0  /genres/classics|/genres/historical-fiction|/g...   
    ...      ...                                                ...   
    5994  2005.0  /genres/history|/genres/non-fiction|/genres/bi...   
    5995  2006.0  /genres/young-adult|/genres/realistic-fiction|...   
    5996  2012.0  /genres/contemporary|/genres/romance|/genres/y...   
    5997  2006.0  /genres/religion|/genres/islam|/genres/religio...   
    5998  2001.0  /genres/fiction|/genres/fantasy|/genres/magic|...   
    
                                                       name  
    0     Harry Potter and the Order of the Phoenix (Har...  
    1                               Twilight (Twilight, #1)  
    2                                 To Kill a Mockingbird  
    3                                   Pride and Prejudice  
    4                                    Gone with the Wind  
    ...                                                 ...  
    5994                                 The River of Doubt  
    5995                                               Shug  
    5996                                             Flawed  
    5997              Ø£Ø³Ø¹Ø¯ Ø§ÙØ±Ø£Ø© ÙÙ Ø§ÙØ¹Ø§ÙÙ  
    5998  Legacy of the Drow Collector's Edition (Legacy...  
    
    [5999 rows x 6 columns]
    

## Exercise 3: Manage Missing Data
We’ve got a number of ways in general of dealing with missing data. These involve

1. Dropping off cases (or rows) in the data with any missing variables
2. Excluding variables in the data with any missing data 
3. Selectively choosing indicators with only a limited amount of missing data
4. Replacing missing variables with averages, or other representative values
5. Creating a separate model to predict missing data

- Count the missing values in each column
- Manage the missing values (delete or replace values or leave them as they are) and briefly explain your choice for each column



```python
# Showing the missing values
missing = db_2.isnull().sum()
print(missing)
```

    rating          2
    isbn          477
    author_url      2
    year            7
    genre_urls     62
    name            2
    dtype: int64
    


```python
# When cleaning up the data it is important to keep in mind what you want to research later on. 
# In 6 & 7 the number of reveiws and the reviews itself will be most important.
# since the column 'isbn' has the most values missing and is not needed this column needs to be dropped. The same goes for genre url's.

db_3 = db_2.drop(columns = ['isbn'])

# After that we can delete all the rows where data is missing.
# This will at max be 1,3% of the total rows amount which leaves us with enough data for a good analysis later

db_4 = db_3.dropna(axis= 0, how='any')
missing = db_4.isnull().sum()
print(missing) #check if the missing data is indeed removed 
```

    rating        0
    author_url    0
    year          0
    genre_urls    0
    name          0
    dtype: int64
    

## Exercise 4: Shape the data
- Parse the `author_url` to create new column named `author`
- Sort the data by putting higher rates go first. If there are overlapping rates, try to put earlier years go first.
- **(Stretch Goal)** Examine how many books were published at each year and find lowest, highest rate of each year. 


```python
# The first step it to define a function that parses the name from the url in a format that is nice to work with

def get_author(url):
    if isinstance(url, str):

        name = url.split('/')[-1].split('.')[1:][0]
    
        return name
    else: # just for safety because there are no rows missing 'author_url' values
        return None 

db_4['author'] = db_4.author_url.map(get_author)
db_5 = db_4.drop(columns = ['author_url']) # drop this column to make the table more readable

#output check
print(db_5)
```

          rating    year                                         genre_urls  \
    0       4.41  2003.0  /genres/fantasy|/genres/young-adult|/genres/fi...   
    1       3.56  2005.0  /genres/young-adult|/genres/fantasy|/genres/ro...   
    2       4.23  1960.0  /genres/classics|/genres/fiction|/genres/histo...   
    3       4.23  1813.0  /genres/classics|/genres/fiction|/genres/roman...   
    4       4.25  1936.0  /genres/classics|/genres/historical-fiction|/g...   
    ...      ...     ...                                                ...   
    5994    4.17  2005.0  /genres/history|/genres/non-fiction|/genres/bi...   
    5995    3.99  2006.0  /genres/young-adult|/genres/realistic-fiction|...   
    5996    3.78  2012.0  /genres/contemporary|/genres/romance|/genres/y...   
    5997    3.91  2006.0  /genres/religion|/genres/islam|/genres/religio...   
    5998    4.35  2001.0  /genres/fiction|/genres/fantasy|/genres/magic|...   
    
                                                       name             author  
    0     Harry Potter and the Order of the Phoenix (Har...        J_K_Rowling  
    1                               Twilight (Twilight, #1)    Stephenie_Meyer  
    2                                 To Kill a Mockingbird         Harper_Lee  
    3                                   Pride and Prejudice        Jane_Austen  
    4                                    Gone with the Wind  Margaret_Mitchell  
    ...                                                 ...                ...  
    5994                                 The River of Doubt    Candice_Millard  
    5995                                               Shug          Jenny_Han  
    5996                                             Flawed       Kate_Avelynn  
    5997              Ø£Ø³Ø¹Ø¯ Ø§ÙØ±Ø£Ø© ÙÙ Ø§ÙØ¹Ø§ÙÙ      A_id_al_Qarni  
    5998  Legacy of the Drow Collector's Edition (Legacy...      R_A_Salvatore  
    
    [5933 rows x 5 columns]
    

    C:\Users\rembr\AppData\Local\Temp\ipykernel_15000\1572354256.py:12: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      db_4['author'] = db_4.author_url.map(get_author)
    


```python
#sorting database by rating and than year with the following function
db_5 = db_5.sort_values(by=['rating', 'year'], ascending=False)

#output check
print(db_5)
```

          rating    year                                         genre_urls  \
    1717    5.00  2014.0                   /genres/poetry|/genres/childrens   
    5563    5.00  2014.0                  /genres/romance|/genres/new-adult   
    3711    4.93  2013.0  /genres/fantasy|/genres/romance|/genres/suspen...   
    3253    4.92  2014.0                                /genres/young-adult   
    910     4.85  2014.0                                    /genres/fiction   
    ...      ...     ...                                                ...   
    5112    3.01  2004.0  /genres/fiction|/genres/womens-fiction|/genres...   
    5843    2.97  1925.0  /genres/history|/genres/non-fiction|/genres/bi...   
    2608    2.90  2013.0  /genres/romance|/genres/realistic-fiction|/gen...   
    5978    2.77  2001.0  /genres/fantasy|/genres/fiction|/genres/myster...   
    3737    2.00  2011.0  /genres/young-adult|/genres/science-fiction|/g...   
    
                                          name                      author  
    1717            An Elephant Is On My House  Othen_Donald_Dale_Cummings  
    5563  Untainted (Photographer Trilogy, #3)              Sarah_Robinson  
    3711                           Blade Heart                 Chris_Lange  
    3253          Blackout (Talisman of El #2)                Alecia_Stone  
    910                     Honor and Polygamy                 Omar_Farhad  
    ...                                    ...                         ...  
    5112             The Jane Austen Book Club            Karen_Joy_Fowler  
    5843                            Mein Kampf                Adolf_Hitler  
    2608              How To Be A Perfect Girl               Mary_Williams  
    5978                                  Lost             Gregory_Maguire  
    3737  Revealing Eden (Save the Pearls, #1)               Victoria_Foyt  
    
    [5933 rows x 5 columns]
    


```python
db_6 = db_5.year.value_counts()
# Since each book has a 'year' attributed to it in the database, this means that each year in de database represents one book.
# We can use the 'value_counts()' function to calculate the frequency of the values in the column 'year'
# this way we now how many books there are per year
# the output of the function also shows the years wwith the most and the least books released
```

    year
    2011.0    369
    2012.0    339
    2010.0    312
    2009.0    294
    2013.0    261
             ... 
    1819.0      1
    1721.0      1
    1140.0      1
    800.0       1
    1748.0      1
    Name: count, Length: 292, dtype: int64
    

## Exercise 5: Saving the results
- Save the cleaned dataframe as 'hw-03-cleaned.csv' in data folder


```python
db_5.to_csv("C:/Users/rembr/Desktop/DATA 1 folders/Assignment 3/data/hw-03-cleaned.csv", index=False, header=True)
```

## Exercise 6: Investigate the relationship between the number of reviews and the average rating for books in the dataset cleaned-goodreads.csv procided.

- Calculate the correlation coefficient. Give me a short definition of this coefficient
- Create a scatter plot showing the relationship between these two features.
- Based on the plot and the correlation, provide a brief interpretation of the relationship.

### Python Tools: Use pandas and numpy for correlation, and matplotlib or seaborn for the scatter plot.


```python
import pandas as pd
import numpy as np
import seaborn as sns

# correlation coefficient that measures linear correlation between two sets of data
d= "C:/Users/rembr/Desktop/DATA 1 folders/Assignment 3/data/cleaned-goodreads.csv"
db_good = pd.read_csv(d, engine = "python")

#calculating correlation coefficient between rating and review count
db_good['rating'].corr(db_good['review_count'])

```




    np.float64(-0.037896372578752904)




```python
# For final notebook figure out plotsize
sns.scatterplot(data=db_good, x='review_count', y='rating')
```




    <Axes: xlabel='review_count', ylabel='rating'>




    
![png](output_19_1.png)
    


# Interpepetation Plot

In the scatterplot we see the review count plotted against the rating. In the plot you see that most books have a very low review count. Furthermore we see from the plot that there is little correlation between rating and review, since most of the dots seem to be distrinuted evenly over the ratings. This is also reflected in the correlation coefficiant calculated since the value is almost equal to 0.


## Exercise 7: Calculate the following descriptive statistics for the numerical features (e.g., number of reviews, average rating, etc.):
- Mean
- Median
- Standard Deviation
- Range
- Create a histogram or box plot for at least one of the numerical features, highlighting any skewness or outliers.
    
### Python Tools: Use pandas for data manipulation and matplotlib or seaborn for visualization.


```python
db_good[['rating', 'review_count', 'rating_count']].median()
```




    rating              4.05
    review_count      936.00
    rating_count    18072.00
    dtype: float64




```python
db_good[['rating', 'review_count', 'rating_count']].describe()
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
      <th>rating</th>
      <th>review_count</th>
      <th>rating_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>5993.000000</td>
      <td>5993.000000</td>
      <td>5.993000e+03</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4.041997</td>
      <td>2374.331220</td>
      <td>5.118390e+04</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.260509</td>
      <td>5493.093328</td>
      <td>1.376493e+05</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.000000</td>
      <td>0.000000</td>
      <td>5.000000e+00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.870000</td>
      <td>390.000000</td>
      <td>7.527000e+03</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4.050000</td>
      <td>936.000000</td>
      <td>1.807200e+04</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4.210000</td>
      <td>2212.000000</td>
      <td>4.294300e+04</td>
    </tr>
    <tr>
      <th>max</th>
      <td>5.000000</td>
      <td>136455.000000</td>
      <td>2.958974e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.histplot(data=db_good, x= 'rating',y=None)

# The mean and the median are almost equal so that means that data of the 'rating' is normally distributed. 
# We also see this in the histogram below since it follows the normal distribution line.
```




    <Axes: xlabel='rating', ylabel='Count'>




    
![png](output_24_1.png)
    



```python
sns.boxplot(data= db_good, x= None, y='rating')

#The boxplot shows that there are some outliers
```




    <Axes: ylabel='rating'>




    
![png](output_25_1.png)
    

