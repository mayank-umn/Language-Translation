# Using Textblob

### Install Textblob


```python
#pip install -U textblob
```

    Requirement already up-to-date: textblob in c:\users\mayan\anaconda3\lib\site-packages (0.15.3)
    Requirement already satisfied, skipping upgrade: nltk>=3.1 in c:\users\mayan\anaconda3\lib\site-packages (from textblob) (3.5)
    Requirement already satisfied, skipping upgrade: tqdm in c:\users\mayan\anaconda3\lib\site-packages (from nltk>=3.1->textblob) (4.46.1)
    Requirement already satisfied, skipping upgrade: joblib in c:\users\mayan\anaconda3\lib\site-packages (from nltk>=3.1->textblob) (0.15.1)
    Requirement already satisfied, skipping upgrade: regex in c:\users\mayan\anaconda3\lib\site-packages (from nltk>=3.1->textblob) (2020.5.14)
    Requirement already satisfied, skipping upgrade: click in c:\users\mayan\anaconda3\lib\site-packages (from nltk>=3.1->textblob) (7.1.2)
    Note: you may need to restart the kernel to use updated packages.
    

### Detect Language


```python
from textblob import TextBlob
hi_blob = TextBlob(u'तुम्हारा नाम क्या है')
hi_blob.detect_language()
```




    'hi'




```python
es_blob = TextBlob('Le dejé un mensaje y luego su teléfono se apagó.')
es_blob.detect_language()
```




    'es'



### Translate Hindi text to English


```python
hi_blob.translate(to='en')
```




    TextBlob("what is your name")



### Translate Spanish to English


```python
es_blob.translate(to='en')
```




    TextBlob("I left him a message and then his phone went off.")



# Using Google Translate


```python
#pip install googletrans
```

    Collecting googletrans
      Using cached googletrans-3.0.0.tar.gz (17 kB)
    Collecting httpx==0.13.3
      Using cached httpx-0.13.3-py3-none-any.whl (55 kB)
    Collecting httpcore==0.9.*
      Using cached httpcore-0.9.1-py3-none-any.whl (42 kB)
    Collecting sniffio
      Using cached sniffio-1.1.0-py3-none-any.whl (4.5 kB)
    Requirement already satisfied: chardet==3.* in c:\users\mayan\anaconda3\lib\site-packages (from httpx==0.13.3->googletrans) (3.0.4)
    Collecting hstspreload
      Using cached hstspreload-2020.6.23-py3-none-any.whl (903 kB)
    Requirement already satisfied: idna==2.* in c:\users\mayan\anaconda3\lib\site-packages (from httpx==0.13.3->googletrans) (2.9)
    Requirement already satisfied: certifi in c:\users\mayan\anaconda3\lib\site-packages (from httpx==0.13.3->googletrans) (2020.6.20)
    Collecting rfc3986<2,>=1.3
      Using cached rfc3986-1.4.0-py2.py3-none-any.whl (31 kB)
    Collecting h11<0.10,>=0.8
      Using cached h11-0.9.0-py2.py3-none-any.whl (53 kB)
    Collecting h2==3.*
      Using cached h2-3.2.0-py2.py3-none-any.whl (65 kB)
    Collecting hpack<4,>=3.0
      Using cached hpack-3.0.0-py2.py3-none-any.whl (38 kB)
    Collecting hyperframe<6,>=5.2.0
      Using cached hyperframe-5.2.0-py2.py3-none-any.whl (12 kB)
    Building wheels for collected packages: googletrans
      Building wheel for googletrans (setup.py): started
      Building wheel for googletrans (setup.py): finished with status 'done'
      Created wheel for googletrans: filename=googletrans-3.0.0-py3-none-any.whl size=15740 sha256=aa5ca650c77ea1da0056709616ad7d828d5d8013a9d37a4fc994ecbc69a5e32a
      Stored in directory: c:\users\mayan\appdata\local\pip\cache\wheels\20\da\eb\a54579056f265eede0417df537dd56d3df5b9eb2b25df0003d
    Successfully built googletrans
    Installing collected packages: sniffio, h11, hpack, hyperframe, h2, httpcore, hstspreload, rfc3986, httpx, googletrans
    Successfully installed googletrans-3.0.0 h11-0.9.0 h2-3.2.0 hpack-3.0.0 hstspreload-2020.6.23 httpcore-0.9.1 httpx-0.13.3 hyperframe-5.2.0 rfc3986-1.4.0 sniffio-1.1.0
    Note: you may need to restart the kernel to use updated packages.
    

### Translate Hindi to English


```python
from googletrans import Translator
translator = Translator()
print(translator.translate(u'तुम्हारा नाम क्या है'))
```

    Translated(src=hi, dest=en, text=what is your name, pronunciation=None, extra_data="{'translat...")
    

### Translate Spanish to English


```python
translator = Translator()
print(translator.translate('Me envió un mensaje diciendo que estaba bien.'))
```

    Translated(src=es, dest=en, text=He texted me saying he was fine., pronunciation=He texted me saying he was fine., extra_data="{'translat...")
    

###  Detect language


```python
translator = Translator()
print(translator.detect("Les livres sont les meilleurs amis de l'homme"))
```

    Detected(lang=fr, confidence=1.0)
    


```python
translator = Translator()
print(translator.detect(u'तुम्हारा नाम क्या है'))
```

    Detected(lang=hi, confidence=1.0)
    


```python
translator = Translator()
print(translator.detect('Laura, ¿le envió al acusado otro mensaje esa noche?'))
```

    Detected(lang=es, confidence=1.0)
    

### Translate List of Sentences


```python
translations = translator.translate(['what is your Name', 'how old are you', 'Boston weather is good'], dest='hi')

for translation in translations:
    print(translation.origin, ' -> ', translation.text)
```

    what is your Name  ->  तुम्हारा नाम क्या हे
    how old are you  ->  आपकी उम्र क्या है
    Boston weather is good  ->  बोस्टन का मौसम अच्छा है
    

# Translating Punjabi to English using Indic NLP library


```python
#pip install indic-nlp-library
```


```python
# download the resource
#git clone https://github.com/anoopkunchukuttan/indic_nlp_resources.git
```


```python
# download the repo
#git clone https://github.com/anoopkunchukuttan/indic_nlp_library.git
```


```python
#Setting path for downloaded libraries
import sys
from indicnlp import common

# The path to the local git repo for Indic NLP library
INDIC_NLP_LIB_HOME=r"indic_nlp_library"

# The path to the local git repo for Indic NLP Resources
INDIC_NLP_RESOURCES=r"indic_nlp_resources"

# Add library to Python path
sys.path.append(r'{}\src'.format(INDIC_NLP_LIB_HOME))

# Set environment variable for resources folder
common.set_resources_path(INDIC_NLP_RESOURCES)
```


```python
from indicnlp.tokenize import sentence_tokenize

indic_string="""तो क्या विश्व कप 2019 में मैच का बॉस टॉस है? यानी मैच में हार-जीत में \
टॉस की भूमिका अहम है? आप ऐसा सोच सकते हैं। विश्वकप के अपने-अपने पहले मैच में बुरी तरह हारने वाली एशिया की दो टीमों \
पाकिस्तान और श्रीलंका के कप्तान ने हालांकि अपने हार के पीछे टॉस की दलील तो नहीं दी, लेकिन यह जरूर कहा था कि वह एक अहम टॉस हार गए थे।"""

# Split the sentence, language code "hi" is passed for hindi
sentences=sentence_tokenize.sentence_split(indic_string, lang='hi')

# print the sentences
for t in sentences:
    print(t)
```

    तो क्या विश्व कप 2019 में मैच का बॉस टॉस है?
    यानी मैच में हार-जीत में टॉस की भूमिका अहम है?
    आप ऐसा सोच सकते हैं।
    विश्वकप के अपने-अपने पहले मैच में बुरी तरह हारने वाली एशिया की दो टीमों पाकिस्तान और श्रीलंका के कप्तान ने हालांकि अपने हार के पीछे टॉस की दलील तो नहीं दी, लेकिन यह जरूर कहा था कि वह एक अहम टॉस हार गए थे।
    

### Translate Panjabi to Hindi


```python
from indicnlp.transliterate.unicode_transliterate import UnicodeIndicTransliterator

# Input text "Today the weather is good. Sun is bright and there are no signs of rain. Hence we can play today."
input_text='ਆਜ ਮੌਸਮ ਅਚ੍ਛਾ ਹੈ੤ ਸੂਰਜ ਉਜ੍ਜ੍ਵਲ ਹੈ ਔਰ ਬਾਰਿਸ਼ ਕੇ ਕੋਈ ਸਂਕੇਤ ਨਹੀਂ ਹੈਂ੤ ਇਸਲਿਏ ਹਮ ਆਜ ਖੇਲ ਸਕਤੇ ਹੈਂ!'

# Translate from Panjabi to Hindi
print(UnicodeIndicTransliterator.transliterate(input_text,"pa","hi"))
```

    आज मौसम अच्छा है। सूरज उज्ज्वल है और बारिश के कोई संकेत नहीं हैं। इसलिए हम आज खेल सकते हैं!
    


```python

```
