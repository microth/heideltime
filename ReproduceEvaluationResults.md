

# Introduction #

On this page, you will find a description how to reproduce **HeidelTime**'s evaluation results reported in our papers listed on [project home](http://code.google.com/p/heideltime/).

To reproduce these evaluation results, download the UIMA **HeidelTime** kit archives ([link](http://code.google.com/p/heideltime/downloads/list)), and all other components needed to run **HeidelTime** in a UIMA pipeline (see the documentation of **HeidelTime** in the UIMA **HeidelTime** kit). Then proceed as follows.


---

# Preparation of folder structure #

To have the evaluation run in an organized fashion, we'll first create a directory structure and then fill it with all of the relevant data.

  1. Create the following directory structure (the top folder will be referred to as `EVALPATH`):
    * `EVALPATH/`
    * `EVALPATH/corpora/`
    * `EVALPATH/evaluation_results/`
    * `EVALPATH/uima_output/`
    * `EVALPATH/uima_workflows/`<br />
  1. Download and extract temporal annotated corpora to `EVALPATH/corpora/`:
    * **ACE Tern 2004** training data is released by the Linguistic Data Consortium (catalogue number [LDC2005T07](http://www.ldc.upenn.edu/Catalog/CatalogEntry.jsp?catalogId=LDC2005T07))
    * **ACE Tern 2005** training data is released by the Linguistic Data Consortium (catalogue number [LDC2006T06](http://www.ldc.upenn.edu/Catalog/CatalogEntry.jsp?catalogId=LDC2006T06))
    * **Arabic corpora** are an annotated subset of the ACE Tern 2005 training data. It is distributed by us through our [institute's research page](http://dbs.ifi.uni-heidelberg.de/index.php?id=129)
    * **TimeBank 1.2** is realeased by the Linguistic Data Consoritum (catalogue number [LDC2006T08](http://www.ldc.upenn.edu/Catalog/CatalogEntry.jsp?catalogId=LDC2006T08))
    * **TempEval-2** training and evaluation sets are released [here](http://timeml.org/site/timebank/timebank.html). Chinese annotations for our improved and clean versions of TE2 are distributed in our [scripts package](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads).
    * **WikiWars** is published [here](http://www.timexportal.info/corpora)
    * **WikiWarsDE** (see our [download page](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads))
    * **WikiWarsVN** (see our [download page](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads))
    * **Time4SMS** (see our [download page](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads))
    * **Time4SCI** (see our [download page](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads))
    * **I-CAB** (see http://ontotext.fbk.eu/i-cab/download-icab.html)
    * **TempEval-3** training (TB/AQ, trainT3) and test (platinum, spanish) corpora (see http://www.cs.york.ac.uk/semeval-2013/task1/) **ATTENTION:** Extract each of the TempEval-3 corpora so that the evaluation files are in `EVALPATH/corpora/TempEval-3/<te3-platinum,TBAQ-cleaned,TE3-test-key,trainT3>/`.
    * **ACE Tern 2004** evaluation data is released by the Linguistic Data Consortium (catalogue number [LDC2010T18](http://www.ldc.upenn.edu/Catalog/CatalogEntry.jsp?catalogId=LDC2010T18))
    * **French TimeBank 1.1** (see https://gforge.inria.fr/projects/fr-timebank/)
    * **AncientTimes** (see our [download page](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads))
    * **WikiWarsHR** is publicly available from [here](http://takelab.fer.hr/data/wikiwarshr/)
    * **EVALITA 2014 Test** corpus is available upon request from the [EVENTI organizers](https://sites.google.com/site/eventievalita2014/data-tools).
  1. Download our preparation and evaluation scripts archive scripts.tar.gz/.zip (see our [download page](http://dbs.ifi.uni-heidelberg.de/index.php?id=form-downloads)) and extract them to EVALPATH, so that these scripts will reside in `EVALPATH/scripts/`.


---

# Preparation of corpora #

Prepare the corpora so that they can be read by the UIMA collection readers and evaluated using the official evaluation scripts:

Go to `EVALPATH/scripts/` and run the `prepare_corpus.sh` script for the corpus that shall be used for evaluation.

> Usage:
```
  bash prepare_corpus.sh <CORPUS_NAME> <EVALPATH>
```

> Valid choices for CORPUS\_NAME:
  * Tern 2004 training data: `tern2004training`
  * Tern 2005 training data: `ace2005training`
  * TimeBank-1.2 corpus: `timebank12`
  * TempEval-2 corpora: `tempeval2eval`, `tempeval2train`, `tempeval2eval-es`, `tempeval2train-es`, `tempeval2eval-it`, `tempeval2train-it`, `tempeval2eval-cn`, `tempeval2train-cn`
  * WikiWars: `wikiwars`
  * TempEval-3: `te3platinum`
  * WikiWarsDE: `wikiwarsde`
  * WikiWarsVN: `wikiwarsvn-te3`
  * WikiWarsHR: `wikiwarshr`
  * Time4SMS: `time4sms`
  * Time4SCI: `time4sci`
  * I-CAB: `icab-training`, `icab-test`
  * French TimeBank 1.1 corpus: `timebank-fr`
  * Arabic corpora: `ace2005trainingArabic`, `arabic_test-50-star`


---

# Create UIMA workflows #

Create UIMA workflows and save them in the `EVALPATH/uima_workflows/` folder.

To create a UIMA workflow, use UIMA's collection processing engine (`runCPE.sh`). Then load the descriptor files of the corresponding components and set the paramters as described below. The components are all part of the UIMA **HeidelTime** kit. In order for the TreeTaggerWrapper Annotator to run, you will need to set up TreeTagger on your system. This is detailed in the project's [readme.txt](https://code.google.com/p/heideltime/source/browse/doc/readme.txt) file.
  * **Tern 2004 training data**
> > save workflow as: `EVALPATH/uima_workflows/tern2004training_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/tern-1.0/data/english/docs_separated/in/`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/tern2004training/keyinline`

  * **ACE 2005 training data**
> > save workflow as: `EVALPATH/uima_workflows/ace2005training_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/ace_2005_td_v7/data/English/docs_separated/in/`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/ace2005training/keyinline`

  * **AncientTimes Arabic**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-ar_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/arabic/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: Standford POS Tagger Wrapper
      * Model\_path: `/path/to/stanfordtagger/models/arabic.tagger`
      * Config\_path: empty
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
    * Analysis Engine: HeidelTime
      * Language: `arabic`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-ar`
      * Convert Timex 3 To 2: `false`

  * **AncientTimes German**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-de_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/german/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `german`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `true`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `german`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-de`

  * **AncientTimes English**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-en_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/english/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-en`

  * **AncientTimes Spanish**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-es_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/spanish/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `spanish`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `spanish`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-es`

  * **AncientTimes French**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-fr_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/french/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `french`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `french`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-fr`

  * **AncientTimes Italian**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-it_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/italian/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `italian`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `italian`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-it`

  * **AncientTimes Dutch**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-nl_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/dutch/untagged`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `dutch`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `dutch`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-nl`

  * **AncientTimes Vietnamese**
> > save workflow as: `EVALPATH/uima_workflows/ancienttimes-vn_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/AncientTimesCorpus/vietnamese/untagged`
    * Analysis Engine: JVnTextProWrapper
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
      * Sent\_model\_path: JVNTEXTPRO\_HOME/models/jvnsensegmenter
      * Word\_model\_path: JVNTEXTPRO\_HOME/models/jvnsegmenter
      * Pos\_model\_path: JVNTEXTPRO\_HOME/models/jvnpostag/maxent
    * Analysis Engine: HeidelTime
      * Language: `vietnamese`
      * Date: `true`
      * Duration: `true`
      * Time: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/ancienttimes-vn`

  * **Arabic Training 203**
> > save workflow as: `EVALPATH/uima_workflows/arabic_training-203_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/ace_2005_td_v7/data/Arabic/docs_separated/training-203/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: Standford POS Tagger Wrapper
      * Model\_path: `/path/to/stanfordtagger/models/arabic.tagger`
      * Config\_path: empty
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
    * Analysis Engine: HeidelTime
      * Language: `arabic`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/arabic_training-203/keyinline`
      * Convert Timex 3 To 2: `false`

  * **Arabic Test 150**
> > save workflow as: `EVALPATH/uima_workflows/arabic_test-150_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/ace_2005_td_v7/data/Arabic/docs_separated/test-150/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: Standford POS Tagger Wrapper
      * Model\_path: `/path/to/stanfordtagger/models/arabic.tagger`
      * Config\_path: empty
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
    * Analysis Engine: HeidelTime
      * Language: `arabic`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/arabic_test-150/keyinline`
      * Convert Timex 3 To 2: `false`

  * **Arabic Test 50**
> > save workflow as: `EVALPATH/uima_workflows/arabic_test-50_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/ace_2005_td_v7/data/Arabic/docs_separated/test-50/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: Standford POS Tagger Wrapper
      * Model\_path: `/path/to/stanfordtagger/models/arabic.tagger`
      * Config\_path: empty
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
    * Analysis Engine: HeidelTime
      * Language: `arabic`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/arabic_test-50/keyinline`
      * Convert Timex 3 To 2: `false`

  * **Arabic Test 50 Star**
> > save workflow as: `EVALPATH/uima_workflows/arabic_test-50-star_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/ace_2005_td_v7/data/Arabic/test-50-star/docs_separated/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: Standford POS Tagger Wrapper
      * Model\_path: `/path/to/stanfordtagger/models/arabic.tagger`
      * Config\_path: empty
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
    * Analysis Engine: HeidelTime
      * Language: `arabic`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/arabic_test-50-star/keyinline`
      * Convert Timex 3 To 2: `false`

  * **Arabic Test 50 Star for TE3-tools evaluation**
> > save workflow as: `EVALPATH/uima_workflows/arabic_test-50-star-te3_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/arabic_test-50-star-te3/`
      * Annotate Creation Time: `true`
    * Analysis Engine: Standford POS Tagger Wrapper
      * Model\_path: `/path/to/stanfordtagger/models/arabic.tagger`
      * Config\_path: empty
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
    * Analysis Engine: HeidelTime
      * Language: `arabic`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/arabic_test-50-star-te3/`
      * Convert Timex 3 To 2: `false`

  * **TimeBank-1.2**
> > save workflow as: `EVALPATH/uima_workflows/timebank12_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/timebank_1_2/data/timex2version/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/timebank12/keyinline`

  * **TempEval-2**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2eval_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/english/entities`
      * Charset: empty
      * Use Spaces As Separators: true
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2eval/temp2files`

  * **TempEval-2 Spanish**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2eval-es_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/spanish/entities`
      * Charset: empty
      * Use Spaces As Separators: true
    * Analysis Engine: TreeTaggerWrapper
      * Language: `spanish`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `spanish`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2eval-es/temp2files`

  * **TempEval-2 Italian**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2eval-it_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/italian/entities`
      * Charset: empty
      * Use Spaces As Separators: true
    * Analysis Engine: TreeTaggerWrapper
      * Language: `italian`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `italian`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2eval-it/temp2files`

  * **TempEval-2 Italian Training for TE3-tools evaluation**
> > save workflow as: `EVALPATH/uima_workflows/te2italian-train_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/training/italian/te3style/input`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `italian`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `italian`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/te2italian-train`

  * **TempEval-2 Italian Test for TE3-tools evaluation**
> > save workflow as: `EVALPATH/uima_workflows/te2italian-eval_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/italian/te3style/input`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `italian`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `italian`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/te2italian-eval`

  * **TempEval-2 Chinese Training**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2train-cn_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/training/chinese/data/`
      * Charset: `GBK`
      * Use Spaces As Separators: `false`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `chinese`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `chinese`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2train-cn/temp2files`

  * **TempEval-2 Chinese Test**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2eval-cn_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/chinese/entities/`
      * Charset: `GBK`
      * Use Spaces As Separators: `false`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `chinese`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `chinese`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2eval-cn/temp2files`

  * **TempEval-2 Chinese Training CLEAN**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2train-cn-clean_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/training/chinese/data-clean/`
      * Charset: `GBK`
      * Use Spaces As Separators: `false`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `chinese`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `chinese`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2train-cn-clean/temp2files`

  * **TempEval-2 Chinese Test CLEAN**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2eval-cn-clean_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/chinese/entities-clean/`
      * Charset: `GBK`
      * Use Spaces As Separators: `false`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `chinese`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `chinese`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2eval-cn-clean/temp2files`

  * **TempEval-2 Chinese Training IMPROVED**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2train-cn-improved_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/training/chinese/data-improved/`
      * Charset: `GBK`
      * Use Spaces As Separators: `false`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `chinese`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `chinese`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2train-cn-improved/temp2files`

  * **TempEval-2 Chinese Test IMPROVED**
> > save workflow as: `EVALPATH/uima_workflows/tempeval2eval-cn-improved_workflow.xml`
    * Collection Reader: TempEval-2 Reader
      * Input Directory: `EVALPATH/corpora/tempeval2-data/test/chinese/entities-improved/`
      * Charset: `GBK`
      * Use Spaces As Separators: `false`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `chinese`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `chinese`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-2 Writer
      * Output Directory: `EVALPATH/uima_output/tempeval2eval-cn-improved/temp2files`

  * **WikiWars**
> > save workflow as: `EVALPATH/uima_workflows/wikiwars_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/WikiWars_20101004/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/wikiwars/keyinline`

  * **WikiWarsDE**
> > save workflow as: `EVALPATH/uima_workflows/wikiwarsde_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/WikiWarsDE_20110412/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `german`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `true`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `german`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/wikiwarsde/keyinline`

  * **WikiWarsVN** (TempEval-3 style)
> > save workflow as: `EVALPATH/uima_workflows/wikiwarsvn-te3_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/WikiWarsVN-TE3/untagged`
    * Analysis Engine: JVnTextProWrapper
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_partofspeech: `true`
      * Sent\_model\_path: JVNTEXTPRO\_HOME/models/jvnsensegmenter
      * Word\_model\_path: JVNTEXTPRO\_HOME/models/jvnsegmenter
      * Pos\_model\_path: JVNTEXTPRO\_HOME/models/jvnpostag/maxent
    * Analysis Engine: HeidelTime
      * Language: `vietnamese`
      * Date: `true`
      * Duration: `true`
      * Time: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/wikiwarsvn-te3`

  * **WikiWarsHR**
> > save workflow as: `EVALPATH/uima_workflows/wikiwarshr_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/TakeLab-WikiWarsHr/timeml`
    * Analysis Engine: HunPosTaggerWrapper
      * Model\_path: `model.hunpos.mte5.defnpout`
      * Language: `croatian`
      * Annotate\_tokens: `true`
      * Annotate\_sentences: `true`
      * Annotate\_pos: `true`
    * Analysis Engine: HeidelTime
      * Language: `croatian`
      * Date: `true`
      * Duration: `true`
      * Time: `true`
      * Set: `true`
      * Type: `narratives`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/wikiwarshr`

  * **Time4SMS**
> > save workflow as: `EVALPATH/uima_workflows/time4sms_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/Time4SMS/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `englishcoll`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `colloquial`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/time4sms/keyinline`

  * **Time4SCI**
> > save workflow as: `EVALPATH/uima_workflows/time4sci_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/Time4SCI/in`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `englishsci`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `scientific`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/time4sci/keyinline`

  * **I-CAB TIMEX 07**
> > save workflow as: `EVALPATH/uima_workflows/icab-test_workflow.xml`
    * Collection Reader: ACE Tern Reader
      * Input Directory: `EVALPATH/corpora/I-CAB_All/TIMEX-07/I-CAB-evalita07-TIMEX-test/docs_separated/in/`
      * Annotate Creation Time: `true`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `italian`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `italian`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: ACE Tern Writer
      * Output Directory: `EVALPATH/uima_output/icab-test/keyinline`

  * **TempEval-3 Platinum**
> > save workflow as: `EVALPATH/uima_workflows/te3platinum_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/TempEval-3/te3-platinum/`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `english`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `english`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/te3platinum`

  * **TempEval-3 Spanish**
> > save workflow as: `EVALPATH/uima_workflows/te3spanish_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/TempEval-3/testES-TaskABC`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `spanish`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `spanish`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/te3spanish`

  * **French TimeBank 1.1**
> > save workflow as: `EVALPATH/uima_workflows/timebank-fr_workflow.xml`
    * Collection Reader: TempEval-3 Reader
      * Input Directory: `EVALPATH/corpora/FR-TimeBank1.1/Data`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `french`
      * Annotate\_tokens: `true`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `true`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `french`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `true`
    * CAS Consumer: TempEval-3 Writer
      * Output Directory: `EVALPATH/uima_output/timebank-fr`

  * **EVALITA 2014 Test**
> > save workflow as: `EVALPATH/uima_workflows/evalita-taskA_workflow.xml`
    * Collection Reader: Eventi 2014 Reader
      * Input Directory: `EVALPATH/corpora/Gold_Standard-EVENTI-2014/Gold_Full_Main/Annotated_Data_Main`
    * Analysis Engine: TreeTaggerWrapper
      * Language: `italian`
      * Annotate\_tokens: `false`
      * Annotate\_partofspeech: `true`
      * Annotate\_sentences: `false`
      * Improvegermansentences: `false`
      * Chinese Tokenizer Path: empty
    * Analysis Engine: HeidelTime
      * Language: `italian`
      * Date: `true`
      * Time: `true`
      * Duration: `true`
      * Set: `true`
      * Type: `news`
      * Convert Durations: `false`
    * Analysis Engine: IntervalTagger
      * Language: italian
      * Annotate\_intervals: `true`
      * Annotate\_interval\_candidates: `false`
    * CAS Consumer: Eventi 2014 Writer
      * Output Directory: `EVALPATH/uima_output/evalita-taskA`


---

# Run UIMA workflows #
Go to `EVALPATH/scripts/` and run the corresponding script depending on the corpus that shall be evaluated. The result file will be written to `EVALPATH/evaluation_results/CORPUS/evaluation_results.txt`

  * **ACE Tern 2004 training data**
```
    bash evaluate_corpus_ternstyle.sh tern2004training EVALPATH
```
  * **ACE 2005 training data**
```
    bash evaluate_corpus_ternstyle.sh ace2005training EVALPATH
```
  * **Arabic corpora:**
```
    bash evaluate_corpus_ternstyle.sh arabic_training-203 EVALPATH
    bash evaluate_corpus_ternstyle.sh arabic_test-150 EVALPATH
    bash evaluate_corpus_ternstyle.sh arabic_test-50 EVALPATH
    bash evaluate_corpus_ternstyle.sh arabic_test-50-star EVALPATH
    bash evaluate_corpus_tempeval3style.sh arabic_test-50-star-te3 EVALPATH
```
  * **TimeBank-1.2**
```
    bash evaluate_corpus_ternstyle.sh timebank12 EVALPATH
```
  * **TempEval-2**
```
    bash evaluate_corpus_tempeval2style.sh tempeval2eval EVALPATH
```
  * **TempEval-2 Spanish**
```
    bash evaluate_corpus_tempeval2style.sh tempeval2eval-es EVALPATH
```
  * **TempEval-2 Italian**
```
    bash evaluate_corpus_tempeval2style.sh tempeval2eval-it EVALPATH
```
  * **TempEval-2 Italian Training with TempEval-3 evaluation scripts**
```
    bash evaluate_corpus_tempeval3style.sh te2italian-train EVALPATH
```
  * **TempEval-2 Italian Eval with TempEval-3 evaluation scripts**
```
    bash evaluate_corpus_tempeval3style.sh te2italian-eval EVALPATH
```
  * **TempEval-2 Chinese**
```
    bash evaluate_corpus_tempeval2style.sh tempeval2train-cn EVALPATH
    bash evaluate_corpus_tempeval2style.sh tempeval2eval-cn EVALPATH
    bash evaluate_corpus_tempeval2style.sh tempeval2train-cn-clean EVALPATH
    bash evaluate_corpus_tempeval2style.sh tempeval2eval-cn-clean EVALPATH
    bash evaluate_corpus_tempeval2style.sh tempeval2train-cn-improved EVALPATH
    bash evaluate_corpus_tempeval2style.sh tempeval2eval-cn-improved EVALPATH
```
  * **WikiWars**
```
    bash evaluate_corpus_ternstyle.sh wikiwars EVALPATH
```
  * **WikiWarsDE**
```
    bash evaluate_corpus_ternstyle.sh wikiwarsde EVALPATH
```
  * **WikiWarsVN**
```
    bash evaluate_corpus_tempeval3style.sh wikiwarsvn-te3 EVALPATH
```
  * **WikiWarsHR**
```
    bash evaluate_corpus_tempeval3style.sh wikiwarshr EVALPATH
```
  * **Time4SMS**
```
    bash evaluate_corpus_ternstyle.sh time4sms EVALPATH
```
  * **Time4SCI**
```
    bash evaluate_corpus_ternstyle.sh time4sci EVALPATH
```
  * **I-CAB**
```
    bash evaluate_corpus_ternstyle.sh icab-test EVALPATH
```
  * **TempEval-3 Platinum**
```
    bash evaluate_corpus_tempeval3style.sh te3platinum EVALPATH
```
  * **TempEval-3 Spanish**
```
    bash evaluate_corpus_tempeval3style.sh te3spanish EVALPATH
```
  * **French TimeBank 1.1**
```
    bash evaluate_corpus_tempeval3style.sh timebank-fr EVALPATH
```
  * **EVALITA 2014 Test**
```
    bash evaluate_corpus_evalitastyle.sh evalita-taskA EVALPATH
```
  * **AncientTimes** corpora
```
    bash evaluate_corpus_tempeval3style.sh ancienttimes-vn EVALPATH
    bash evaluate_corpus_tempeval3style.sh ancienttimes-nl EVALPATH
    bash evaluate_corpus_tempeval3style.sh ancienttimes-fr EVALPATH
    bash evaluate_corpus_tempeval3style.sh ancienttimes-it EVALPATH
    bash evaluate_corpus_tempeval3style.sh ancienttimes-en EVALPATH
    bash evaluate_corpus_tempeval3style.sh ancienttimes-de EVALPATH
    bash evaluate_corpus_tempeval3style.sh ancienttimes-es EVALPATH
```


---

# Compare results #

The evaluation results produced should be similar to the ones described in our papers "Multilingual Cross-domain Temporal Tagging" ([pdf](http://www.springerlink.com/content/64767752451075k8/) [bibtex](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/stroetgen_bib.html#LREjournal2012)) and "Temporal Tagging on Different Domains: Challenges, Strategies, and Gold Standards" ([pdf](http://www.lrec-conf.org/proceedings/lrec2012/pdf/425_Paper.pdf) [bibtex](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/stroetgen_bib.html#LREC2012)), "Chinese Temporal Tagging with HeidelTime" ([pdf](http://www.aclweb.org/anthology/E/E14/E14-4026.pdf) [bibtex](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/stroetgen_bib.html#EACL2014)), "Time for More Languages: Temporal Tagging of Arabic, Italian, Spanish, and Vietnamese" ([pdf](http://dl.acm.org/authorize?6981239) [bibtex](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/stroetgen_bib.html#TALIPjournal2014)) and "Extending HeidelTime for Temporal Expressions Referring to Historic Dates". Alternatively, you can always find the current evaluation results on [this](EvaluationResults.md) wiki page.

Please note that deviations from those numbers can arise from different tokenization/pos/sentence-taggers and experimental development versions of HeidelTime.