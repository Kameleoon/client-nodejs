# Kameleoon NodeJS SDK

## Introduction

Kameleoon NodeJS SDK is used to work with Kameleoon Feature Flags and Experiments using native NodeJS api.
Integration of this SDK on server is easy, and its footprint is low.

This page describes the most basic `KameleoonClient` configuration, for more in-depth review of all the methods and configuration options follow [Official Kameleoon Documentation](https://developers.kameleoon.com/nodejs-sdk.html)

## Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Using KameleoonClient (Recommended)](#using-kameleoonclient-recommended)
- [Legacy KameleoonUtils Method (Deprecated)](#legacy-kameleoonutils-method-deprecated)

## Installation

- **npm** - `npm install @kameleoon/nodejs-sdk`
- **yarn** - `yarn add @kameleoon/nodejs-sdk`
- **pnpm** - `pnpm add @kameleoon/nodejs-sdk`

## Configuration

1. Obtain your site code from [Kameleoon Platform](https://app.kameleoon.com/)
2. Create client instance

```ts
import { KameleoonClient } from '@kameleoon/nodejs-sdk';

const client = new KameleoonClient({ siteCode: 'my_site_code' });
```

3. Asynchronously initialize client to fetch the configuration from remote server and handle possible errors

```ts
try {
  await client.initialize();
} catch (error) {
  // Handle error
}
```

## Using KameleoonClient (Recommended)

1. `KameleoonClient` is ready to go! Fetch the visitor code and add Custom Data:

```ts
const visitorCode = KameleoonClient.getVisitorCode({
  request: req, // `NodeJS/NextJS/Deno` request object
  response: res, // `NodeJS/NextJS/Deno` response object
});
const customDataIndex = 0;

// -- Add targeting data
client.addData(visitorCode, new CustomData(customDataIndex, 'my_data'));
```

2. Check if a feature is active for a visitor:

```ts
const isMyFeatureActive = client.isFeatureFlagActive(
  visitorCode,
  'my_feature_key',
);
```

## Legacy KameleoonUtils Method (Deprecated)

> **Note:** The `getVisitorCode` method from `KameleoonUtils` is deprecated. We recommend using `getVisitorCode` from `KameleoonClient` for new implementations, as it correctly handles legal consent requirements.

1. Fetch the visitor code and add Custom Data:

```ts
const visitorCode = KameleoonUtils.getVisitorCode({
  domain: 'www.example.com',
  request: req, // `NodeJS/NextJS/Deno` request object
  response: res, // `NodeJS/NextJS/Deno` response object
});
const customDataIndex = 0;

// -- Add targeting data
client.addData(visitorCode, new CustomData(customDataIndex, 'my_data'));
```

2. Check if a feature is active for a visitor:

```ts
const isMyFeatureActive = client.isFeatureFlagActive(
  visitorCode,
  'my_feature_key',
);
```
