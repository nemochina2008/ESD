

#### A "Quick-and-Dirty" Introduction

##### How to Install
The package is currently available from [GitHub](https://github.com/environmentalinformatics-marburg/vegexploratories) only. It can be installed via 

```r
devtools::install_github("environmentalinformatics-marburg/vegexploratories")
```


... is an open-access tutorial about the **gimms** package which is now available from [GitBook](https://www.gitbook.com/book/envin-marburg/introducing-the-r-gimms-package/details). The book will be continuously updated as **gimms** develops further, so make sure to check it out regularly!

<hr>

#### What's new?

##### 2015-12-16, added parallel support
I decided to add optional multi-core support to `downloadGimms`, `rasterizeGimms` and `monthlyComposite`. The referring arument is called 'cores' and, if not specified otherwise, defaults to 1 (i.e., parallel computing is disabled). In the course of this, the **gimms** package version on branch 'develop' has been incremented to 0.4.0 and can be installed via `devtools::install_github` (see further below).

<hr>

##### 2015-11-13, **gimms** 0.3.0 is now on CRAN
It's Friday 13th and an updated version of the **gimms** package has been published on [CRAN](https://CRAN.R-project.org/package=gimms). The new version includes

* `significantTau` to calculate pixel-based (and optionally pre-whitened) Mann-Kendall trend tests from a previously processed GIMMS NDVI<sub>3g</sub> (or any kind of) 'RasterStack/Brick' object. Note that it also works with simple 'numeric' vectors (i.e., univariate time series observations);
* the below compatibility update of `downloadGimms` that enabled 'Date' input;
* and some minor bug-fixes.

<hr>

##### 2015-11-11, `downloadGimms` now works with 'Date' input
In response to recent user suggestions, I decided to enable 'Date' input for `downloadGimms` which grants the user a finer control over the temporal coverage of the data to be downloaded. The changes are currently available from the 'develop' branch via 


```r
devtools::install_github("environmentalinformatics-marburg/gimms", 
                         ref = "develop")
```

and will be submitted to CRAN soon.

<hr>
##### 2015-11-06, pre-whitened Mann-Kendall trend test via `significantTau`
In order to account for lag-1 autocorrelation when trying to deduce reliable long-term monotonous trends, **gimms** now features a function called `significantTau`. The code imports the standard (i.e., without pre-whitening) procedure included in package **Kendall** (McLeod, 2011) or, if the user decides to apply pre-whitening prior to the actual trend test, one of the algorithms included in **zyp** (Bronaugh and Consortium, 2013). Check out `?significantTau` for further details. 

<hr> 
##### 2015-10-26, `downloadGimms` now works properly on Windows
I recently received a bug report about some strange behavior of `downloadGimms` (when working on Windows platforms) which resulted in a rather awkward look of the rasterized images. 

<center>
  <img src="http://i.imgur.com/MySaI9F.png" alt="windows_bug" style="width: 650px;"/>
</center>

The problem was obviously related to `download.file` which worked just fine on Linux when using the default settings, but introduced distortions on Windows. In the newest package version 0.2.0 which is now brand-new on [CRAN](https://CRAN.R-project.org/package=gimms), I therefore specified `download.file(..., mode = "wb")` to explicitly enable binary writing mode. 

Thanks again for the input! 

<hr>

