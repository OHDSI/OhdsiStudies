OHDSI Studies
=============

**Important**: This repo was an attempt at organizing OHDSI study packages that wasn't very succesful. Please use the [ohdsi-studies organization](https://github.com/ohdsi-studies) for sharing OHDSI study packages.


Running a study
===============

Click on one of the folders and read the instructions there to execute one of these studies

Adding and updating studies
===========================

## Adding a study to this repository

1. **Create a study package repository in your own GitHub space**. We do not store any packages directly in this repository. Instead, we rely on [Git submodules](https://blog.github.com/2016-02-01-working-with-submodules/). To create a study package, please create a repository in your own GitHub space. For example, a study package called 'MethodLibraryPleEvaluation' has been created [here](https://github.com/schuemie/MethodsLibraryPleEvaluation) in @schuemie's personal space. 

2. **Add the package repository as a submodule**. Here are example Git commands:

	First clone the OhdsiStudies repository if you haven't done so:

	```git
	git clone https://github.com/OHDSI/OhdsiStudies.git
	cd OhdsiStudies
	```
	
	Then, add your repository as a submodule. Note that the URL is the 'clone' URL. The name after the URL is the name of the folder that will be created in the OhdsiStudies repository. Please keep that the same as the study package name:
	
	```git
	git submodule add https://github.com/schuemie/MethodsLibraryPleEvaluation.git MethodsLibraryPleEvaluation
	git commit -a -m "Adding submodule"
	git push
	```
	
## Updating study packages

Note that submodules create a snapshot of the study repository. OhdsiStudies will point to the commit at the time the submodule was added, future changes in the source repository are not automatically visible in OhdsiStudies. Whenever the source study package is updated, we may want to update the submodule in OhdsiStudies. Here's how:

First initialize your submodule. Before initialization, the submodules will just be pointers to the source repositories:

```git
git submodule update --init -- MethodsLibraryPleEvaluation
```

Change into the submodule directory:

```git
cd MethodsLibraryPleEvaluation
```

Switch to the source repository master branch if needed:

```git
git checkout master
```

And pull the latest changes:

```git
git pull
```

Go to the root folder, add the new changes, and push to OhdsiStudies:

```git
cd ..
git add MethodsLibraryPleEvaluation
git commit -a -m "Updating MethodsLibraryPleEvaluation submodule"
git push
```
