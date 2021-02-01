# nlp-log-analysis

### Importing necessary library
```
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
import string
```
##### These two lines for download is temporary for demo 
##### scaled version of this solution will have all dependencies installed
```
nltk.download('stopwords')
nltk.download('punkt')
```
### Defnining process pipeline function

  #### Tokenization
  ```
  tokens = word_tokenize(text)
  ```
  #### Removing stop-words
  ```
  stop_words = set(stopwords.words('english') + list(string.punctuation))
  filter_words = [word for word in tokens if word not in stop_words]
  ```
  ##### further filteration with custom stop words
  ##### As a scaled solution, we can save these customs stop words to a db
  ##### like my_sql or any other and connect it to a admin dashboard panel 
  ##### where user can add/drop such words further for training/refinement.
  ```
  custom_stop_words = ['server','unknown','reason','amount','everything','fine']
  filter_words = [word for word in filter_words if word not in custom_stop_words]
  ```
  ##### Aggregation
  ```
  output = ' '
  output = output.join(filter_words)
  ```
  ##### Final output
  ```
  print(output)
  ```
### Reading local log file
### This solution is going to evaluate each line for log file
### This processing can be changed as per actual requirement.
```
with open("/content/log1.txt") as f:
  for line in f:
    process_pipeline(line.lower())
```
