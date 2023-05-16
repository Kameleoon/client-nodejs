# Change Log

All notable changes to this project will be documented in this file.

[Project Homepage](https://developers.kameleoon.com/nodejs-sdk.html)

# 2.1.4 (2023-05-16)


### Bug fixes

* Cookies now correctly set for Next JS SSR

# 2.1.3 (2023-04-24)


### Bug fixes

* Tracking feature flag rule with variation `off` wasn't displayed on result page

# 2.1.2 (2023-04-22)


### Bug fixes

* core dependency fix

# 2.1.1 (2023-04-18)


### Bug fixes

* Visitor code cookie header is now set correctly

# 2.1.0 (2023-04-14)

### Features

* Added method [`getExperimentVariationData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#get-experiment-variation-data)
* Added method [`getEngineTrackingCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#sending-exposure-events-to-external-tools)
* Targeting data cleanup interval is now [`optional`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#1-initializing-the-kameleoon-client) and is set to `30` minutes
* [`getFeatureFlagVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#get-variation-key-for-a-certain-feature-flag), [`getFeatureFlagVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#get-a-variable-of-a-certain-feature-flag), [`isFeatureFlagActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#check-if-the-feature-is-active-for-visitor) methods do not check previously allocated variation, rather recalculate it each time. Same methods now send tracking request for any rule type (previously only for `Experementation` rule)

### Bug fixes

* `variationId` is undefined when using feature flag related methods

### Bug fixes

* add node-fetch to dependency

# 2.0.0 (2023-04-05)


### Features

* Integration of compute edge

# 1.1.0 (2023-03-22)


### Features

- License changed from `GPL3.0` to `ISC`

# 1.0.0 (2023-03-21)


### Features

* Initial Release
