

# Introduction #

In this section, we'll detail how to set up the working development environment you will need in order to participate in the development of **HeidelTime**.

As **HeidelTime** is written entirely in Java, and [Eclipse](http://eclipse.org/) is the most popular Java IDE, we'll focus on setting you up with this particular IDE. If you choose to use a different IDE, you should be able to implement our instructions relatively easily in an analogous fashion in that IDE.

By the end of this tutorial, you should have a working copy of **HeidelTime** in your IDE and should be able to start implementing changes or features to **HeidelTime**.


# Eclipse IDE #

You can grab a copy of Eclipse at http://eclipse.org/downloads/. You don't need to get a specific version or abandon your current installation of Eclipse; if you don't have one already, the classic version should be adequate. Under Linux, you can just get Eclipse from your package manager.


# Repository #

As **HeidelTime** is under steady development, any changes you make should -- if possible -- be made against our latest revisions in the version control system. This makes it way easier to integrate your changes into our current codebase -- if you choose to share your work with us.

We use Mercurial, a distributed version control system. You should [grab a copy of it](http://mercurial.selenic.com/downloads/) and install it on your operating system; any of MacOSX, Windows or Linux have installation candidates.

If you've not checked out **HeidelTime**'s code from the repository before, you should get a fresh copy by cloning the official repository. From a command line, do
```
$ hg clone http://code.google.com/p/heideltime/
```
This will create a folder called `heideltime` in your current directory and download all of the files residing in the repository as well as a differential history of previous changes done by us.


# Project parameters #

At this point, we'll import the source code into an Eclipse project. To do that in a proper fashion, follow these steps:

  1. In Eclipse, go to **File** -> **New** -> **Project...**, create a **Java Project**.
  1. Give the project a name (i.e., `heideltime`), untick **Use default location** and enter or browse to the location of the `heideltime` folder we created during the cloning process. Hit **Next**.
    * In the **Source** tab, make sure that the `src/` folder is marked as a source folder and that the **Default output folder** is named "`class`", not "`bin`".
    * In the **Libraries** tab, make sure that `uima-core.jar` from the `lib/` folder is added as a library.

At this point, you should have a project filled with source code and are almost ready to get going.

Note that as of **HeidelTime** 1.3, you will need copies of the [StanfordPOSTaggerWrapper](StanfordPOSTaggerWrapper.md) `.jar` file and the [JVnTextProWrapper](JVnTextProWrapper.md) `bin` to be linked as **Libraries** inside your Eclipse project for all error messages to disappear. Eclipse will still be able to compile everything but those two wrappers without them, though.


# Finishing touches #

Once you've changed something, before you try it out in the context of a UIMA pipeline, you'll want to do a clean build at least once by going to **Project** -> **Clean...**.

After that, you'll need to open up a shell and execute the script `printResourceInformation.sh` inside the `resources/` folder:
```
$ cd resources
$ sh printResourceInformation.sh
```
This will copy all of the resources residing in the `resources/` folder to the `class/` folder and create a list of them along the way.

And that's all you need in terms of basic setup.


# Further reading #

Once you're all set up, you can take a look at ArchitecturalOverview to better understand **HeidelTime**'s source code.

To test your changes' impact on the results that **HeidelTime** produces, take a look at ReproduceEvaluationResults to set up an obstacle course to run **HeidelTime** through. Alternatively, take a look at `readme.txt` in the `doc/` folder, which contains more detailed instructions on how to set up a test.