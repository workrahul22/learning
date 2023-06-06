## The SafetyNet Attestation API is an anti-abuse API that allows app developers to assess the Android device their app is running on. The API should be used as a part of your abuse detection system to help determine whether your servers are interacting with your genuine app running on a genuine Android device.


## How it works

* Android app interacts with Google SafetyNet Attestation API to construct an attestation token formatted in JSON Web Signature (JWS).

* The SafetyNet Attestation service evaluates the runtime environment and requests a signed attestation of the assessment results from Google's servers.

* Google's servers send the signed attestation to the SafetyNet Attestation service on the device.

* The SafetyNet Attestation service returns this signed attestation to your app.
* This JWS is then send to a backend service for validation.
* The backend service returns the validation results. And to validate the token, the backend service decodes/parse the JWS received from the client app. It should look like this.

{
    "timestampMs",
    "nonce",
    "apkPackageName",
    "apkCertificateDigestSha256" : [],
    "ctsProfileMatch": true,
    "basisIntegrity": true,
    "evaliationType": "BASIC",
}

## For a egit Android app running on a legit Android device basicIntegrity and ctsProfileMatch should be true, nounce should not be empty, and the value of these apkPackageName and apkCertificateDigestSha256 should match with that of your Androidn app.
