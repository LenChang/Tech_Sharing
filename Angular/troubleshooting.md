# API Response: 200 (OK) with error - ERR_CONTENT_LENGTH_MISMATCH
> This issue happens because the download speed of your device is limited, and the server raises a timeout to break the connection before the necessary angular js files are downloaded.
## Reference
- https://stackoverflow.com/questions/58880302/angular-8-get-styles-js-neterr-content-length-mismatch-200-ok-when-served

# Add typing manually for library
> src/typings.d.ts
## Sample Code
```typescript
// src/typings.d.ts
declare module 'host' {
   export interface Host {
     protocol?: string;
     hostname?: string;
     pathname?: string;
   }
   export function parse(url: string, queryString?: string): Host;
}
```
```typescript
import * as host from 'host';
const parsedUrl = host.parse('https://angular.io');
console.log(parsedUrl.hostname);
```
## Reference
- https://angular.dev/tools/libraries/using-libraries#library-typings
