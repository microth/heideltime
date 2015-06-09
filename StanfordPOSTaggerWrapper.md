


## Introduction and Requirements ##

This section explains how to use the StanfordPOSTaggerWrapper Analysis Engine.

We have been using it primarily to annotate Arabic documents, but the Analysis Engine should work for any tagger parameter file that it is used with.

The StanfordPOSTaggerWrapper Analysis Engine was created to supply tokenization as well as part-of-speech information about a document that enters the UIMA pipeline. If used with HeidelTime, it must be present in the workflow and be executed before HeidelTime, as HeidelTime requires at the very least the StanfordPOSTaggerWrapper's sentence tokenization output.

The StanfordPOSTaggerWrapper leverages the functionality of the Stanford POS Tagger created by the Stanford NLP Group, so in order to use it, you will need to download one of the full packages from here: http://nlp.stanford.edu/software/tagger.shtml. The last tested and confirmed to be working version is 3.3.1.


## Environment setup ##

The StanfordPOSTaggerWrapper requires an environment variable to be set in order to find the Stanford POS Tagger binaries.

Use this command to set the STANFORDTAGGER environment variable to the path where the Stanford POS Tagger .jar file is located, e.g.:
```
  # for unixoid systems, e.g., Linux and MacOS X
  $ export STANFORDTAGGER=/path/to/stanford-postagger-full-2014-01-04/stanford-postagger-2014-01-04.jar
  
  # for Windows systems
  > set STANFORDTAGGER=c:\path\to\stanford-postagger-full-2014-01-04\stanford-postagger-2014-01-04.jar
```

Whenever you run a UIMA pipeline with the StanfordPOSTaggerWrapper in it, this variable needs to be present, so it makes sense to make it permanent by adding it to your .bashrc file or similar.

Additionally, whenever you use the StanfordPOSTaggerWrapper, you will need to source the `$HEIDELTIME_HOME/metadata/setenv` script, which will add this path to the CLASSPATH for execution with Java:
```
  # for unixoid systems, e.g., Linux and MacOS X. This represents BASH syntax:
  $ . $HEIDELTIME_HOME/metadata/setenv
  
  # for Windows systems
  > %HEIDELTIME_HOME%\metadata\setenv.bat
```
If you run HeidelTime together with the StanfordPOSTaggerWrapper, you should only need to perform this action once per pipeline execution.


## Configuration for the UIMA pipeline ##

The StanfordPOSTaggerWrapper's descriptor resides in `$HEIDELTIME_HOME/desc/annotator/StanfordPOSTaggerWrapper.xml`.

Once you add it to your workflow, you can configure the following parameters.

  * **Model\_path**: this must be set to the path that contains the model tagger file you wish to use. Example: /some/path/stanford-postagger-full-2014-01-04/models/arabic.tagger
  * **Config\_path** (optional): this allows you to set an optional configuration file. If it is not required, leave this field empty.
  * **Annotate\_tokens**: controls whether or not Token Annotations will be added to the pipeline.
  * **Annotate\_sentences**: controls whether or not Sentence Annotations will be added to the pipeline. Note that HeidelTime requires these to perform any work at all.
  * **Annotate\_partofspeech**: controls whether or not part-of-speech information will be added to Token Annotations.