# Cybersecurity Articles Analysis
Applies a pre-trained LLM (_t5-small_) and various NLP methods on Cyber Security news articles



## Executive Summary

Cybersecurity news articles are extracted from a custom built database stored on AWS S3. Each full length article in the dataset is summarized with a pretrained Hugging Face LLM, i.e.,  _t5-small_.

The summarized articles are analyzed by:

1. counting and plotting their frequencies per search keywords  
![Threat Actors](/_pic/threat_actors.png)
![Topics](/_pic/topics.png)

2. a frequency distribution  
![Frequency Distribution](/_pic/frequency_distribution.png)

3. a dispersion plot of the most frequent words  
![Dispersion Plot](/_pic/dispersion_plot.png)




## Technical Details

### 0. Precondtions

#### Libraries
- Create a virtual environment
```Bash
python3 -m venv nlpenv
source nlpenv/bin/activate
```


- Install Pytorch
```Bash
pip install torch
```


- Install the transformer library
```Bash
pip install transformers

pip install pandas
pip install chardet
```

- Install nltk
```Bash
pip install nltk
```

- Install graphical packages
```Bash
pip intall plotly
```

- Install nltk modules
```Python
import nltk
nltk.download('stopwords')
nltk.download('punkt_tab')
nltk.download('wordnet')
nltk.download('averaged_perceptron_tagger_eng')
```

- Update nbformat (used for plot)
```bash
pip install --upgrade nbformat
```


- Plots
```bash
pip install matplotlib
```


- Image exporting as file
```bash
pip install -U kaleido
```

#### Access to Cloud Ressources
The project is run locally and access cloud ressources through VS Code Studio.

### 1. Data Load
Data are loaded from a custom built database of cybersecurity news articles on AWS S3.
As each extraction is split into different parts, the data are aggregated after extraction.

The result is a Pandas Dataframe which contains multiple cybersecurity news articles.

### 2. Summarize Articles
Each full length article in the dataset is summarized with a pretrained Hugging Face LLM, i.e.,  _t5-small_.
The summarized articles are the basis for running further analyses on them (see section below.)

_Note: for simplicity only the first 3000 articles are used._

### 3. Analysis of summarized articles
The articles are first prepared before they are further analyzed with the following steps:
- Tokenization
- Removal of stop words, punctuation, single letter words, words other than verbs

The articles are analyzed by:
- 1. counting and plotting their frequencies per search keywords
- 2. a frequency distribution
- 3. a dispersion plot of the most frequent words