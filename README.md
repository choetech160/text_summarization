# Install appropriate libraries


```bash
pip install gensim
pip install wikipedia
pip install -U spacy
python -m spacy download en_core_web_sm
```



# Run the code

```python
from gensim.summarization.summarizer import summarize
from gensim.summarization import keywords
import wikipedia
import spacy

# Get wiki content.
wikisearch = wikipedia.page("Amitabh Bachchan")
wikicontent = wikisearch.content
# nlp = en_core_web_sm.load()
nlp = spacy.load("en_core_web_sm")
doc = nlp(wikicontent)
# Save the wiki content to a file 
# (for reference). 
f = open("wikicontent.txt", "w") 
f.write(wikicontent) 
f.close() 
  
# Summary (0.5% of the original content). 
summ_per = summarize(wikicontent, ratio = 0.05)
print("Percent summary")
print(summ_per)
  
# Summary (200 words)
summ_words = summarize(wikicontent, word_count = 200)
print("Word count summary")
print(summ_words)
```

