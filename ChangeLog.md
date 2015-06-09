# Changelog #

### Version 1.8 (rf03c102b1569) ###

  * fixed: Italian resources have received a major overhaul `[`Resources`]`
  * added: Support for Croatian (thanks to Luka Skukan), including a wrapper for the hunpos preprocessing tool `[`Resources`]`
  * added: Ability to use regular expressions in POS constraints of rules `[`Resources`]`
  * added: Tokenization without the Tree Tagger's Perl script `[`TreeTaggerWrapper`]`
  * fixed: various minor bugfixes in the TreeTaggerWrapper and Standalone code
  * fixed: Some code pertaining to the invocation of Processors `[`Core`]`

### Version 1.7 (r8d11b8f5f37f) ###

  * added: Support for calculation of BC and AD dates, and dates close to the year 0, including Arabic, Dutch, English, French, German, Italian, Spanish, Vietnamese language resources.
  * added: A preliminary version of Elena Klyachko's Russian resources `[`Resources`]`
  * fixed: A minor issue with parameter files in TreeTaggerWrapper `[`Core`]`

### Version 1.6 (r83d785e4ce5e) ###

  * added: Chinese resources, support in TreeTaggerWrapper as well as the TempEval-2 Reader and Standalone version
  * added: Better handling of overlapping temporal expressions `[`Core`]`
  * fixed: Made TempEval-3 Reader more robust to non-TE3-inputs
  * fixed: More stable TreeTaggerWrapper parameter file recognition
  * fixed: Various minor improvements in the resources for all languages `[`Resources`]`
  * fixed: Some minor fixes for resource recognition in Standalone `[`Standalone`]`

### Version 1.5 (r0e374f29f3e9) ###

  * added: French resources, kindly provided by Véronique Moriceau of the LIMSI-CNRS `[`Resources`]`
  * added: Support for the IntervalTagger in HeidelTime Standalone `[`Standalone`]`
  * added: Support to choose from !StanfordPOSTagger or TreeTagger as HeidelTime Standalone's preprocessing engine `[`Standalone`]`
  * added: Interval resources to Vietnamese `[`Resources`]`
  * fixed: Improvements in German, English and Vietnamese resources `[`Resources`]`
  * added: Rudimentary Maven support `[`Meta`]`

### Version 1.4.1 (r676009ca8119) ###

  * fixed: A bug that would prevent HeidelTime Standalone from loading resources under Windows `[`Standalone`]`

### Version 1.4 (r8f7fb11e0052) ###

  * added: Support for Spanish and Arabic document processing via standalone `[`Standalone`]`
  * added: Some more error handling for unexpected user input `[`Core`]`

  * fixed: Made fixes and alterations to Spanish, Italian, German, Vietnamese and Arabic resources `[`Resources`]`
  * fixed: A bug where underspecified centuries ("UNDEF-century") in resources would break processing `[`Core`]`
  * fixed: Made several improvements to the StanfordPOSTagger to work with more unconventional documents
  * fixed: Erroneous normalization of underspecified centuries; it now works according to the TIMEX standard `[`Resources`]`
  * fixed: The Windows `printResourceInformation.bat` script now works with paths that contain spaces `[`Resources`]`

### Version 1.3 (r79aa71332497) ###

  * added: Resources for Spanish, Italian, Vietnamese and Arabic `[`Resources`]`
  * added: TreeTaggerWrapper, a sentence-tokenization, word-tokenization and part of speech tagging wrapper for the popular TreeTagger. It replaces the DKPro Analysis Engines as preprocessing component.
  * added: Support for regular expressions in normalization resources `[`Core`]`
  * added: A new annotator, IntervalTagger that recognizes interval expressions
  * added: New UIMA Collection Reader and Consumer for our participation in the TempEval-3 challenge: TempEval3Reader and TempEval3Writer
  * added: A UIMA Analysis Engine (JVnTextProWrapper) that leverages the JVnTextPro tool to produce word- and sentence-tokenization as well as part of speech tagging for Vietnamese
  * added: A switch (-c) that allows passing the path of the config.props file ([issue 3](https://code.google.com/p/heideltime/issues/detail?id=3)) `[`Standalone`]`
  * added: Sub-processor priorities to influence when they are being run `[`Core`]`
  * added: Switches (-v/-vv) to control the verbosity of logging messages ([issue 4](https://code.google.com/p/heideltime/issues/detail?id=4)) `[`Standalone`]`
  * added: A descriptor parameter as well as command line switch (-locale) to specify a locale for HeidelTime to base relative date calculation on ([issue 1](https://code.google.com/p/heideltime/issues/detail?id=1)) `[`Core/Standalone`]`
  * added: setenv and printResourceInformation batch files for Windows
  * added: An optional setting in the ACETernWriter descriptor to prevent conversion from Timex3 to Timex2

  * fixed: Charset in Dutch resources `[`Resources`]`
  * fixed: Behaviour when non-hardcoded languages are supplied: The resource folder is assumed to be the name of the language `[`Core`]`
  * fixed: Token boundary detection `[`Core`]`
  * fixed: Typos in english resources `[`Resources`]`
  * fixed: A bug where two overlapping temporal expressions would break XML-conformity ([issue 5](https://code.google.com/p/heideltime/issues/detail?id=5)) `[`Standalone`]`
  * fixed: A bug that would break resource loading on the Mac OS platform `[`Core`]`
  * fixed: TempEval2 Reader now works properly with the italian TempEval2 corpus
  * fixed: ACE Tern reader recognizes DCTs from the ICAB corpus
  * fixed: A bug in TempEval2Writer that would break the output of parallelized UIMA workflows
  * fixed: A bug where when you used the HeidelTime standalone version programmatically, the OutputType would be ignored ([issue 7](https://code.google.com/p/heideltime/issues/detail?id=7)) `[`Standalone`]`
  * fixed: Several things in a lot of places that made it hard to use HeidelTimeStandalone programmatically (i.a. [issue 6](https://code.google.com/p/heideltime/issues/detail?id=6)) `[`Standalone`]`

### Version 1.2 (r66d53ffd449d) ###

  * added: links to the journal paper to the readme file
  * fixed: TIMEX3 SET expressions not being translated to TIMEX2 expresions correctly `[`ACETernWriter`]`
  * removed: dead code

### Version 1.1 (r55cd93c1bbca) ###

  * added: support code and english resources for two additional domains: COLLOQUIAL and SCIENTIFIC
  * fixed: an incorrect DCT recognition regex
  * fixed: standalone not recognizing parameters when not all upper case

### Version 1.0 (r82f25f0e2dc5) ###

  * conducted major code overhaul, mostly modularization-based refactoring
  * merged the previously independent heideltime-standalone project into the kit repository
  * fixed: made logger message source more apparent

### Version 0 (r41421a5ee0a7) ###

  * added: support to read the ACE Tern 2005 Corpus
  * fixed: regex recognitions of strings in the form of "1995-1996"
  * added: recognition logic for holidays together with english and german resources

### Initial Version (rc00a05746254) ###

This release represents the state of HeidelTime's development before the use of a revision control system; i.e., the version, which was available from the dbs.ifi.uni-heidelberg.de page.