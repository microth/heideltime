


# Introduction #

The code that makes up the **HeidelTime** project -- written entirely in Java -- is grouped into several distinctive, independent packages. Due to the original nature of **HeidelTime**, most of the package structure is organized to reflect the separate components that can be used to run **HeidelTime** as an annotator in a [UIMA](http://uima.apache.org/) pipeline.

Having been developed under the Database Systems, all of the sub-packages reside in the `de.unihd.dbs` package.


# UIMA interface #

In order to do interface with other UIMA components, namely to comprehend data from or make data comprehensible to the [DKPro](http://www.ukp.tu-darmstadt.de/research/current-projects/dkpro/) UIMA annotator, the `AnnotationTranslator` in `de.unihd.dbs.uima.annotator.annotationtranslator` was developed.

In keeping an eye on having a highly performing analysis engine, evaluating it against a number of diverse corpora has been a key step to any change that was done to **HeidelTime** over the time. In order to be able to process these corpora, several reader and writer modules for the UIMA pipeline had to be composed:
  * ACETern reader/writer to read and write the ACE Tern, timebank and wikiwars corpora (`de.unihd.dbs.uima.reader.aceternreader` and `de.unihd.dbs.uima.consumer.aceternwriter`), and
  * Tempeval2 reader/writer to read and write the Tempeval2 corpus (`de.unihd.dbs.uima.reader.tempeval2reader` and `de.unihd.dbs.uima.consumer.tempeval2writer`).
  * Tempeval3 reader/writer to read and write Tempeval3 corpus (`de.unihd.dbs.uima.reader.tempeval3reader` and `de.unihd.dbs.uima.consumer.tempeval3writer`)

Additionally, we have developed several UIMA annotators that provide vital preprocessing information for **HeidelTime**'s use. These provide tokenization, sentence tokenization and part of speech information to the pipeline.
  * [TreeTaggerWrapper](TreeTaggerWrapper.md) (`de.unihd.dbs.uima.annotator.treetagger`)
  * [JVnTextProWrapper](JVnTextProWrapper.md) (`de.unihd.dbs.uima.annotator.jvntextprowrapper`)
  * [StanfordPOSTaggerWrapper](StanfordPOSTaggerWrapper.md) (`de.unihd.dbs.uima.annotator.stanfordtagger`)

We have also developed an annotator that, if used after and based on **HeidelTime**'s results, discovers intervals between temporal expressions in documents.
  * IntervalTagger

Finally, since **HeidelTime** itself is used as an annotator, its main class (`HeidelTime` in `de.unihd.dbs.uima.annotator.heideltime`) implements the `JCasAnnotator_ImplBase` class with its relevant methods to accomplish its task.


# HeidelTime Standalone #

Since **HeidelTime**'s functionality is usually leveraged within the context of a UIMA pipeline, there is a lot of overhead to overcome for someone who just wants to use the **HeidelTime** annotator from the command line, or as part of let's say an online demo to quickly preview its power.

For this purpose, a standalone version of **HeidelTime** was developed, wrapping the normally-present UIMA pipeline components around **HeidelTime**, handling in- as well as output, and furthermore any at a basic level required configuration parameters. This sane, self-contained project was consequently merged into the **HeidelTime** project to facilitate easier project management, ensure interoperability with the **HeidelTime** annotator and make building the standalone version less of a hack-fest.

The standalone code is contained within the package `de.unihd.dbs.heideltime.standalone`.


# HeidelTime's architectural concepts #

All of the methods and classes key to **HeidelTime**'s core functionality reside inside of the package `de.unihd.dbs.uima.annotator.heideltime`.

As any UIMA annotator component, **HeidelTime**'s main class is derived from UIMA's `JCasAnnotator_ImplBase`, whose inherited methods, called by the UIMA framework, are implemented by **HeidelTime**.

Since what **HeidelTime** does -- finding and normalizing contextualized temporal references in plain text -- requires a plethora of logic, and has a lot of openings for additional functionality to be added, it was eventually decided that, while keeping core functionality within an identity-reflecting main class, the source code's structure had to be modeled in a way that allowed for rapid comprehension of functionality as well as an architecture that would encourage the development of new sub-modules.


## Resource handling ##

As there are three major resource types that form part of **HeidelTime**'s core logic, handlers for each of these resources were implemented. All of these reside in the `de.unihd.dbs.uima.annotator.heideltime.resources` package.

A `GenericResourceManager` was constructed to take over reading of the resource files from the file system. `Manager` classes inheriting from the `GenericResourceManager` for _normalization_-, _repattern_- and _rule_-resources facilitate reading and aggregation of read information into data structures that can be accessed by **HeidelTime**'s programmatic logic.


## (Sub-)Processors ##

Since temporal expressions come in many shapes and forms, it is a natural assumption that **HeidelTime** will over time accumulate more functionality to spot them; more functionality than is already inside of its core methods. To de-clutter code, it was decided that a plug-in-like architecture would be a good architectural choice to allow for new functionality.

Any new module (Processor) must adhere to these bullet points:
  1. A Processor must inherit from the `GenericProcessor` class and implement its methods.
  1. A Processor receives the JCas object that is passed to **HeidelTime** by the UIMA pipeline and may manipulate it.
  1. A Processor must register itself in **HeidelTime**'s `initialize()` method for execution using its fully qualified name (package + class name), as well as an optional priority.

### Example: HolidayProcessor ###
Package: `de.unihd.dbs.uima.annotator.heideltime.processors`

As a first addition to **HeidelTime**, a Processor was developed that recognizes holidays: `HolidayProcessor`.

Since some holidays are dependent upon other, variable dates, it was not sufficient to just add resources to recognize holiday's names. Additionally, methods that calculate relative dates had to be devised, and these functions found their way into the first Processor of **HeidelTime**.

Its normalization resources augmented the function set to include a function to calculate dates relative to Easter Sunday -- thereby determining most Christian holidays that occur at variable dates in the year. These functions are invoked inside the `HolidayProcessor`.


## Utilities ##

Some of the methods used by **HeidelTime** do not represent functionality that is limited to just the core, but are rather of a nature that would allow for them to be used in any number of other methods in other classes as well. Those functions, due to their comparably loose relation to the context, reside inside the `de.unihd.dbs.uima.annotator.heideltime.utilities` package mostly as static methods organized into classes by commonalities in their functionality.