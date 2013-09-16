jspm Registry
---

Pull requests welcome!

While the registry is small enough, all registry entries are managed through Github, moderated by the registry maintainers.

* The registry provides a mapping from a unique registry name (`jquery`), to a target package (`github:components/jquery` / `npm:jquery`).
* For ease of reference, please ensure new names are added in the correct alphabetical location.
* An optional `main` entry point can be specified with `#main-file-name`. For example:
  
  `"jquery": "github:components/jquery#jquery"

  will map:

  * `jquery`           -> `github:components/jquery/jquery`
  * `jquery/submodule` -> `github:components/jquery/submodule`

  It is simply a shorthand for specifying the main entry point when the package is requested directly by name.

* Currently the following `locations` are available in the registry mapping:

  * `github:*`: Maps to the Github service.
  * `npm:*`   : Maps to the NPM service.

  In this way, any package on Github or NPM is available for reference in the jspm registry.

  Additional locations are in planning for other servies. Anyone can provide a location service. To provide a new
  location service, see the Location Service Guidelines, then contact us directly to have your location service 
  included in jspm.


Package Overrides
---

The registry also provides a `package.json` override system.

All jspm package configuration options are specified in the `package.json` file for packages. The jspm `package.json`
extension properties are documented here. Often changes need to be made to packages one may not have maintainer access to. 
In this case, submit the `package.json` as an override in this repo to override the `package.json` file jspm uses for a given package.

The overrides are located in the `package-overrides` folder of this repo, with the folder format:

`package-overrides/[location-name]/[location-path]@[version].json`

Only exact semver versions can be used, excluding semver build numbers and suffices.

For example, a package override for `jquery` would be located at:

`package-overrides/github/jquery/jquery@2.0.0.json`