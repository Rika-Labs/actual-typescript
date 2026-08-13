# Waitlist

## Overview

Unauthenticated early-access registration.

### Available Operations

* [joinWaitlist](#joinwaitlist) - Join the early-access waitlist

## joinWaitlist

Registers an email address for Actual early access. Repeated addresses return the same response and do not reveal prior membership.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="joinWaitlist" method="post" path="/v1/waitlist" -->
```typescript
import { Actual } from "@rikalabs/actual";

const actual = new Actual();

async function run() {
  const result = await actual.waitlist.joinWaitlist({
    email: "Dante21@gmail.com",
    source: "landing",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ActualCore } from "@rikalabs/actual/core.js";
import { waitlistJoinWaitlist } from "@rikalabs/actual/funcs/waitlist-join-waitlist.js";

// Use `ActualCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const actual = new ActualCore();

async function run() {
  const res = await waitlistJoinWaitlist(actual, {
    email: "Dante21@gmail.com",
    source: "landing",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("waitlistJoinWaitlist failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [models.JoinWaitlistRequest](../../models/join-waitlist-request.md)                                                                                                            | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.JoinWaitlistResponse](../../models/join-waitlist-response.md)\>**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.InvalidJsonResponseError         | 400                                     | application/json                        |
| errors.InvalidEmailResponseError        | 422                                     | application/json                        |
| errors.WaitlistUnavailableResponseError | 503                                     | application/json                        |
| errors.ActualDefaultError               | 4XX, 5XX                                | \*/\*                                   |