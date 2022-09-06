# FOCUS

This repository contains the source code implementation of DeepMig and the datasets used to replicate the experimental results of our paper submitted at ICSE 2023:

_DeepMig: a transformer-based approach to support coupled library and code migrations_

*Abstract:* While working on software projects, developers often replace third-party libraries (TPLs) with different ones offering similar functionalities. However, choosing a suitable TPL to migrate to is a complex task. As TPLs provides developers with Application Programming Interfaces (APIs) to allow for the invocation of their functionalities, after adopting a new TPL, projects need to be migrated by the methods containing the affected API calls. Altogether, the coupled migration of both TPLs and 
code is a strenuous process, requiring massive development effort. So far, most of the existing approaches tackle these two issues independently, \ie they either deal with library or API call migration, but not both of them in a cohesive manner.

This paper presents DeepMig as a novel approach to the coupled migration of TPLs and API calls. It provides developers with a practical means of replacing TPLs and migrating the affected code that no longer works due to calls to replaced APIs. \DE works based on the transformer architecture, translating an input data sequence to an output one. It accepts a set of libraries to predict a new set of libraries. Afterward, it looks for the changed API calls and recommends a migration plan for the affected methods. We evaluate the proposed tool on datasets collected from Maven Central Repository. The empirical evaluation reveals promising outcomes: DeepMig recommends both libraries and code; by several testing projects, it retrieves a perfect match for the recommended items, obtaining an accuracy of 1.0. \DE outperforms a state-of-the-art baseline for TPL recommendation. More importantly, being fed with proper training data, it provides comparable code migration steps of a static API migrator.


## Repository Structure

This repository is organized as follows:

* The [tools](./tools) directory contains the implementation of the different tools we developed:
	* [DeepMig](./TOOLS/DeepMig.py): The python implementation of DeepMig
	* [Code exctractor](https://github.com/MDEGroup/aethereal/): A set of tools written in Java and [Rascal](https://www.rascal-mpl.org/) that are used to (i) transform raw Java source and binary code into DeepMig-processable data (ii) navigate the Maven Dependency Graph.
	* [DeepLib](https://github.com/MDEGroup/DeepLib): The _DeepLib_ baseline for library migrations.
	* [OpenRewrite](https://docs.openrewrite.org/): The _OpenRewrite_ baseline for code migration.
* The [dataset](./dataset) directory contains the datasets described in the paper that we use to evaluate FOCUS:

	* [DL](./dataset/DL): meta-data consisting of 122,340 software projects relying on 35,543 TPLs,
	* [DC](./dataset/DC): meta-data consisting of 3,699 update pairs counting 16,850 migration pairs,
	* [DCR](./dataset/DCRewrite): meta-data extrated from the 29 mined clients,	* [DCS](./dataset/DCSMALL): it is extracted from DC consisting of 3,953 pairs where each definition occurs in at least 10 extracted clients.
* [Supporting materials](./Materials)