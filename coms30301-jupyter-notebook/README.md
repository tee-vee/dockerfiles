# Docker Development Environment: Jupyter R ML notebook
A Jupyter notebook environment for ML in R using Weka.

This was developed for the "Introduction to ML" class at University of
Bristol.

## Usage
```
$ mkdir notebooks
$ docker run -p 8888:8888 -p "$PWD:notebooks:/home/jovyan/work" willprice/jupyter-r-weka
```

Finally point your brower to http://localhost:8888 to access the Jupyter
notebook.

## Features
* Everything from
  [jupyter/r-notebook](https://hub.docker.com/r/jupyter/r-notebook/)
* OpenJDK 7
* R Packages:
  * [rJava](https://cran.r-project.org/web/packages/rJava/index.html),
    Java VM bindings for R
  * [RWeka](https://cran.r-project.org/web/packages/RWeka/index.html),
    R interface to Weka, a collection of ML algorithms for data mining
  * [partykit](https://cran.r-project.org/web/packages/partykit/index.html),
    A toolkit for representing, summarizing and visualising tree
    structured regression and classifications models

## Build
```
$ docker build -t willprice/jupyter-r-weka .
```
