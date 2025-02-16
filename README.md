# paper2kg

![](https://img.shields.io/badge/Status-Done-brightgreen.svg)

Generate Knowledge Graph for Paper

# Extractor/Algorithm

- [Ollie](http://knowitall.github.io/ollie/), Java code extracts relation triples which has been integrated into the project.

Notice: BERT-BiLSTM-CRF will be added.

## Files

- paperAPI.py: api entry
- d3.html: visualization demo (You need to replace the 'links' value [line 8, d3.html].)
- toolkit
  - Ollie: triple extractor
  - pdf_parser: pdf2xml
 
## Requirements (python packages)

- uvicorn
- fastapi
- pydantic
- nltk

**Before** using NLTK, you may need to add the following code to the top of readxml.py and text2kg.py

```
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
```

**Once the download is successful, these two lines of code must be removed.**

PS: JAVA environment is required.

## Run

No API: Configure readXML.py and run.

or
```bash
uvicorn paperAPI:app --reload --port 8000 --host 127.0.0.1
```
or
```bash
python paperAPI.py
```

- GET: http://127.0.0.1:8000/paper2kg?paperID=ELG.pdf&confidence=0.6&fine_grain=false

- POST: {"paperID": "ELG.pdf", "confidence": 0.1, "fine_grain": "False"}

- API docs: http://127.0.0.1:8000/docs

## Preview

![](preview.png)

## Word Classes/tags for paper2api

- NNP: proper noun, singular
- NNPS: proper noun, plural
- NN: noun, singular
- NNS: noun, plural
