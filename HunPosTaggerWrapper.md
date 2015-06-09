


## Introduction and Requirements ##

This section explains how to use the HunPosTaggerWrapper Analysis Engine created by Luka Skukan.

Its primary use for us has been annotating documents in Croatian, but it should work with any model file you supply it with.

The HunPosTaggerWrapper Analysis Engine creates tokenization as well as part-of-speech annotations. If used with HeidelTime, it must be present in the workflow and be executed before HeidelTime, as HeidelTime requires at the very least the HunPosTaggerWrapper's sentence tokenization output.

To process documents with HunPosTaggerWrapper, you will need to download a version of it for your operating system from https://code.google.com/p/hunpos.

In order to process documents in Croatian, you should get a copy of the model file (`model.hunpos.mte5.defnpout`) from here http://nlp.ffzg.hr/resources/models/tagging/.


## Environment setup ##

The HunPosTaggerWrapper requires an environment variable to be set in order to find the HunPos binary and model file.

Use this command to set the HUNPOS\_HOME environment variable to the HunPos folder, e.g.:
```
  # for unixoid systems, e.g., Linux and MacOS X
  $ export HUNPOS_HOME=/path/to/hunpos/
  
  # for Windows systems
  > set HUNPOS_HOME=c:\path\to\hunpos\
```

Whenever you run a UIMA pipeline with the HunPosTaggerWrapper in it, this variable needs to be present, so it makes sense to make it permanent by adding it to your .bashrc file or similar.


## Configuration for the UIMA pipeline ##

The HunPosTaggerWrapper's descriptor resides in `$HEIDELTIME_HOME/desc/annotator/HunPosTaggerWrapper.xml`.

Once you add it to your workflow, you can configure the following parameters.

  * **Model\_path**: this must be set to the name of the model tagger file you wish to use, or the full path relative to `HUNPOS_ROOT`. Example: `model.hunpos.mte5.defnpout` or `../model-files/model.hunpos.mte5.defnpout`
  * **Language**: this allows you to set the language file to be annotated.
  * **Annotate\_tokens**: controls whether or not Token Annotations will be added to the pipeline.
  * **Annotate\_sentences**: controls whether or not Sentence Annotations will be added to the pipeline. Note that HeidelTime requires these to perform any work at all.
  * **Annotate\_pos**: controls whether or not part-of-speech information will be added to Token Annotations.