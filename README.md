# OpenClaw Twilio SMS Plugin

Standalone Twilio SMS/MMS channel plugin for [OpenClaw](https://github.com/openclaw/openclaw).

Works with stock OpenClaw installed via npm — no fork required.

## Install

```bash
# Clone into OpenClaw extensions directory
cd ~/.openclaw/extensions
git clone git@github.com:mitchellgordon95/openclaw-twilio-sms.git twilio-sms
cd twilio-sms
npm install
```

## Configure

Add to `~/.openclaw/openclaw.json`:

```json
{
  "channels": {
    "twilio-sms": {
      "accountSid": "YOUR_TWILIO_ACCOUNT_SID",
      "authToken": "YOUR_TWILIO_AUTH_TOKEN",
      "phoneNumber": "+1XXXXXXXXXX",
      "webhookPath": "/twilio-sms/webhook",
      "webhookUrl": "https://your-domain.com/twilio-sms/webhook",
      "dmPolicy": "allowlist",
      "allowFrom": ["+1XXXXXXXXXX"],
      "pinAuth": true,
      "pin": "1234"
    }
  }
}
```

With `pinAuth` enabled, new numbers must send the correct PIN before they can interact with the agent. This adds a layer of protection on top of the allowlist.
```

Then set your Twilio phone number's messaging webhook to `https://your-domain.com/twilio-sms/webhook` (HTTP POST).

## Origin

Extracted from the [openclaw/openclaw](https://github.com/openclaw/openclaw) fork branch `feat/twilio-sms-channel` by [@mitchellgordon95](https://github.com/mitchellgordon95).

Adapted to work as a standalone plugin against stock OpenClaw by remapping internal plugin-sdk imports and bundling `twilio-shared` utilities locally.
