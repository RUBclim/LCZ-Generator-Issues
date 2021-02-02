[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/RUBclim/LCZ-Generator-Issues/master.svg)](https://results.pre-commit.ci/latest/github/RUBclim/LCZ-Generator-Issues/master)

# LCZ-Generator-Issues

Use this repository to create issues for the [LCZ-Generator](https://lcz-generator.geographie.ruhr-uni-bochum.de/).

- if you think your issue might be sensitive [reach out directly to us](mailto:info@wudapt.org).

## Changelog

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
