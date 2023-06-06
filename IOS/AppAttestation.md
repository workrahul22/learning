## For IOS v14 and above the implementation is multi-sstep back and forth communication between an IOS app, a backend service, and the apple app attest service to construct and validate the attestation token.


## Every time your app needs to communicate attestation data to your server, the app first asks the server for a wunique, one-time challenge. App attest integrates this challenge into the objects that it provides, and that your app sends back to your server for validation. This makes it harder for an attacker to implement a replay attack.

## How it works?

* The IOS app interacts with Apple App attest service to get key identifier.

* The IOS app then asks its backend service for the first challenge string.

* The backend service generated the first challenge, saves it in a database record, and returns to the app.

* The IOS app uses this challenge and the key identifier received in step 1 to fetch an attestation token from App attest service.

* The IOS app then sends this attestation token and key identifier to the backend service for validation.

* The beackend sevice decodes/parses the attestation token to validate. It should looks like this.

{
    fmt,
    attStmt: {
        x5c: [],
        receipt: []
    },
    authData: []
}

* If the validation passes on the backend, then the service saves the credCert (first buffer in the decoded x5c arrays) value and another newly generated second challenge string into the database record.

* The backend service sends this second challenge back to the IOS app.

* The IOS app uses this second challenge to generate an assertion token from App attest service corresponding to a request body.

* The IOS app then sends this assertion token in the successive API requests to backend for validation.

* The backend service decodes/parses the assertion token to validate. It should look this
{
    signature: [],
    authenticatorData: []
}

* The backend service validates this assertion token before proceddint to execute the API call.
