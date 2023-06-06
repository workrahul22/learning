# What is SMS Traffic Pumping Fraud?

## SMS Traffic Pumping Fraud, also known as Artificially inflated Traffic, happen when fraudsters take advantage of phoen number input field to receive a one-time passcode (OPT), and app download link, or anything elase via SMA. If this form does not have adequate controls, the attackers can inflate traffic and exploit your app. The fraudsters send SMS toa range of numbers controlled by a specific mobile network operator (MNO) and receive a share of the generated revenue.

## This happens in one of two scenarios:

### The MNO is complicit in the scheme and has a revenue sharing agreement with the fraudsters.
### The MNO is unknowingly exploited by the fraudsters.

## In the second case, smaller MNOs get paid by large MNOs for subscribers and traffic. In this situation it is possible for a fraudster to create a fake company and promise large amounts of traffic. The MNO many not care what the source of the traffic is and ends up supporting the fraud. In either case, you're more likely to see this type of fraud occur with smaller MNOs.

# How can i determine if I'm experiencing an SMA Pumping attck?

## You will likely see a spike of messages send to a block of adjacent numbers, often to emote destination countries. If you're sending SMS for one-time passcode (OTP) use case, you will likely not see c completed verification cycle for these OTPs.

# Best Practices for preventing SMS Traffic Pumping Fraud

## Disable Geo-Permissions for unused countries

### Ensuring that countries to which you do not intend message are disabled will lower the likelihood of SMS Traffic Pumping Fraud.

## Set Rate Limits

### Make sure your app will not send more than 1 message per X seconds to the same mobile number range or prefix. Implement rate limits by user, IP, or device identifier. You can use a CDN like Cloudflare or implement modules in your web server like Nginx and Apache for basic rate limiting.

### Rate limits may not prevent 100$ of fraud but can significantly mitigate the damage that an attacker can do and may even deter them if they decide that it's not worth it to go after your app.

## Detect bots and refresh your user experience to prevent them.

## Libraries like botd or CAPTCHAs can help detect and deter bot traffic. Small changes to your user experience like ensuring that your users confirm their email address before enrolling in 2FA introduce a small amount of friction for legitimate users but can deter automated scripts and bots.

## Implement exponential delays between verification retry requests.

### Similar to rate limits, implementing exponential delays between requests to the same phone number is one way to prevent rapid sending. you can search the way we can do that

## Look up the phone number before sending

### Use Carrier Lookup to get the line type of number and only send SMS to mobile numbers. You can also use this API request to determine the carrier and block carriers that may be (knowingly or not) cauing inflated traffic.

## Monitors one-time passcode (OTP) conversion rates and create alerts

### Create internal monitors for conversion rate of verifications (i.e number of OTP's validated by end users / number of OTPs send to end users). If you notice this rate starting to drop especially in an unexpected country, trigger an alert review.

## Migrate one-time passcode (OTP) traffic to verify

### Migrating to verify will aloow you to utilize verify Fraud Guard. This tool helps prevent SMS releated fraud by blocking SMS transmissions to any destination deemed fraudulent.


