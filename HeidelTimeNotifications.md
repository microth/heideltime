# December 8, 2014 #

Dear HeidelTime users,

We are happy to announce the release of version 1.8 of our multilingual, cross-domain temporal tagger HeidelTime.

There are two major additions to HeidelTime that have flown into this release. The first is Croatian resources that Luka Skukan of the University of Zagreb has kindly provided to us. With Croatian, HeidelTime supports 11 languages now.
Additionally, we are releasing a major overhaul of our Italian resources with which we participated in this year's EVALITA 2014 EVENTI challenge, where we managed to secure first place in the sub-task of temporal tagging (extraction and normalization).

We will be presenting our work for this challenge in a short talk and as a poster at EVALITA 2014 in Pisa this week on December 11th. The poster looks like this:
[http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/evalita2014\_poster.pdf](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/evalita2014_poster.pdf)

Furthermore, we have made some processing speed and stability improvements affecting the UIMA kit and standalone versions as well as all languages.
To download HeidelTime 1.8, take a look at our Downloads page:
[https://code.google.com/p/heideltime/wiki/Downloads](https://code.google.com/p/heideltime/wiki/Downloads)

If you'd like receiving real-time updates on HeidelTime, make sure to
follow us on Twitter: [https://twitter.com/heideltime](https://twitter.com/heideltime)

We appreciate your interest and feedback.

Best Regards,
The HeidelTime Team
http://code.google.com/p/heideltime/
Twitter: @HeidelTime (https://twitter.com/heideltime)

# May 27, 2014 #

Dear HeidelTime users,

We are once more releasing a new version (1.7) of our temporal tagger HeidelTime ([https://code.google.com/p/heideltime](https://code.google.com/p/heideltime)).

Our focus for this version was on implementing support for the recognition and normalization of **Historic Dates** - expressions that describe dates before and "shortly" after the year 0. In this context, we not only extended HeidelTime but also developed the multilingual AncientTimes corpus containing temporally annotated documents about different time periods.

We will present this work ("Extending HeidelTime for Temporal Expressions Referring to Historic Dates") at LREC this week. If you are in Reykjavik, visit us at our poster:
Thursday, May 29, 14:55 - 16:35, Poster Area 1, P34: Corpora and Annotations.
The poster looks like this:
[http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/lrec2014\_poster.pdf](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/lrec2014_poster.pdf)

Furthermore, Elena Klyachko has kindly provided us with a preliminary set of **Russian resources** for HeidelTime that she developed for her master's thesis. With her help, we have incorporated them into our UIMA Kit and Standalone versions and are thus to our knowledge the first publicly available temporal tagger that supports Russian.

Note that so far, the resources of 8 of the 10 currently supported HeidelTime languages already address historic dates, while we are confident that the support for Chinese and Russian will follow soon.

To download HeidelTime 1.7, take a look at our Downloads page:
[https://code.google.com/p/heideltime/wiki/Downloads](https://code.google.com/p/heideltime/wiki/Downloads)

If you'd like receiving real-time updates on HeidelTime, make sure to follow us on Twitter: [https://twitter.com/heideltime](https://twitter.com/heideltime)

We appreciate your interest and feedback.

Best Regards,
The HeidelTime Team
http://code.google.com/p/heideltime/
Twitter: @HeidelTime (https://twitter.com/heideltime)

# April 4, 2014 #

Dear HeidelTime users,

We are pleased to announce the release of the new stable version 1.6 of our temporal tagger HeidelTime (http://code.google.com/p/heideltime/).

The major addition to functionality for this release is the support of processing Chinese documents, which we will also present at EACL in Gothenburg (poster paper):

Hui Li, Jannik Strötgen, Julian Zell, and Michael Gertz:
Chinese Temporal Tagging with HeidelTime.
To appear: EACL'14.

We also made minor improvements to almost all resources, and improved the handling overlapping expressions as well as the overall compatibility.

A more detailed list of the changes can be viewed under
http://code.google.com/p/heideltime/wiki/ChangeLog

If you want to get more HeidelTime-related news, please follow us on Twitter: https://twitter.com/heideltime

As always, your feedback is highly appreciated.

Best regards,
The HeidelTime Team
http://code.google.com/p/heideltime/
Twitter: @HeidelTime (https://twitter.com/heideltime)

# September 18, 2013 #
Dear HeidelTime users,

Once more we are happy to release a new stable version 1.5 of HeidelTime (https://code.google.com/p/heideltime).

The biggest addition in this release is the support for French documents, thanks to the contribution of French resources by [Véronique Moriceau](http://vero.moriceau.free.fr/) of the LIMSI-CNRS. Aside from this, a lot of work went into improving resources as well as adding even more functionality to HeidelTime Standalone.


A brief overview of the other major changes included in this release:

- Added support for the IntervalTagger to HeidelTime Standalone
- Added support for the StanfordPOSTagger to HeidelTime Standalone
- Improvements in English, German and Vietnamese resources
- Added IntervalTagger resources for Vietnamese
- Added rudimentary Maven support (see the new Wiki page http://code.google.com/p/heideltime/wiki/Maven for details)


These and several more of the changes can be viewed under https://code.google.com/p/heideltime/wiki/ChangeLog.

As always, your feedback is highly appreciated.

Best Regards,
The HeidelTime Team (https://code.google.com/p/heideltime; Twitter: [@HeidelTime](https://twitter.com/HeidelTime))


# July 2, 2013 #
Dear HeidelTime users,

We are again happy to announce a new stable version 1.4 of HeidelTime (https://code.google.com/p/heideltime).

After our release of version 1.3 in April, this version mainly contains bug fixes and the introduction of support for Arabic and Vietnamese in our standalone HeidelTime package. To understand how to run HeidelTime Standalone for Arabic and Vietnamese documents, please refer to the manual that comes with the distribution.

A brief overview of changes that we made:

  * Added support for Arabic and Vietnamese in Standalone
  * Rewrote both the JVnTextProWrapper and StanfordPOSTaggerWrapper to produce more robust output
  * Fixed a bug in resource preparation under Windows for paths with spaces
  * Made several improvements to German, Spanish, Italian, Arabic and Vietnamese resources
  * Improved error handling in HeidelTime for incomplete resources

These and several more of the changes can be viewed under https://code.google.com/p/heideltime/wiki/ChangeLog.

As always, your feedback is highly appreciated.

Best regards,
The HeidelTime Team (https://code.google.com/p/heideltime; Twitter: [@HeidelTime](https://twitter.com/HeidelTime))


# April 18, 2013 #

Dear HeidelTime users,

We are happy to announce a new stable release of HeidelTime (http://code.google.com/p/heideltime/).

It has been a long time since we last published a new release, and a lot of changes have been made since. With our participation in the TempEval-3 challenge, we now present HeidelTime 1.3 (TempEval-3 winner for English and Spanish temporal expression extraction and normalization).

Please note beforehand that the HeidelTime 1.3 UIMA Kit cannot be considered a drop-in replacement for any prior version as we have made extensive changes to the code as well as resources and UIMA descriptors. Substituting the Standalone for an older version should not pose a problem, as long as the newer config.props file is used.

Here are some cliffnotes of what's new:

  * NEW LANGUAGES: Support and resources for Arabic, Vietnamese, Spanish, and Italian were added (so far, Arabic and Vietnamese can only be used with the UIMA kit, but we are working on bringing that functionality to the Standalone version as well)
  * The IntervalTagger: A UIMA Annotation Engine that discovers interval expressions and translates dates of every granularity into an interval with earliest/latest start/end points
  * TempEval-3 Reader and Writer UIMA Engines
  * Better support for the Windows and MacOS X platforms
  * A few additional parameters and improved behaviour for the Standalone
  * The TreeTaggerWrapper: A UIMA Annotation Engine that interfaces with the TreeTagger
  * The JVnTextProWrapper: A UIMA Annotation Engine that interfaces with JVnTextPro, a Vietnamese tokenizer/tagger
  * The StanfordPOSTaggerWrapper: A UIMA Annotation Engine that interfaces with the Stanford POS Tagger (for Arabic)

For the full changelog, please see https://code.google.com/p/heideltime/wiki/ChangeLog.
We also updated the online demo: http://heideltime.ifi.uni-heidelberg.de/heideltime/

As always, any kind of feedback is highly appreciated.

Best regards,
The HeidelTime Team (you can follow us on Twitter: https://twitter.com/HeidelTime)