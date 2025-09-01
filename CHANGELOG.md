# Change Log

## 5.15.0 (2025-09-01)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Features

- Added an `overwrite` flag to [`CustomData`](CustomData), used as the `overwrite` parameter during tracking.
- [`CustomData`](CustomData) can now be created using a `name`, in addition to the existing method of using an `index`.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.15.0

## 5.14.6 (2025-08-20)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Patch Changes

- Corrected the logic for sending tracking data to comply with GDPR requirements.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.14.5

## 5.14.5 (2025-08-13)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Patch Changes

- Fixed an issue where using [`getRemoteVisitorData`][getRemoteVisitorData] with `personalization=true` or [`evaluateAudiences`][evaluateAudiences] could cause a visitor’s targeting data to be unexpectedly removed from storage.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.14.4

## 5.14.4 (2025-08-12)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Patch Changes

- Fixed an issue where [`Cookie`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#cookie) would throw an exception when parsing from a string if the cookie value was empty.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.14.3

## 5.14.3 (2025-08-04)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Patch Changes

- Fixed the missing **SDK version** parameter in the bundle, which caused incorrect tracking URLs and prevented proper evaluation of the [SDK Language](https://help.kameleoon.com/target-groups-of-users-with-rules) condition.

## 5.14.2 (2025-08-01)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Patch Changes

- Fixed an issue where [`setLegalConsent()`][setLegalConsent] automatically triggered [`flush()`][flush], which could cause extra latency in serverless or edge environments (e.g., **Lambda@Edge**). It now requires an explicit `flush()`, giving developers full control over data submission.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.14.2

## 5.14.1 (2025-07-30)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Patch Changes

- Improved error logging when parsing [`defaultDataFile`](defaultDataFile) - now provides more informative messages for easier debugging.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.14.1

[defaultDataFile]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#configuration-parameters

## 5.14.0 (2025-07-24)

> [!WARNING]
> If you're upgrading from a version earlier than 5.14.0 and run into any unexpected build or SDK-related issues, please reach out to the Kameleoon Support Team. We're here to ensure your transition is smooth and will promptly address any concerns.

### Features

- Migrated the build system for the NPM package from Babel (which previously generated multiple minified JS files) to Rollup, producing a single, optimized bundle.
  - Significantly reduced package size by consolidating files and improving tree-shaking.
  - Added native ESM support via modern Rollup outputs for better compatibility with modern bundlers.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.14.0

## 5.13.0 (2025-07-23)

### Features

- Added the [`evaluateAudiences`][evaluateAudiences] method. This method iterates over all Audiences Explorer segments, evaluates each one, and tracks the segments for which the visitor is targeted using the [`TARGETINGSEGMENT`](https://developers.kameleoon.com/apis/data-api-rest/all-endpoints/post-visit-events/) event.

### Patch Changes

- Fixed an issue where `defaultDataFile` loaded configuration incorrectly when using the new [v3 data file format](sdk-config.kameleoon.eu/v3/<sitecode>).
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.13.0

[evaluateAudiences]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#evaluateaudiences

## 5.12.1 (2025-07-11)

### Patch Changes

- Stability and performance improvements
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.12.1

## 5.12.0 (2025-07-10)

### Features

- Introducing a fallback configuration mechanism via the [`defaultDataFile`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#configuration-parameters) parameter. If no cached configuration is available, the SDK immediately uses the provided default. For version control, the SDK prioritizes the default configuration if its `dateModified` timestamp is more recent than the cached version.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.12.0

## 5.11.0 (2025-06-27)

### Features

- Added support for using a Custom Data value for traffic bucketing instead of the default visitor code. [Learn More](https://help.kameleoon.com/create-feature-flag/#Advanced_Flag_Settings).
- Added support for **304 (Not Modified)** responses from the SDK config service to avoid redundant updates and reduce traffic when the configuration hasn't changed.
- Added new optional parameter `instant` to the [`flush`][flush] method, allowing data to be sent to the server immediately without waiting for the next scheduled flush cycle.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.11.0

## 5.10.1 (2025-06-26)

### Patch Changes

- Stability and performance improvements
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.10.1

## 5.10.0 (2025-05-26)

### Features

- Added support for a **New**/**Returning** visitor breakdown filter in reports (requires calling [`getRemoteVisitorData`][getRemoteVisitorData]).

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.10.0

## 5.9.2 (2025-05-15)

### Patch Changes

- Fixed an issue with the [session merging][SessionMerging] feature that could prevent registered users from being correctly included in experiment results when they were linked to an anonymous user during the same visitor session.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.9.2

[SessionMerging]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#using-custom-data-for-session-merging

## 5.9.1 (2025-04-08)

### Patch Changes

- Changed the order in which **conversion** and **experiment** events are sent. This may lead to more accurate **visit**-level experiment reporting.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.9.1

## 5.9.0 (2025-03-24)

### Features

- Added new optional parameters `negative` and `metadata` to the [`trackConversion`](trackConversion) method.
- Added new optional parameter `metadata` to the [`Conversion`](Conversion) data constructor.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.9.0

[trackConversion]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#trackconversion
[Conversion]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#conversion

## 5.8.0 (2025-03-18)

### Features

- Added support for Contextual Bandit evaluations. Calling [`getRemoteVisitorData`][getRemoteVisitorData] with the `cbs=true` flag is required for this feature to function correctly. Platform-wide release expected in March 2025.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.8.0

[getRemoteVisitorData]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#getremotevisitordata

## 5.7.1 (2025-03-14)

### Patch Changes

- Fixed the evaluation of the targeting condition for [**New or Returning Visitors**](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#targeting-conditions-requiring-getremotevisitordata).
- Removed incorrect logging for the [`CustomData`](CustomData) condition when using the **has not been defined yet** operator.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.7.1

[CustomData]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#customdata

## 5.7.0 (2025-03-12)

### Features

- Reduced the number of technical requests to Data API servers to enhance performance and minimize the risk of [Too Many Requests](https://developers.kameleoon.com/apis/data-api-rest/all-endpoints/post-visit-events/) errors

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.7.0

## 5.6.1 (2025-03-05)

### Patch Changes

- Resolved all circular dependencies to improve stability.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.6.1

## 5.6.0 (2025-02-26)

### Features

- Added SDK support for **Mutually Exclusive Groups**. When feature flags are grouped into a **Mutually Exclusive Group**, only one flag in the group will be evaluated at a time. All other flags in the group will automatically return their default variation.

### Patch Changes

- Fixed validation for the [`networkDomain`][configurationParameters] parameter.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.6.0

## 5.5.0 (2025-02-10)

### Features

- Added SDK support for **holdout experiments**. Visitors assigned to a holdout experiment are excluded from all other rollouts and experiments, and consistently receive the default variation. For visitors not in a holdout experiment, the standard evaluation process applies, allowing them to be evaluated for all feature flags as usual. Platform-wide release expected in February 2025.
- Introduced a new `personalization` parameter to [`RemoteVisitorDataFilter`][getRemoteVisitorData]. Default value of the parameter is `false`.
- The following targeting conditions are now supported:
  - Exclusive Campaign
  - Experiment
  - Personalization

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.5.0

## 5.4.0 (2025-01-20)

### Features

- Added support for specifying a custom `Environment` value as a string in the [configuration parameters][configurationParameters], alongside the standard options.

[configurationParameters]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#configuration-parameters

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.4.0

## 5.3.0 (2025-01-17)

### Features

- Introduced a new `visitorCode` parameter to [`RemoteVisitorDataFilter`][getRemoteVisitorData]. This parameter determines whether to use the `visitorCode` from the most recent previous visit instead of the current `visitorCode`. When enabled, this feature allows visitor exposure to be based on the retrieved `visitorCode`, facilitating [cross-device reconciliation][CrossDevice]. Default value of the parameter is `true`.
- The mapping identifier is now persistent within a visitor session, ensuring that the assigned variation for a visitor remains unchanged when [merging sessions][mergingSessions] between anonymous and registered users.
- Added support for additional Data API servers worldwide, enabling faster network requests when the [`networkDomain`][configurationParameters] is manually configured.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.3.0

[CrossDevice]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#cross-device-experimentation
[getRemoteVisitorData]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getremotevisitordata
[mergingSessions]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#synchronizing-custom-data-across-devices
[configurationParameters]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#configuration-parameters

## 5.2.3 (2024-12-25)

### Patch Changes

- Enhanced the performance of the [`setLegalConsent()`][setLegalConsent] method.
- Resolved an issue that could lead to uncontrolled memory growth in specific scenarios.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.2.3

[setLegalConsent]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#setlegalconsent

## 5.2.2 (2024-12-19)

### Patch Changes

- Resolved an issue where the SDK could crash in certain scenarios when an error occurred during a request.
- Improved the consistency of logs for requests by updating similar messages and ensuring accurate display of both responses and errors.
- Implemented logging for EventSource status updates (connection, disconnection, and errors).
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.2.2

## 5.2.1 (2024-12-10)

### Patch Changes

- Replaced the nullish coalescing assignment operator (??=) with a more widely supported approach to ensure compatibility with older ES versions.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.2.1

## 5.2.0 (2024-12-09)

### Features

- Added support for **simulated** variations.
- Added the [`setForcedVariation()`][setForcedVariation] method. This method allows explicitly setting a forced variation for a visitor, which will be applied during experiment evaluation.

### Patch Changes

- Resolved an issue where the validation of [cookie domains][cookieDomain] for `localhost` resulted in incorrect failures. The SDK now accepts the provided domain without modification if it is deemed invalid and logs an [error][logLevels] to notify you of any issues with the specified domain.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.2.0

[setForcedVariation]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#setforcedvariation
[cookieDomain]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#configuration-parameters
[logLevels]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#log-levels

## 5.1.3 (2024-12-06)

### Patch Changes

- Fixed the issue with `off` variation not being added to `getEngineTrackingCode` result
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.1.3

## 5.1.2 (2024-12-05)

### Patch Changes

- Resolved an issue that caused server slowdowns when handling large numbers of unique visitors.
- Resolved an issue where setting the [`DEBUG`][loglevels] log level could cause unexpected crashes.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.1.2

[loglevels]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#log-levels

## 5.1.1

### Patch Changes

- Fixed the issue where Real-Time Update server failures could lead to SDK configuration update issues. If the Real-Time Update server fails SDK will now temporarily switch to polling mode until the Real-Time Update server is available again.
- Added an optional `onError` handler for [`IExternalEventSource`][iextrnaleventsource] interface. If the `onError` handler is not provided the SDK would not be able to handle Real-Time Update server failures. Note: no action is required when using default Kameleoon event source solutions.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.1.1

[iextrnaleventsource]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#eventsource

## 5.1.0 (2024-11-14)

### Features

- Enhanced top-level domain validation within the SDK. The implementation now includes automatic trimming of extraneous symbols.
- Enhanced [`logging`][logging]:
  - Introduced [`log levels`][loglevels]:
    - `None`
    - `Error`
    - `Warning`
    - `Info`
    - `Debug`
  - Added support for [`custom logger`][customlogger] implementations.
- Introduced new evaluation methods for clarity and improved efficiency when working with the SDK:
  - [`getVariation`][getVariation]
  - [`getVariations`][getVariations]
- Introduced methods replace the deprecated ones:
  - [`getFeatureFlags`][getFeatureFlags]
  - [`getVisitorFeatureFlags`][getVisitorFeatureFlags]
  - [`getActiveFeatureFlags`][getActiveFeatureFlags]
  - [`getFeatureFlagVariationKey`][getFeatureFlagVariationKey]
  - [`getFeatureFlagVariable`][getFeatureFlagVariable]
  - [`getFeatureFlagVariables`][getFeatureFlagVariables]
- A new version of the [`isFeatureFlagActive`][isFeatureFlagActive] method now has a new overload, which contains an optional `track` parameter for managing the assigned variation tracking (default: `true`).

### Patch Changes

- [`UniqueIdentifier`][uniqueidentifier] data is now correctly exported from the SDK
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.1.0

[logging]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#logging
[loglevels]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#log-levels
[customlogger]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#custom-handling-of-logs
[getVariation]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getvariation
[getVariations]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getvariations
[getFeatureFlags]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflags
[getVisitorFeatureFlags]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getvisitorfeatureflags
[getActiveFeatureFlags]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getactivefeatureflags
[getFeatureFlagVariationKey]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflagvariationkey
[getFeatureFlagVariable]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflagvariable
[getFeatureFlagVariables]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflagvariables
[isFeatureFlagActive]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#isfeatureflagactive

## 5.0.2 (2024-11-08)

### Patch Changes

- Fixed build issue resulting in potential issues when using any targeting condition with `Exclude` option
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.0.2

## 5.0.1 (2024-11-05)

### Patch Changes

- Fixed an issue with the [`Page URL`][Targeting Conditions] and [`Page Title`][Targeting Conditions] targeting conditions, where the condition evaluated all previously visited URLs in the session instead of only the current URL, corresponding to the latest added `PageView`
  NOTE: This change may impact your existing targeting. Please review your targeting conditions to ensure accuracy.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.0.1

[Targeting Conditions]: https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments#benefits-of-calling-getremotevisitordata

## 5.0.0 (2024-10-03)

### Breaking Changes

- `isUniqueIdentifier` parameter has been removed from methods [`flush`][flush], [`getRemoteVisitorData`][getremotevisitordata] and [`trackConversion`][trackconversion]
- Previously deprecated method [`onConfigurationUpdate`][onconfigurationupdate] has been removed from SDKs. Use [`onEvent`][onevent] method with `EventType.ConfigurationUpdate` to achieve the same effect.
- Previously deprecated field [`domain`][domain] of `SDKConfiguration` has been removed from SDKs. Use [`cookieDomain`][domain] field of `SDKConfiguration` instead.
- Parameter `text` of `KameleoonResponseType` used in custom [`requester`][requester] implementation is now mandatory, for the vast majority of implementations like `fetch`, `axios` or `node-fetch` it won't require any changes.
- SDK stopped using `node-fetch` dependency - that leads to external [`requester`][requester] becoming mandatory dependency. To make sure SDK works correctly make sure to install `@kameleoon/nodejs-requester` package or provide your implementation. Use [`sdk-installer`][sdk-installer] for more detailed information.
- `externalRequestDispatcher` was removed from an SDK - all its functionality can be covered by using custom `requester` implementation.
- SDK parameters [`integrations`][integrations] was removed along with its field [`externalClientConfiguration`][integrations], use custom [`requester`][requester] with [`RequestType.ClientConfiguration`][requesttype] to provide custom configuration instead.
- Static method [`KameleoonUtils.getClientConfigurationUrl`][getclientconfigurationurl] was removed - configuration url can be accessed using [`requester`][requester]

### Features

- Added new [`UniqueIdentifier`][uniqueidentifier] data to be used instead of removed `isUniqueIdentifier` parameters in some methods
- Added new [`SDKConfiguration`][sdkconfiguration] parameter `trackingInterval` to set the interval between SDK tracking network requests in _milliseconds_, default value is 1000, which is also maximum interval, minimum value is 100
- `FeatureVariableType` returned from the methods obtaining feature flag variables can now have two new `VariableType`s - `VariableType.JS` containing a `string` of JavaScript code and `VariableType.CSS` containing a string with CSS code
- Added [`compatibility`][domain] SDK parameter to set the compatibility mode for the SDK, default value is `Compatibility.Node16`, it can also be set to `Compatibility.Node14` or `Compatibility.Node12.

### Patch Changes

- [`getEngineTrackingCode`][getenginetrackingcode] method now correctly sets `triggerExperiment` parameter based on variable types
- Updated dependencies
  - @kameleoon/javascript-sdk-core@5.0.0

[getenginetrackingcode]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getenginetrackingcode
[uniqueidentifier]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#uniqueidentifier
[sdkconfiguration]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#arguments
[flush]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#flush
[getremotevisitordata]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getremotevisitordata
[trackconversion]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#trackconversion
[requester]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#requester
[sdk-installer]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#installation
[onconfigurationupdate]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#onconfigurationupdate
[onevent]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#onevent
[domain]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#configuration-parameters
[integrations]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#integration-with-edge-providers
[requesttype]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#parameters-1
[getclientconfigurationurl]: https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getclientconfigurationurl

## 4.4.8 (2024-09-09)

### Patch Changes

- It's now possible to create several SDK instances with different site codes
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.8

## 4.4.7 (2024-08-15)

### Patch Changes

- Fixed the issue with mapping identifier Custom Data not being set correctly after reading SDK configuration from a storage
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.6

## 4.4.6 (2024-08-08)

### Patch Changes

- Fixed an issue that caused duplicate entries in feature flag results for both anonymous and authorized/identified visitors during data reconciliation. This problem occurred when custom data of type mapping ID was not consistently sent for all sessions.
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.5

## 4.4.5 (2024-07-19)

### Patch Changes

- Fix previous release, which didn't contain all the described changes
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.4

## 4.4.4 (2024-07-19)

### Patch Changes

- Improved random generation for `nonce` values
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.3

## 4.4.3 (2024-07-16)

### Patch Changes

- Fixed the issue of `addData` method throwing an error after using `setLegalConsent`
- [`getVisitorCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getvisitorcode) now sets the visitor code to server `response`, custom `output` or Next.js `cookie` object correctly, when the visitor code was initially retrieved from it
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.2

## 4.4.2 (2024-07-12)

### Patch Changes

- `ClientConfiguration` and `RemoteData` Kameleoon Exceptions are now more informative
- [`getEngineTrackingCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#getenginetrackingcode) output code is now correctly overrides experiment variation assigned by JS Script
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.1

## 4.4.1 (2024-06-27)

### Patch Changes

- Resolved an issue where the custom `externals { requester }` was not applied to the KameleoonClient instance during initialization, causing the SDK to continue using the default one.

## 4.4.0 (2024-06-21)

### Features

- Added new [`networkDomain`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#1-initializing-the-kameleoon-client) parameter in `SDKConfigurationType` for configuring custom network domain for all outgoing requests.
- [`SDKConfigurationType`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#1-initializing-the-kameleoon-client) parameter `domain` was deprecated and will be removed in the next major version. Instead new `cookieDomain` is available.
- Added new optional [External Dependency](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#external-dependencies) - [Requester](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#requester) for implementing custom network request handler. The dependency will become mandatory in the next major release, a new package `@kameleoon/nodejs-requester` is available for use in place of `Requester`.
- Added new `KameleoonUtils` methods:
  - [`getCookieValue`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getcookievalue) for extracting cookie value from cookie string
  - [`simulateSuccessRequest`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#simulatesuccessrequest) for mocking successful network requests when implementing custom `Requester`
- [Integration](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#arguments) parameter is now deprecated and will be removed in the next major release. New [Requester](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#requester) external dependency covers all integration needs.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.4.0

## 4.3.0 (2024-05-24)

### Features

- Added new [`onEvent`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#onevent) method to handle SDK events with a callback.
- Method [`onConfigurationUpdate`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#onConfigurationUpdate) is now marked as `deprecated` and will be removed in the next major release. Use [`onEvent(EventType.ConfigurationUpdate, callback)`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#onevent) instead.
- Added support of range match type for numeric Custom Data values.

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.3.0

## 4.2.0 (2024-05-07)

### Features

- Added support for a new Kameleoon Visitor Code Manager interface - `IExternalCustomVisitorCodeManager` that allows providing custom visitor code manager with arbitrary `input` and `output` parameters.
- New method [`getActiveFeatureFlags`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#getactivefeatureflags) for retrieving feature flags that are active for visitor with detailed variation and variables information.

### Patch Changes

- Removed optional `NextJS` dependency
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.2.0

## 4.1.0 (2024-04-19)

### Features

- New [Likelihood to Convert](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#predefined-targeting-conditions) targeting condition.
- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getremotevisitordata) method now accepts new boolean parameter `isUniqueIdentifier` to obtain all linked visitors data when working with [Cross-device experimentation](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#cross-device-experimentation)
- Miscellaneous [Cross-device experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation) improvements

### Patch Changes

- Fixed the issue with when `_` variable was transformed to duplicate identifier `a` causing `TypeError`
- Improved visits data collection logic
- `Browser` condition could throw an error when the browser version wasn't specified on Kameleoon Platform
- `Geolocation` condition is now case insensitive
- SDK Core version is no more sent with tracking
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.1.0

## 4.0.1 (2024-02-21)

### Patch Changes

- Added support for additional Data API servers across the world for even faster network requests
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.0.1

## 4.0.0 (2024-02-16)

### Breaking Changes

- Previously deprecated `KameleoonUtils.getVisitorCode()` was removed
- NodeJS SDK now requires [providing external dependencies](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#1-initializing-the-kameleoon-client) for correct work

### Features

- [`getVisitorCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#kameleoonclient-getvisitorcode) method now has new overload for `NextJS` server actions `cookie` object.
- [`setLegalConsent`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#setlegalconsent) method now has new overload for `NextJS` server actions `cookie` object.
- Added [External Dependencies](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#external-dependencies) capabilities

### Patch Changes

- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.0.0

## 3.6.1 (2024-02-07)

### Bug fixes

- Tracking wasn't sent if consent is required

## 3.6.0 (2024-02-01)

### Features

- Add environment support to [getClientConfigurationUrl](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#kameleoonutils-getclientconfigurationurl)

## 3.5.0 (2024-01-18)

### Bug fixes

- SDK threw an error reading storage when migrating from older SDK versions

### Features

- Added new SDK `configuration` parameter [`requestTimeout`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#1-initializing-the-kameleoon-client), which defines maximum time in _milliseconds_ after which any SDK network request will fail

## 3.4.1 (2023-12-15)

### Bug fixes

- Fix nonce for `Conversion` data

## 3.4.0 (2023-12-12)

### Features

- Updated the [getFeatureFlagVariable](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflagvariable) method to return an object of type `FeatureFlagVariableType`
- Enhanced the [getFeatureFlagVariables](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflagvariables) method to include the `key` field in its return value.

### Bug fixes

- Custom Data mapping identifier wasn't tracked correctly

## 3.3.0 (2023-12-11)

### Features

- [flush](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#flush) and [trackConversion](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#trackConversion) methods now have a new optional parameter `isUniqueIdentifier` used for extra [Kameleoon Cross-device Experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation) capabilities
- [getVisitorCode](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getvisitorcode) and [setLegalConsent](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#setlegalconsent) methods now have an overload allowing methods to be used without parameters (instead of providing and empty object `{}`)

### Bug fixes

- Targeting data cleanup caused `TypeError`

## 3.2.0 (2023-11-30)

### Features

- [CustomData session merging](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#using-custom-data-for-session-merging) abilities for [Kameleoon Cross-device Experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation)

## 3.1.0 (2023-11-24)

### Features

- Added `setLegalConsent` method to determine the types data Kameleoon includes in tracking requests. This helps you adhere to legal and regulatory requirements while responsibly managing visitor data. You can find more information in the [Consent management policy](https://help.kameleoon.com/consent-management-policy).

## 3.0.0 (2023-11-16)

### Breaking change

- SDK stopped the support of the following methods were:
  - `getExperiments`
  - `getVisitorExperiments`
  - `triggerExperiment`
- Previously deprecated `flushData` method was removed
- [`KameleoonClient`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#arguments) constructor parameters now have mandatory `clientId` and `clientSecret` fields
- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getremotevisitordata) method parameters was changed to an object with type [`RemoteVisitorDataParamsType`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#parameters-12) that has a new `filters` field

### Features

- New method for retrieving multiple feature flag variables - [`getFeatureFlagVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getfeatureflagvariables)
- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getremotevisitordata) is now capable of retrieving information from up to 25 visits along with some additional visit information configured by new `filters` field
- [`PageView`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#pageview) data items are now stored by unique URL with timestamps of visits - each visitor can have several `PageView` URLs stored
- [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#conversion) data items are now stored as a list of conversion for each visitor
- [Cross Device Synchronization](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#synchronizing-custom-data-across-devices) was improved - [`CustomData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#customdata) with `Visitor` scope is always re-sent with tracking calls allowing seamless synchronization using [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getremotevisitordata)
- [New targeting conditions](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#list-of-supported-targeting-conditions) are now available (some of them may require [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getremotevisitordata) pre-loaded data)
  - `Browser Cookie`
  - `Application Version`
  - `Operating System`
  - `IP Geolocation`
  - `Segment`
  - `Target Feature Flag`
  - `Previous Page`
  - `Number of Page Views`
  - `Time since First Visit`
  - `Time since Last Visit`
  - `Number of Visits Today`
  - `Total Number of Visits`
  - `New or Returning Visitor`
- New Kameleoon Data types were introduced:
  - [`ApplicationVersion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#applicationversion)
  - [`Cookie`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#cookie)
  - [`OperatingSystem`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#operatingsystem)
  - [`GeolocationData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#geolocationdata)

### Bug fixes

- `SDKParameters` type is now correctly exported from SDK
- SDK Polling re-tries mechanism was optimized - SDK will now try to obtain configuration again during the next poll after 3 failed configuration loading attempts
- [`onConfigurationUpdate`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#onconfigurationupdate) callback now fires on successful configuration update in storage (previously fired after network configuration retrieval)

## 2.8.1 (2023-10-20)

### Bug fixes

- Fix previous version deploy issue

## 2.8.0 (2023-10-20)

### Features

- Added new method [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#getvisitorwarehouseaudience)

## 2.7.1 (2023-10-11)

### Bug fixes

- Storage data parse overhead optimization

## 2.7.0 (2023-09-25)

### Features

- Added `getClientConfigurationUrl` utility

## 2.6.3 (2023-09-05)

### Bug fixes

- `UserAgent` was not exported from SDK

## 2.6.2 (2023-08-31)

### Bug fixes

- `Custom Data Condition` now handles index `0` properly

## 2.6.1 (2023-08-25)

### Bug fixes

- Multiple `Real Time Update` connections are no longer created
- `Custom Data Condition` now handles all exceptions properly

## 2.6.0 (2023-08-11)

### Bug fixes

- Empty Custom Data is now sending activity tracking event

### Features

- Added [Tracking requests rate limit](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#tracking-rate-limit) capabilities
- Added [Cross Device Custom Data Synchronization](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#cross-device-custom-data-synchronization) capabilities

## 2.5.0 (2023-07-21)

### Features

- `flushData` has been deprecated in favor of [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#flush).

## 2.4.1 (2023-07-17)

### Bug fixes

- Typescript `.d.ts` files have proper relative path resolution.
- Unused tracking parameters are no longer sent.
- Real-time update events now get the latest configuration.

### Features

- Minor optimization for checking [targeting conditions](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk/#list-of-supported-targeting-conditions) of a segment.

## 2.4.0 (2023-07-04)

### Features

- Deno support

## 2.3.1 (2023-06-30)

### Bug fixes

- Tracking data duplications

## 2.3.0 (2023-06-28)

### Bug fixes

- Improve error handling for [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#obtain-custom-data-from-kameleoon-data-api)
- Visitor code is now validated correctly in every method that uses it.
- Result bundle is now compatible with systems not using `ESM` and `CommonJS`. It's minimized and uses code splitting for `crypto-js` `sha256` function.
- Parameter `revenue` for [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#conversion) is now optional.
- Each visitor can now only have one type of associated [`Kameleoon Data Type`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#data-types), except for [`CustomData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#customdata), that a visitor can have one per `customDataIndex`.

### Features

- New conditions are now supported: `Device`, `Browser`, `SDKLanguage`, `Page Title`, `Page View`, `Visitor Code`, `Conversion`. See the [full list of supported conditions](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#list-of-supported-targeting-conditions).
- [`Browser`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#browser) now has new optional parameter `version`.
- [`flushData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#flush-tracking-data) `visitorCode` parameter is now optional.
- Custom data that is marked as `local only` on Kameleoon Platform is now only used for targeting (not flushed with tracking requests).

## 2.2.5 (2023-06-01)

### Bug fixes

- Empty visitor code is no more allowed
- Incorrect tracking body upon triggering an experiment

## 2.2.4 (2023-05-31)

### Bug fixes

- Improve targeting data cleanup interval handling

## 2.2.3 (2023-05-24)

### Bug fixes

- Fixed issue for sending unique `Nonce` parameter on tracking requests

## 2.2.2 (2023-05-21)

### Bug fixes

- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#obtain-custom-data-from-kameleoon-data-api) current visits not being up-to-date

## 2.2.1 (2023-05-20)

### Bug fixes

- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#obtain-custom-data-from-kameleoon-data-api) data parse error

## 2.2.0 (2023-05-19)

### Features

- Added method [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#obtain-custom-data-from-kameleoon-data-api)

## 2.1.4 (2023-05-16)

### Bug fixes

- Cookies now correctly set for Next JS SSR

## 2.1.3 (2023-04-24)

### Bug fixes

- Tracking feature flag rule with variation `off` wasn't displayed on result page

## 2.1.2 (2023-04-22)

### Bug fixes

- core dependency fix

## 2.1.1 (2023-04-18)

### Bug fixes

- Visitor code cookie header is now set correctly

## 2.1.0 (2023-04-14)

### Features

- Added method [`getExperimentVariationData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#get-experiment-variation-data)
- Added method [`getEngineTrackingCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#sending-exposure-events-to-external-tools)
- Targeting data cleanup interval is now [`optional`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#1-initializing-the-kameleoon-client) and is set to `30` minutes
- [`getFeatureFlagVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#get-variation-key-for-a-certain-feature-flag), [`getFeatureFlagVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#get-a-variable-of-a-certain-feature-flag), [`isFeatureFlagActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/nodejs-sdk#check-if-the-feature-is-active-for-visitor) methods do not check previously allocated variation, rather recalculate it each time. Same methods now send tracking request for any rule type (previously only for `Experementation` rule)

### Bug fixes

- `variationId` is undefined when using feature flag related methods

### Bug fixes

- add node-fetch to dependency

## 2.0.0 (2023-04-05)

### Features

- Integration of compute edge

## 1.1.0 (2023-03-22)

### Features

- License changed from `GPL3.0` to `ISC`

## 1.0.0 (2023-03-21)

### Features

- Initial Release
