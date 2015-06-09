


## Introduction and Requirements ##

This section explains how to use the JVnTextProWrapper Analysis Engine for preprocessing Vietnamese text.

The JVnTextProWrapper Analysis Engine was created to supply tokenization as well as part-of-speech information about a document that enters the UIMA pipeline. If used with HeidelTime, it must be present in the workflow and be executed before HeidelTime, as HeidelTime requires at the very least the JVnTextProWrapper's sentence tokenization output.

The JVnTextProWrapper leverages the functionality of the JVnTextPro tool created by Cam-Tu Nguyen, Xuan-Hieu Phan and Thu-Trang Nguyen, so in order to use it, you will need to download it from here: http://jvntextpro.sourceforge.net/. The last tested and confirmed to be working version is 2.0.


## Environment setup ##

The JVnTextProWrapper requires an environment variable to be set in order to find the binary JVnTextPro class files.

Use this command to set the JVNTEXTPRO\_HOME environment variable to the path where the JVnTextPro bin folder is located, e.g.:
```
  # for unixoid systems, e.g., Linux and MacOS X
  $ export JVNTEXTPRO_HOME=/path/to/JVnTextPro-v.2.0/bin
  
  # for Windows systems
  > set JVNTEXTPRO_HOME=c:\path\to\JVnTextPro-v.2.0\bin
```

Whenever you run a UIMA pipeline with the JVnTextProWrapper in it, this variable needs to be present, so it makes sense to make it permanent by adding it to your .bashrc file or similar.

Additionally, whenever you use the JVnTextProWrapper, you will need to source the `$HEIDELTIME_HOME/metadata/setenv` script, which will add this path to the CLASSPATH for execution with Java:
```
  # for unixoid systems, e.g., Linux and MacOS X. This represents BASH syntax:
  $ . $HEIDELTIME_HOME/metadata/setenv
  
  # for Windows systems
  > %HEIDELTIME_HOME%\metadata\setenv.bat
```
If you run HeidelTime together with the JVnTextProWrapper, you should only need to perform this action once per pipeline execution.


## Configuration for the UIMA pipeline ##

The JVnTextProWrapper's descriptor resides in `$HEIDELTIME_HOME/desc/annotator/JVnTextProWrapper.xml`.

Once you add it to your workflow, you can configure the following parameters.

  * **Annotate\_tokens**: controls whether or not Token Annotations will be added to the pipeline
  * **Annotate\_sentences**: controls whether or not Sentence Annotations will be added to the pipeline. Note that HeidelTime requires these to perform any work at all.
  * **Annotate\_partofspeech**: controls whether or not part-of-speech information will be added to Token Annotations.
  * **Sent\_model\_path**: this must be set to the path that contains the Sentence model folder you wish to use. Example: /some/path/JVnTextPro-v.2.0/models/jvnsensegmenter
  * **Word\_model\_path**: this must be set to the path that contains the Word model folder you wish to use. Example: /some/path/JVnTextPro-v.2.0/models/jvnsegmenter
  * **Pos\_model\_path**: this must be set to the path that contains the POS tag folder you wish to use. Example: /some/path/JVnTextPro-v.2.0/models/jvnpostag/maxent