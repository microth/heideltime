


## Introduction and Requirements ##

This section explains how to use the TreeTaggerWrapper Analysis Engine.

The TreeTaggerWrapper Analysis Engine was created to supply tokenization as well as part-of-speech information about a document that enters the UIMA pipeline. If used with HeidelTime, it must always be present in the workflow and be executed before HeidelTime, as HeidelTime requires at the very least the TreeTaggerWrapper's sentence tokenization output.

The TreeTaggerWrapper leverages the functionality of the TreeTagger created by Helmut Schmidt, so in order to use it, you will need to download it from here: http://www.cis.uni-muenchen.de/~schmid/tools/TreeTagger/. Tokenization and POS parameter files exist for many languages. Note that the TreeTaggerWrapper by default requires the UTF-8 versions of parameter files when processing `German`, `Spanish` or `Italian` documents.


## Environment setup ##

The TreeTaggerWrapper requires an environment variable to be set in order to find the TreeTagger binaries.

Use this command to set the TREETAGGER\_HOME environment variable to the path where the TreeTagger is located:
```
  # for unixoid systems, e.g., Linux and MacOS X
  $ export TREETAGGER_HOME=/path/to/treetagger
  
  # for Windows systems
  > set TREETAGGER_HOME=c:\path\to\treetagger
```

Whenever you run a UIMA pipeline with the TreeTaggerWrapper in it, this variable needs to be present, so it makes sense to make it permanent by adding it to your .bashrc file or similar.


## Configuration for the UIMA pipeline ##

The TreeTaggerWrapper's descriptor resides in `$HEIDELTIME_HOME/desc/annotator/TreeTaggerWrapper.xml`.

Once you add it to your workflow, you can configure the following parameters.

  * **Language**: this controls which parameter file the TreeTaggerWrapper will use. By default, the TreeTaggerWrapper uses this format to load parameter files: **`language-name`**.par
  * **Annotate\_tokens**: controls whether or not Token Annotations will be added to the pipeline.
  * **Annotate\_sentences**: controls whether or not Sentence Annotations will be added to the pipeline. Note that HeidelTime requires these to perform any work at all.
  * **Annotate\_partofspeech**: controls whether or not part-of-speech information will be added to Token Annotations.
  * **Improvegermansentences**: performs some improvements on the TreeTagger output when dealing with German documents.
  * **Chinese Tokenizer Path**: Set this to the folder of the Chinese Tokenizer script for the TreeTagger (http://corpus.leeds.ac.uk/tools/zh/) if you're processing Chinese language documents.