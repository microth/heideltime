


## Introduction ##

This section explains how to use the IntervalTagger Analysis Engine.

The IntervalTagger was developed to discover temporal expressions that define intervals spanning between two temporal expressions.


## Language support ##

For now, high quality interval rules that are required for the IntervalTagger to extract intervals exist only for German, English, Vietnamese and Italian.

If you create additional resources and would like to share them, please let us know!


## Configuration for the UIMA pipeline ##

The IntervalTagger's descriptor resides in `$HEIDELTIME_HOME/desc/annotator/IntervalTagger.xml`.

It will only be able to do its work when used together with HeidelTime. In any workflow, it needs to be inserted after HeidelTime to work properly off the temporal expressions detected by HeidelTime.

Once you add the IntervalTagger to your workflow, you can configure the following parameters.

  * **language**: this must be set to the language that you used in the HeidelTime descriptor's configuration
  * **annotate\_intervals**: if enabled, this will let the IntervalTagger add Interval tokens to the UIMA pipeline
  * **annotate\_interval\_candidates**: if enabled, this will let the IntervalTagger add IntervalCandidates to the UIMA pipeline