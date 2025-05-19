# LiveKit Phone Assistant Agent - using SIP REFER

This agent was forked from a LiveKit example located [here](https://github.com/livekit-examples/phone-assistant/tree/main).  

This agent will answer calls and give the caller the option to specify which department they want to speak with. The caller can select from the Billing Department, Customer Service Department or the Tech Support Department.  The agent will transfer the call to that department using SIP REFER.  This means that the call will be sent back to the carrier and the carrier will initiate a new call using a SIP URI that represents that department.

## Setup a virtual environment
```
python3 -m venv ./.venv
source ./.venv/bin/activate
```

## Install LiveKit Prequisite Packages
```
python3 -m pip install -r requirements.txt
```

## Setup Environment Variables

Copy the sample file to .env.local and update the file with values needed to connect to LiveKit and OpenAI.  The LiveKit values can be found in the LiveKit Portal and the OpenAI API Key can be found in the OpenAI Portal

```
cp env.local.example .env.local
vi .env.local
```

## Setup Twilio

1. Login into Twilio
2. Setup an Elastic SIP Trunk
3. Set the Origination SIP URI to the SIP URI in your LikeKit Portal
4. Purchase and/or Assign a Phone Number to the trunk
5. Place an inbound test call

## Configure LiveKit to Accept a Call from Twilio and Route to the Agent

# Setup LiveKit CLI

1. Install the [LiveKit CLI](https://docs.livekit.io/home/cli/cli-setup/)
2. Create/Obtain your LiveKit API Keys
3. Configure Environment Variables
4. Login to the CLI via OAUTH

# Use the LiveKit CLI to Accept Calls from Twilio


1. Add the Twilio Phone Number to inbound-trunk.json and create an inbound configuration

```
lk sip inbound create inbound-trunk.json
```

2. Setup a Dispatch rule that will route the inbound call from Twilio to the Agent

```
lk dispatch create dispatch-rule.json
```
