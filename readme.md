# kongdd_packages

[![License](http://img.shields.io/badge/license-GPL%20%28%3E=%203%29-brightgreen.svg?style=flat)](http://www.gnu.org/licenses/gpl-3.0.html)

>  Copyright (c) 2019 Dongdong Kong, China University of Geosciences

> Keep in mind that this repository is released under a GPL3 license, 
> which permits commercial use but requires that the source code (of
> derivatives) is always open even if hosted as a web service.

## Table of Content
[TOC]

## Installation

This repository is a GEE package in `JavaScript`. You can access it by 
https://code.earthengine.google.com/?accept_repo=users/kongdd/public.

## Functions

### 1. Visualization

```javascript
// Load package
var pkg_vis  = require('users/kongdd/public:pkg_vis.js');
```

- gradient legend, `pkg_vis.grad_legend(viz, title, IsPlot, position)`

   - viz           Visualization parameters.
   - position      String, legend position, e.g. "bottom-left", "bottom-right".
   - palette       Corresponding colors.

- discrete legend, `pkg_vis.discrete_legend(names, palette, title, IsPlot, position)`

   Legend examples: https://code.earthengine.google.com/c35e156e943370c1dd363732a5b59531.

- Layout
   `layout` works like `layout` in **R** and `subplot` in __MATLAB__ , which is used to produce multiple maps.

### 2. Temporal interpolation

```javascript
// load package
var pkg_smooth = require('users/kongdd/public:Math/pkg_smooth.js');
```

- Linear interpolation, `pkg_smooth.linearInterp(imgcol, frame, nodata)`

   Example: https://code.earthengine.google.com/3b08f56a5f646104c742be584877e94e.

- Historical average interpolation: `pkg_smooth.historyInterp(imgcol, imgcol_his_mean, prop, nodata)`

   Example: https://code.earthengine.google.com/3b08f56a5f646104c742be584877e94e.

- `wBisquare_array` Bisquare weights updating function

### 3. Trend Analysis

```javascript
// Load package
var pkg_trend = require('users/kongdd/public:Math/pkg_trend.js');
```

- `aggregate_prop`: works like `aggregate` function in  **R** . 

   ```javascript
   // add the property of Year, YearStr, YearMonth, Season
   imgcol      = pkg_trend.imgcol_addSeasonProb(imgcol); 
   imgcol_year = pkg_trend.aggregate_prop(imgcol, "year", 'mean');
   pkg_trend.aggregate_prop(ImgCol, prop, reducer, delta)
   ```

- linearTrend, `pkg_trend.linearTrend(ImgCol, robust)`

### 4. Export data

```javascript
// Load package
var pkg_export = require('users/kongdd/public:pkg_export.js');
```

*<u>If you need to download in batch, suggest combining with [gee_monkey](https://github.com/kongdd/gee_monkey).</u>*   

- `ExportImg`: Export `ee.Image` in degree, `pkg_export.ExportImg(img, task, options)`

- `ExportImgCol`: Export `ee.ImageCollection` in degree, `pkg_export.ExportImgCol(ImgCol, dateList, options, prefix)`


### 5. Palette

Show available palettes provided by `pkg_vis`. This function is modified from [Gena](https://github.com/gena)‘s package.

```javascript
pkg_vis.showColors();
```

![](man/Figure/RColorBrewer.svg)   
*<u>Figure 1. Available palettes.</u>*

