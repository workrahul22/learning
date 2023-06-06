## The DeviceCheck service consist of both a framework interface that you access from your mobile app and an Apple server interface that you access from your backend service.

## Someone who modifies your app and distributes it outside the App Store can add unauthorized features like game cheats, ad removale, or access to premium content. The App attest service gives your app a way to assert its validity so that your server can more confidently provide access to sensitive resources.

How does it works

* iOS app interacts with the App attest service to construct an attestation token base64 encoded.

* The app attest service returns an attestation token to iOS app.

* This token is then sent to a backend service for validation.

* The backend service doesn;t unpack/validate the token and instead forwards this to the Apple Device Check server for validation.

* If the Apple Device Check server returns 200, then it means the Device Check passed. Otherwise, validation failed.

* At this step backend service can device how to proceed depending on the results received from Apple Server.

culr -i --verbose -H "Authorization: Beared <GeneratedJWT>" \ -X POST --date-binary @ValidValidateDeviceToken Request.json \ https://api.developement.devicecheck.apple.com/v1/validate_device_token

## Here, the GeneratedJWT token is generated using the Team Id, Key Id, and the private Key of your legit IOS app. On how to create this suth token see this:
https://help.apple.com/developer-account/#/deva05921840

And Request.json contains the device token for validation along with some other infromation.

{
    "device_token": "",
    "transaction_id": "",
    "timestamp": 
}

