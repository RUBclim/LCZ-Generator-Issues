[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/RUBclim/LCZ-Generator-Issues/master.svg)](https://results.pre-commit.ci/latest/github/RUBclim/LCZ-Generator-Issues/master)

# LCZ-Generator-Issues

Use this repository to create issues for the [LCZ-Generator](https://lcz-generator.rub.de/).

- if you think your issue might be sensitive [reach out directly to us](mailto:lcz-generator@rub.de).

## [LCZ Generator Status](https://hetrixtools.com/r/34989feee57529ebe9c7c3a96d3e1bbe/)

You can't reach the LCZ Generator? Have a look at the status [status page](https://hetrixtools.com/r/34989feee57529ebe9c7c3a96d3e1bbe/)

## Changelog

### 2.6.1 (2025-08-20)

#### Modifications

- fix container health checks, fix url rewrite from cloud-optimized geotiffs
- update requirements
- move to python 3.13
- add google site verification

### 2.6.0 (2025-04-07)

#### Modifications

- move to TiTiler for hosting the TMS server
- upgrade requirements

### 2.5.4 (2025-02-20)

#### Bug fixes

- fix a bug where requeueing a submission failed, when the metadata already existed in the directory

### 2.5.3 (2025-02-20)

#### Bug fixes

- we need to explicitly specify the cloud project to use when working with the earthengine CLI

#### Modifications

- upgrade requirements

### 2.5.2 (2025-01-30)

#### Modifications

- remove a leftover print statement
- port the deployment to docker
- move to Python 3.12 for the deployment
- remove deprecated `datetime.utcnow`

### 2.5.1 (2025-01-25)

### Bug fixes

- the new test-train-split algorithm released in 2.5.0 did not work with TAs where **every** class only had the minimum of three TAs (which are very bad TA sample sets, but are submitted frequently)

### Modifications

- upgrade requirements
- previously an invalid kmz file was reported as an error even though it was correctly rejected

### 2.5.0 (2025-01-14)

#### Modifications

- upgrade requirements
- The test-train split for the 25 bootstraps performed is now stratified per LCZ-class. This
  improves the robustness of the accuracy assessment and should reduce the number of failed
  submissions due to not enough class being available. The change is documented
  [here](/tt_split_algo_change.md) and the overall impact was assessed and found to be,
  in most cases, minimal. If there are any questions regarding this change, please reach out.

### 2.4.0 (2024-12-28)

#### Modifications

- upgrade requirements
- for training areas to be valid, there now have to be at least 3 polygons per class present for a submission to go through
- use `uv` for requirements-management and CI

### 2.3.1 (2024-11-08)

#### Features

- extend routine that extracts TAs from the LCZ Generator to also include data from the
  old WUDAPT portal
- Use gzip compression fro requests - this will drastically speed up loading the
  submission table for users with a slow(er) internet connection

#### Modifications

- upgrade requirements

### 2.3.0 (2024-09-26)

#### Features

- add routine to extract TAs from LCZ Generator

#### Modifications

- add new FAQ-entries for downloading TAs and the submission table
- Revert: change the maximum allowed area from 2.5°x 2.5° to 2.0° x 2.0°
- upgrade requirements

### 2.2.0 (2024-08-14)

#### Features

- allow suppressing the error email to the submitter for a requeue
- allow requeueing multiple submissions at once
- implement monitoring of all earthengine tasks to be able to terminate early
  if something went wrong. Previously the task would only terminate when the time
  limit was reached

#### Modifications

- **change the maximum allowed area from 2.5°x 2.5° to 2.0° x 2.0°**
- upgrade requirements

### 2.1.7 (2024-08-12)

#### Bug Fixes

- address geometry warnings when setting a CRS

#### Modifications

- upgrade requirements
- migrate to a google cloud project

### 2.1.6 (2024-07-24)

#### Bug Fixes

- fix the centering of the datatable components when resized

#### Modifications

- upgrade requirements
- remove export to earthengine to save computation time

### 2.1.5 (2024-04-15)

#### Bug Fixes

- fix data tables appearance after 2.0.0 changes

#### Modifications

- upgrade requirements
- add bootstrap styling to the accuracy slider

### 2.1.4 (2024-03-05)

#### Modifications

- update dependencies

### 2.1.3 (2023-12-19)

#### Modifications

- update dependencies
- add an sri-checker as pre-commit hook and in CI to avoid invalid SRI-hashes ending up in production
- update the links for the global LCZ map to point to the updated version in earthengine
- make the css/js upgrade write atomically
- migrate the dependency management from `requirements-tools` to `pip-tools`

### 2.1.2 (2023-11-20)

#### Bug Fixes

- fix a bug where the selection of rows for download was not possible due to a js/css hash being invalid

#### Modifications

- update dependencies
- change the order of the leaflet layer in the display of the global LCZ-Map so they appear similar to a GIS

### 2.1.1 (2023-10-25)

#### Modifications

- update dependencies ([CVE in Werkzeug](https://cwe.mitre.org/data/definitions/407.html))

### 2.1.0 (2023-10-24)

#### Modifications

- update dependencies
- update FAQ with multi-temporal LCZ mapping which is now open-source on GitHub

#### Features

- add versioning to tile map services (TMS). Now version `v2` and version `v3` are available as well as a `latest` version always pointing towards the latest available version (currently `v3`). To avoid breaking existing connections to the TMS, old urls will now redirect to the latest version. This way was selected since no versioning was provided for the old urls hence updates can be expected (similar to open street map). The documentation was updated accordingly.

### 2.0.1 (2023-09-24)

#### Modifications

- update dependencies #442
- update FAQ with multi-temporal LCZ mapping which is now open-source on GitHub #446

#### Features

- add feature to allow inverting coordinates for multiple Tile Map Services #445

### 2.0.0 (2023-06-16)

#### Modifications

- update requirements
- Make the generic error email a little more specific and suggest a fix. Since most unhandled errors are caused by too few training areas
- change the license from **CC BY-SA** to **CC BY-NC-SA**. To be fully transparent: The following changes were applied to the license:

```diff
commit fb5cfabcf92fdeac19775542f9a78e8daf4e449e
Author: Jonas Kittner
Date:   Wed Jun 14 18:22:31 2023 +0200

    change the licence from CC BY-SA to CC NC-BY-SA

diff --git a/dashboard/templates/attribution_text.html b/dashboard/templates/attribution_text.html
index 0f48c48..69adffc 100644
--- a/dashboard/templates/attribution_text.html
+++ b/dashboard/templates/attribution_text.html
@@ -31,7 +31,7 @@
     <li>
       {{ content.LASTNAME|e }}, {{ content.FIRSTNAME|e }}
       ({{ content.SUBMISSIONDATE[:4]|e }}). WUDAPT Level 0 training data for {{ content.CITY|e }} ({{ content.COUNTRY|e }}), submitted to
-      the LCZ Generator. This dataset is licensed under CC BY-SA, and more information is available at
+      the LCZ Generator. This dataset is licensed under CC BY-NC-SA, and more information is available at
       <a
         href="https://lcz-generator.rub.de/factsheets/{{ content.HASHID|e }}/{{ content.HASHID|e }}_factsheet.html"
       >
diff --git a/dashboard/templates/tos_text.html b/dashboard/templates/tos_text.html
index 09aaca0..77dee0e 100644
--- a/dashboard/templates/tos_text.html
+++ b/dashboard/templates/tos_text.html
@@ -1,11 +1,12 @@
 <p class="tm-p-mb">
   All data are distributed under the
-  <a href="https://creativecommons.org/licenses/by-sa/4.0/" target="_blank">
-  CC BY-SA 4.0 license</a>. In particular, permission is hereby granted, free
-  of charge, to any person obtaining a copy of this data and associated
-  documentation files, to copy and redistribute the material in any medium or
-  format, and to remix, transform, and build upon the material for any purpose,
-  even commercially, all subject to the following:
+  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank"
+    >CC BY-NC-SA 4.0 license</a
+  >. In particular, permission is hereby granted, free of charge, to any person
+  obtaining a copy of this data and associated documentation files, to copy and
+  redistribute the material in any medium or format, and to remix, transform,
+  and build upon the material for non-commercial use only, all subject to the
+  following:
 </p>
 <ul>
   <li>
```

#### Features

- Document how to use the tile map service (TMS) of the global LCZ map in qgis and `contextily`

### 1.7.0 (2023-05-08)

#### Modifications

- update requirements
- migrate to `sqlalchemy` >= 2.0
- make the codebase python3.11+

#### Features

- migrate to bootstrap 5. Attribution Guidelines, Terms of Service and Declaration of Consent now show up as a modal instead of a popup

### 1.6.2 (2023-03-13)

#### Modifications

- update requirements

### 1.6.1 (2023-01-27)

#### Bug fixes

- fix a bug where mixed geometry type (`Polygon` and `LineString`) caused the training
  area database insert to fail.

#### Modifications

- tests against python 3.11
- update requirements
- fix warning and remove pinning of scikit-learn for `min_samples` of `DBSCAN`

### 1.6.0 (2022-12-01)

#### Bug fixes

- fix a bug where nothing was logged, because the log level was set incorrectly set to `ERROR` (the default) instead of `INFO`
- fix a bug where no errors were sent to sentry, because the `DSN` was set incorrectly
- fix a bug where the DOI did not point to the generic DOI within Zenodo.
- fix a typo in the integrity check of the `leaflet.js` library
- Now the email also takes the original casing into account
- fix deprecation warnings

#### Modifications

- vendor all used images directly to not rely on 3rd parties
- update all external `css` and `js` that is used
- check the integrity of every `js` and `css`
- update the dependencies
- render the date displayed in the submission table in the user's timezone and format
- keep the casing the user entered when submitting. Do not capitalize it anymore. Existing records were updated using `INITCAP` to be compatible.
- make the codebase python3.10+ (using `pyupgrade`)

#### Features

- implement a script for safely requeueing a submission. A few prerequisite need to be fulfilled before being able to requeue. If one was not satisfied, the user got a second error email. (almost all necessary requeues are caused by an unstable internet connection at the data center or an outage of the university-Email service - both are outside of what we can fix (we already have a dozen exponentially backed off retries))

#### Test/code quality

- do not test against python 3.9 anymore, since the deployed version is python 3.10
- extent `mypy` checking and add missing type annotations
- the codebase is python3.10+ now removing most imports from `typing` and only testing against python 3.10 also configuring `pre-commit` accordingly
- fix some test pollution that was caused by incorrectly mocking the `mapping_process`

### 1.5.0 (2022-11-07)

#### Bug fixes

- fix broken link to institute logo
- fix a bug where the logger handler was not cleared properly

#### Modifications

- update dependencies

#### Features

- add link to Google Earth Engine and show code snippet

### 1.4.0

#### Modifications

- update requirements
- improve the error emails
- improve error and performance monitoring

#### Features

- implement an XYZ tile map server for the global LCZ map
- implement an inverted y-axis redirect for the global LCZ map tile map server

### 1.3.0

#### Bugfixes

- fix broken shp links in shape files. Previously only the `.shp` could be downloaded

#### Modifications

- update requirements

#### Features

- add new API to request the quality control polygons and point shape files

### 1.2.2

#### Bugfixes

- upgrade version of `Pillow` because `9.1.0` had a [CVE-2022-30595](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-30595)

#### Modifications

- change internal dependency management tool
- multiple version upgrades, now all bundled in one PR

### 1.2.1

#### Modifications

- dependency updates

### 1.2.0

#### Modifications

- dependency updates
- Show the full firstname in the citation suggestion for the training areas

#### Tests/code quality

- CI improvements
- test speed improvements
- pre-commit autoupdate

### 1.1.4

#### Modifications

- dependency updates
- improve the loading speed of the submission table
- extend the submission form expiration time (_Error CSRF Token expired_)
- add more retries to all email sending calls to address reoccurring short outages of the RUB-Email service

### 1.1.3

#### Modifications

- dependency updates

### 1.1.2

#### Bugfixes

- fix a bug where cases with two folders in the input file, but one only with 1 polygon were not rejected and the processing would fail in the end
- fix a bug where filenames with not a single ascii character would cause an internal server error

#### Modifications

- dependency updates
- make the error message for too few polygons more explicit

### 1.1.1

#### Bugfixes

- fix a typo on the index page
- fix a bug where an error `403` was raised when trying to access `*.kmz` files
- fix a bug where a file just called `.kml` or `.kmz` would cause and internal server error `500`

#### Modifications

- dependency updates
- add item to FAQ for submission deletion

### 1.1.0

#### Bugfixes

- added two missing tiles for EO data in eastern Alaska
- fix a bug where a training area file would pass the quality check, even though it only had one LCZ class
- fix a bug where a submission was not fully removed, even though the initial check failed

#### Modifications

- dependency updates
- do not send the processed results via email anymore, generate only a download link in the email

#### Features

- add a `.kmz` file with the LCZ map and already applied colormap to the archive
  - a link for the download of this file is also included in the factsheet

### 1.0.3

#### Bugfixes

- fix a bug where a missing asset in earthengine would cause the mapping process to fail

#### Modifications

- dependency updates

### 1.0.2

#### Bugfixes

- fix/handle an (upstream) [bug](https://issuetracker.google.com/u/1/issues/188576299) where the asset ingest would randomly fail, but succeed on the second try

#### Modifications

- dependency updates

### 1.0.1

#### Bugfixes

- fix a bug where an internal server error (500) would be raised if the `kml` file had an invalid syntax and could not be parsed
- fix a bug where the quality control would fail
- fix a bug where 2 dimensional `kml` files (only two coordinates, no z coordinate) would cause an error. 2D polygons are now converted to 3D polygons, adding 0 as the new z-value
- fix a bug where an invalid `kmz` file caused an internal server error (500)
- fix a typo `succesfully` &rarr; `successfully`

#### Modifications

- dependency updates
- add a new web message for the invalid `kmz` file case

#### Features

- improve the internal error notification system

### 1.0.0

#### Modifications

- add the final reference and DOI for the paper: [Demuzere et al. (2021)](https://doi.org/10.3389/fenvs.2021.637455)
- restructure `/`- index page

#### Features

- add a `/faq` route
- add a quality disclaimer to the top of the submission page
- add a _getting started_ to the index page

### 0.0.0b9

#### Bugfixes

- fix a bug where multi part features could not be processed. The features are now split up into single part features so the quality check can work on the individual polygons

#### Features

- add a `/robots.txt` route so crawlers can access it

### 0.0.0b8

#### Bugfixes

- fix a bug where fonts were missing
- fix a bug where the qc failed when an LCZ class was present in the training data, but not in the final result coming from earth engine
- fix a bug where the deprecation of `ee.Classifier.randomForest` caused the mapping process to fail
- fix a bug where a submission would be displayed in the `/submission` table even though it failed
- fix a bug where the colors of the provided LCZ color maps and the used colors would differ from each other
- fix a bug where a mapping process would not terminate if the earth engine mapping process failed

#### Modifications

- change the header in the Terms of Service page for the Declaration of Consent to be the same font size
- use a `.clr` ArcGIS ascii formatted colormap

#### Features

- add a favicon route at `/favicon.ico`
- limit the size of incoming request to max 10 MB

### 0.0.0b7

#### Bugfixes

- fix a bug where not always the best result per author and city was displayed in the show best submission table
- fix bug where burger menu could not be closed on the submission table page
- fix general typos

#### Modifications

- change html page title of the index page from `Index` to to `LCZ Generator`
- link in page footer for github issues now points to the issue overview instead of the form where a github user account was required
- update Terms of Service
- split Terms of Service and Attributions in separate sections in the factsheet
- add a Privacy Note to the footer
- results are now sent via a different email address
- the LCZ Generator is now accessible via a shorter url: `https://lcz-generator.rub.de`
- the histogram of the number of Training Areas per class now only shows integer values on the y-axis
- whitespace escape sequences are now removed in the reference and remarks section

#### Features

- add colormaps for QGIS and ArcGIS to the results zip archive
- add a suggestion for citing the training data to the factsheet

### 0.0.0b6

#### Bugfixes

- fix bug where leading and trailing whitespaces was not stripped in firstname, lastname and city

#### Features

- added footers to all pages including useful links
- added a navbar to improve navigation between different pages

### 0.0.0b5

#### Bugfixes

- fix typo on index page footer

#### Modifications

- change `Freq` to `Count` in `<id>_TA_statistics.csv`
- update the Terms of Service: now using `CC-BY`
- update the background image of the index page with the new filtered version of the [european LCZ map](https://figshare.com/s/db6203e0a806816c6f22)
- add link to [wudapt.org](http://wudapt.org) in the index page footer
- change paper status from _in preperation_ to _submitted_

### 0.0.0b4

#### Bugfixes

- fixed a bug where the country selection was not kept when reloading the page or after being redirected from the same page

#### Modifications

- the `/country/<continen_code>`-API now only takes arguments with length `2`.
  - all other requests are not executed, instead aborted with error `400` (Bad Request)
- reformat all `html` templates

#### Features

- add popover to the publish name and email checkbox
- a `?` is now present. When hovering over it, a help message is displayed
