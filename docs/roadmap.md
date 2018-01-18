# Roadmap

Information about the actual development goals and timelines.

## Overview

* **January 18, 2018**: Meet and discuss general project strategy
* **Feburary 2018**: Can we reproduce CellRanger from the DAG or from the code? Start implementation.
* ...

## Milestones

### January 18, 2018 - Meet and discuss project strategy

* Keep the pipeline as general as possible so that every institute can use it out of the box.
* Why do we want to reimplement CellRanger in NF?!
    * Nextflow allows performance monitoring
    * More flexible code
    * Easily exchangeable modules
    * Better documentation
    * Better fine tuning of cluster ressources with respect to the different pipeline steps
* Anastasios has a lot of experience with CellRanger
* It may be hard to run CellRanger on the cluster efficiently

**TODO**

_Simon_: Take a look at the CellRanger Code and compare to the DAG 
**KEY QUESTION**: Do we stick to the CODE or to the DAG?!

Once we know, what is easier to follow for the pipeline reproduction, we start.
