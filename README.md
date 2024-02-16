# Kameleoon NodeJS SDK

## Introduction

Kameleoon NodeJS SDK is used to work with Kameleoon Feature Flags and Experiments using native NodeJS api.
Integration of this SDK on server is easy, and its footprint is low.

This page describes the most basic `KameleoonClient` configuration, for more in-depth review of all the methods and configuration options follow [Official Kameleoon Documentation](https://developers.kameleoon.com/nodejs-sdk.html)

## Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage Example](#usage-example)
- [External Dependencies](#external-dependencies)

## Installation

- **npm** - `npm install @kameleoon/nodejs-sdk`
- **yarn** - `yarn add @kameleoon/nodejs-sdk`
- **pnpm** - `pnpm add @kameleoon/nodejs-sdk`
- **bun** - `bun install @kameleoon/nodejs-sdk`

## Configuration

1. Obtain your site code and credentials from [Kameleoon Platform](https://app.kameleoon.com/)
2. Instantiate a client providing [external dependencies](#external-dependencies).

```ts
import { KameleoonClient } from '@kameleoon/nodejs-sdk';
import { KameleoonVisitorCodeManager } from '@kameleoon/nodejs-visitor-code-manager';
import { KameleoonEventSource } from '@kameleoon/nodejs-event-source';

const client = new KameleoonClient({
  siteCode: 'my_site_code',
  credentials: {
    clientId: 'my_id',
    clientSecret: 'my_secret',
  },
  externals: {
    visitorCodeManager: new KameleoonVisitorCodeManager(),
    eventSource: new KameleoonEventSource(),
  },
});
```

## Usage Example

```ts
// -- Wait for the client initialization
await client.initialize();

// -- Generate or obtain a visitor code
const visitorCode = KameleoonClient.getVisitorCode({
  request: req, // `NodeJS/NextJS/Deno` request object
  response: res, // `NodeJS/NextJS/Deno` response object
});

// -- Add targeting data
const customDataIndex = 0;
client.addData(visitorCode, new CustomData(customDataIndex, 'my_data'));

// -- Check if the feature flag is active
const isActive = client.isFeatureFlagActive(
  visitorCode,
  'my_feature_key',
);
```

## External Dependencies

NodeJS SDK utilizes certain external dependencies, which are required to be able to use specific API when working in different contexts.

There are several possible external dependencies used by Kameleoon NodeJS SDK, some of them have default Kameleoon implementations in form of external npm packages, while other are SDK built-ins, but can still be re-implemented by the developers using an SDK.

Here is the list of such dependencies:

- `visitorCodeManager`_(mandatory)_ is responsible for managing the visitor code and cookies, it has several default Kameleoon implementations:
  - `@kameleoon/nodejs-visitor-code-manager`
  - `@kameleoon/nextjs-visitor-code-manager`
  - `@kameleoon/deno-visitor-code-manager`
- `eventSource`_(madatory)_ is responsible for Real Time Updates(Streaming) for SDK, it has one default Kameleoon implementation:
  - `@kameleoon/nodejs-event-source` (suitable for NodeJS/Deno/NextJS)
- `storage`_(optional)_ is responsible for storing all SDK related data, it has a built-in implementation in the SDK.

Following is the example implementation for each dependency.

### visitorCodeManager

```ts
import { IExternalVisitorCodeManager, GetDataParametersType } from "@kameleoon/nodejs-sdk";

class MyVisitorCodeManager implements IExternalVisitorCodeManager {
  // - Get visitor code from `request` cookie
  public getData({ request, key }: GetDataParametersType): string | null {
    const cookieString = request.headers.cookie;

    if (!cookieString) {
      return null;
    }

    const cookieEntry = cookieString
      .split(' ;')
      .find((keyValue) => {
        const [cookieKey, cookieValue] = keyValue.split('=');

        return cookieKey === key && cookieValue !== '';
      });

    if (cookieEntry) {
      const [_, value] = cookieEntry.split('=');

      return value;
    }

    return null;
  }

  // - Set visitor code to `response` cookie
  public setData({
    visitorCode,
    response,
    domain,
    maxAge,
    key,
    path,
  }: SetDataParametersType): void {
    let resultCookie = `${key}=${visitorCode}; Max-Age=${maxAge}; Path=${path}`;

    if (domain) {
      resultCookie += `; Domain=${domain}`;
    }

    response.setHeader('Set-Cookie', resultCookie);
  }
}
```

### eventSource

```ts
import { IExternalEventSource } from "@kameleoon/nodejs-sdk";

class MyEventSource implements IExternalEventSource {
  private eventSource?: EventSource;

  public open({
    eventType,
    onEvent,
    url,
  }: EventSourceOpenParametersType): void {
    // - Use any suitable EventSource implementation here
    const eventSource = new EventSource(url);

    this.eventSource = eventSource;
    this.eventSource.addEventListener(eventType, onEvent);
  }

  public close(): void {
    if (this.eventSource) {
      this.eventSource.close();
    }
  }
}
```

### storage

```ts
import { IExternalStorage } from "@kameleoon/nodejs-sdk";

const storage = new Map();

class MyStorage<T> implements IExternalStorage<T> {
  public read(key: string): T {
    // - Utilize the storage implementation of your choice
    const data = storage.get(key);

    // - Optionally handle errors
    if (!data) {
      throw new Error("Couldn't read data from myStorage");
    }

    return data;
  }

  public write(key: string, data: T): void {
    storage.set(key, data);
  }
}
```
