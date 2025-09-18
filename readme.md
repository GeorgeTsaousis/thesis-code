# POS Tagging Experiments (Spanish)

This workspace contains three Jupyter notebooks implementing and evaluating part-of-speech (POS) tagging on the Spanish CoNLL-2002 dataset using three approaches:

- Rule/statistical backoff tagger with NLTK — [Nltkcode.ipynb](Nltkcode.ipynb)  
  Key symbols: [`backoff_tagger`](Nltkcode.ipynb), [`tagger`](Nltkcode.ipynb), [`pred_tags`](Nltkcode.ipynb), [`gold_tags`](Nltkcode.ipynb), [`execution_time`](Nltkcode.ipynb).

- spaCy pretrained model — [spacycode.ipynb](spacycode.ipynb)  
  Key symbols: [`test_sents`](spacycode.ipynb), [`nlp`](spacycode.ipynb), [`map_conll_to_universal`](spacycode.ipynb), [`pred_tags`](spacycode.ipynb), [`gold_tags_mapped`](spacycode.ipynb), [`execution_time`](spacycode.ipynb).

- Stanza pretrained pipeline — [stanzacode.ipynb](stanzacode.ipynb)  
  Key symbols: [`test_tokenized`](stanzacode.ipynb), [`nlp`](stanzacode.ipynb), [`map_conll_to_universal`](stanzacode.ipynb), [`pred_tags`](stanzacode.ipynb), [`gold_tags_mapped`](stanzacode.ipynb), [`execution_time`](stanzacode.ipynb).


Quick overview
- All notebooks load the CoNLL-2002 Spanish test split via NLTK (`conll2002.tagged_sents`) and compare predicted POS tags to gold tags after mapping the CoNLL tagset to universal POS tags using the notebook-local function [`map_conll_to_universal`](spacycode.ipynb) (also present in the other notebooks).
- Each notebook reports Accuracy, weighted F1, Recall, a full classification report, execution time, top error samples, and a bar plot of the 50 most frequent words.

Requirements
- Python 3.x
- Libraries used (install via pip): nltk, spacy, stanza, scikit-learn, pandas, matplotlib, seaborn
- Additional model downloads:
  - NLTK CoNLL-2002 data: the notebooks call `nltk.download('conll2002')` — see [Nltkcode.ipynb](Nltkcode.ipynb).
  - spaCy Spanish model: install `es_core_news_md` (run `python -m spacy download es_core_news_md`) before running [spacycode.ipynb](spacycode.ipynb).
  - Stanza Spanish models: the notebooks call `stanza.download('es')` — see [stanzacode.ipynb](stanzacode.ipynb).

How to run
1. Open the desired notebook in JupyterLab / Jupyter Notebook or VS Code.
2. Ensure the required packages and models are installed (see "Requirements").
3. Run cells top-to-bottom. Each notebook performs inference on the CoNLL-2002 test set and prints metrics and plots.

Notes & tips
- Mapping function: [`map_conll_to_universal`](spacycode.ipynb) maps the dataset-specific tags (e.g., `NC`, `NP`, `AQ`, ...) to Universal POS tags. Inspect and adjust it if you need different mappings.
- Filtering: notebooks filter out None or unsupported predicted tags before metric computation (see `filtered` logic in [spacycode.ipynb](spacycode.ipynb) and [Nltkcode.ipynb](Nltkcode.ipynb)).
- Performance: reported example metrics and timings are available in notebook outputs (e.g., Accuracy ~0.97 for NLTK, ~0.78 for spaCy, ~0.82 for Stanza in these runs). See the printed reports inside each notebook for full per-tag breakdowns.
