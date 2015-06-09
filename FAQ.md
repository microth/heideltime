#Frequently asked questions

This page contains frequently asked questions as well as notes about how HeidelTime functions.



### Chinese processing under Windows ###

Due to improper codepage support in the Windows command prompt, our standard processing method (TreeTagger) for documents in Chinese will not work under Windows with the HeidelTime Kit or the Standalone version.

As an alternative, you can set up the StanfordPOSTaggerWrapper as a preprocessing engine for both the Standalone as well as the Kit version.
The way to do that for the Standalone version is described in section 4 under the "Extra steps" headline.

For a kit pipeline, you simply need to tie in the [StanfordPOSTaggerWrapper](StanfordPOSTaggerWrapper.md) Analysis Engine supplied with the kit ahead of the HeidelTime AE.

For both of these variants, you will need to specify one of the Chinese model files that ship with the StanfordPOSTaggerWrapper full version.