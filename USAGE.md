<!-- Start SDK Example Usage [usage] -->
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
<!-- End SDK Example Usage [usage] -->