# Changelog
All changes to the Kameleoon Client Server-Side SDK for Node.js will be documented in this file.

## 3.3.0 - 2023-02-27
- Added method:
    - [`isFeatureActive`](https://developers.kameleoon.com/nodejs-sdk.html#isFeatureActive) (added instead of deprecated method `activateFeature`)
- Renaming of exceptions:
    - `NotActivated` -> `NotAllocated`

## 3.2.0 - 2023-02-16

- Added [`initialize`](https://developers.kameleoon.com/nodejs-sdk.html#initialize) method
- `fs` module is now only imported if the file system configuration is being used

## 3.1.2 - 2023-01-20
* Removed `blocking` parameter from initilization method

## 3.1.1 - 2022-12-14
* Added support of `is among the values` operator for Custom Data

## 3.1.0 - 2022-12-09
* `activateFeature` & `obtainFeatureVariable` are deprecated.
* Renaming of methods (old methods marked as deprecated and will be removed later):
    - `obtainVisitorCode` -> [`getVisitorCode`](https://developers.kameleoon.com/nodejs-sdk.html#getVisitorCode)
    - `obtainVariationAssociatedData` -> [`getVariationAssociatedData`](https://developers.kameleoon.com/nodejs-sdk.html#obtainVariationAssociatedData)
    - `obtainFeatureAllVariables` -> [`getFeatureAllVariables`](https://developers.kameleoon.com/nodejs-sdk.html#getFeatureAllVariables)
    - `obtainExperimentList` -> [`getExperimentList`](https://developers.kameleoon.com/nodejs-sdk.html#getExperimentList)
    - `obtainExperimentListForVisitorCode` -> [`getExperimentListForVisitorCode`](https://developers.kameleoon.com/nodejs-sdk.html#getExperimentListForVisitorCode)
    - `obtainFeatureList` -> [`getFeatureList`](https://developers.kameleoon.com/nodejs-sdk.html#getFeatureList)
    - `obtainFeatureListForVisitorCode` -> [`getFeatureListForVisitorCode`](https://developers.kameleoon.com/nodejs-sdk.html#getFeatureListForVisitorCode)

## 3.0.3 - 2022-12-01
* Minor bug fixing for tracking calls

## 3.0.2 - 2022-12-01
* Minor bug fixing

## 3.0.1 - 2022-11-25
* Minor bug fixing

## 3.0.0 - 2022-11-25
* [`triggerExperiment`](https://developers.kameleoon.com/nodejs-sdk.html#triggerexperiment) and [`activateFeature`](https://developers.kameleoon.com/nodejs-sdk.html#activatefeature) are synchronized methods now.
* Added support of new feature flag rules.
* Added possibility to set [`UserAgent`](https://developers.kameleoon.com/nodejs-sdk.html#useragent).

## 2.1.8 - 2022-07-29
* Minor bug fixes

## 2.1.7 - 2022-06-14
* Fixed an issue when tracking data could be sent twice. Related to: [`triggerExperiment`](https://developers.kameleoon.com/nodejs-sdk.html#triggerexperiment) & [`activateFeature`](https://developers.kameleoon.com/nodejs-sdk.html#activatefeature)

## 2.1.6 - 2022-05-31
* Added Support **Experiment** & **Exclusive Campaign** conditions. Related to [`triggerExperiment`](https://developers.kameleoon.com/nodejs-sdk.html#triggerexperiment)
* Fixed an issue when an user which was already registered with a variation gets new randomly selected variation. Related to [`triggerExperiment`](https://developers.kameleoon.com/nodejs-sdk.html#triggerexperiment)
* Added update campaigns and feature flag configurations instantaneously with Real-Time Streaming Architecture: [`documentation`](https://developers.kameleoon.com/nodejs-sdk.html#streaming) or [`product updates`](https://www.kameleoon.com/en/blog/real-time-streaming)
* Added a new method [`onUpdateConfiguration`](https://developers.kameleoon.com/nodejs-sdk.html#onUpdateConfiguration) to handle events when configuration data is updated in real time.

## 2.1.5 - 2022-05-10
* Added KameleoonData [`Device`](https://developers.kameleoon.com/nodejs-sdk.html#device) data. Possible values are: **PHONE**, **TABLET**, **DESKTOP**.
* Removed KameleoonData `Interest`

## 2.1.4 - 2022-04-18
* Added method to obtain a list of feature flags: [`obtainFeatureList`](https://developers.kameleoon.com/nodejs-sdk.html#obtainfeaturelist)
* Added method to obtain a list of feature flags targeted for specified visitor code: [`obtainFeatureListForVisitorCode`](https://developers.kameleoon.com/nodejs-sdk.html#obtainfeaturelistforvisitorcode)
* Added method to obtain a list of experiments: [`obtainExperimentList`](https://developers.kameleoon.com/nodejs-sdk.html#obtainexperimentlist)
* Added method to obtain a list of experiments targeted for specified visitor code: [`obtainExperimentListForVisitorCode`](https://developers.kameleoon.com/nodejs-sdk.html#obtainexperimentlistforvisitorcode)
* Added method to obtain all variables for feature flag: [`obtainFeatureAllVariables`](https://developers.kameleoon.com/nodejs-sdk.html#obtainfeatureallvariables)
* Added an indication of feature flag (Id, Key) when exception happens. Related to [`activateFeature`](https://developers.kameleoon.com/nodejs-sdk.html#activatefeature), [`obtainFeatureVariable`](https://developers.kameleoon.com/nodejs-sdk.html#obtainfeaturevariable)
* Added an indication of experiment (Id) when exception happens. Related to [`triggerExperiment`](https://developers.kameleoon.com/nodejs-sdk.html#triggerexperiment)


## 2.1.3 - 2022-04-12
* Added method for retrieving data from remote source: [`retrieveDataFromRemoteSource`](https://developers.kameleoon.com/nodejs-sdk.html#retrievedatafromremotesource)

## 2.1.2 - 2022-02-28
* Improving token fetching
* Added support of multi-environment for feature flags, Related to [`activateFeature`](https://developers.kameleoon.com/nodejs-sdk.html#activatefeature), [`obtainFeatureVariable`](https://developers.kameleoon.com/nodejs-sdk.html#obtainfeaturevariable)


## 2.1.1 - 2022-02-01
* Added checking for status of site_code (Enable / Disable). Related to [`activateFeature`](https://developers.kameleoon.com/nodejs-sdk.html#activatefeature) and [`triggerExperiment`](https://developers.kameleoon.com/nodejs-sdk.html#triggerexperiment)
* Added scheduling functionality for [`activateFeature`](https://developers.kameleoon.com/nodejs-sdk.html#activatefeature)

## 2.1.0 - 2021-09-29
* Improving SDK stability

## 2.0.9 - 2021-06-16
* Add DEVIATED status

## 2.0.8 - 2021-06-10
* Update dependencies
* Add typescript types
