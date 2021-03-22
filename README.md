[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/RUBclim/LCZ-Generator-Issues/master.svg)](https://results.pre-commit.ci/latest/github/RUBclim/LCZ-Generator-Issues/master)

# LCZ-Generator-Issues

Use this repository to create issues for the [LCZ-Generator](https://lcz-generator.rub.de/).

- if you think your issue might be sensitive [reach out directly to us](mailto:info@wudapt.org).

## Changelog

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

- fixed a bug where the country selection was not kept when reloading the page or after beeing redirected from the same page

#### Modifications

- the `/country/<continen_code>`-API now only takes arguments with length `2`.
  - all other requests are not executed, instead aborted with error `400` (Bad Request)
- reformat all `html` templates

#### Features

- add popover to the publish name and email checkbox
- a `?` is now present. When hovering over it, a help message is displayed
