# Changelog
All changes to the Kameleoon Client Server-Side SDK for Node.js will be documented in this file.

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
