# semantic-text-duplication
This repository provides experiment code and resources to support the paper "Quantifying the Effects of Text Duplication on Semantic Models" by Alexandra Schofield, Laure Thompson, and David Mimno from EMNLP 2017. These experiments were run using Python and Bash scripts on an HTCondor cluster. The code is structured around the Mallet command-line interface; you can download the current version of Mallet 
at https://github.com/mimno/Mallet.

The repository contains the following code:

## bash/
 * `load_into_mallet.sh`: a very basic script to load all .txt files whose path starts with the first argument into Mallet sequence vector files for training. This helps for running several trials of each condition with different random duplication.
 * `lsa_new.sh`: runs trials of LSA across different conditions using the LSA script in the python directory.
 * `remove_exact_duplicates.sh`: a super basic script to get rid of exact duplicate documents (of which there were a few).
 * `train_new.sh`: runs trials of LDA across different conditions using Mallet. Saves a variety of different types of file output from the model; see the Mallet documentation for more information.
 
 ## python/
 * `corpus_deduplicator.py`: Runs the procedures for deleting duplicate documents by unigram frequency and frequent n-grams.
 * `duplicate_writing.py`: Base functions for writing out documents with systematic random duplication for different conditions.
 * `lda_metrics.py`: Base functions for finding the metrics we report in our paper.
 * `lsa.py`: Trains an LSA model.
 * `write_exact_duplicates_mallet.py`: Uses duplicate writing logic for exact document duplication for proportions of the corpus.
 * `write_single_docs_duplicates_mallet.py`: Uses duplicate writing logic for exact document duplication for a single document.
 * `write_template_duplicates_mallet.py`: Uses duplicate writing logic for writing template strings out into documents.

In addition, we also include the list of 30,000 documents we used from each of the Reuters Spanish Language newswire corpus (REUSL) and the NYT Annotated Corpus (NYT). These are in __input_doc_ids/__. To obtain the de-duplicated corpus we use, run the `corpus_deduplicator.py` script on the datasets.

__Mallet__: Andrew K McCallum. 2002. MALLET: a machine learning for language toolkit. Available  at: http://mallet.cs.umass.edu.
__NYT Corpus__: Evan Sandhaus. 2008. The New York Times annotated corpus. _Linguistic Data Consortium_ DVD:LDC2009T19.
__REUSL Corpus__: David amd Gallegos Gustavo  Graff. 1995. Spanish News Text. _Linguistic Data Consortium_ DVD:LDC95T9.
