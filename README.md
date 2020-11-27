# LCZ-Generator-Issues

Use this repository to create issues for the [LCZ-Generator](https://lcz-generator.geographie.ruhr-uni-bochum.de/).

- if you think your issue might be sensitive [reach out directly to us](mailto:info@wudapt.org).

## Changelog

### 0.0.0b4

#### Bugfixes
- fixed a bug where the country selection was not kept when reloading the page or after beeing redirected from the same page

#### Modifications

- the `/country/<continen_code>`-API now only takes arguments with length `2`.
  - all other requests are not executed, instead aborted with error `400` (Bad Request)
- reformat all `html` templates

#### Features

- add popover to the publish name and email checkbox #47
- a `?` is now present. When hovering over it, a help message is displayed
