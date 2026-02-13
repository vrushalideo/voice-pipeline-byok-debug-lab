# Provider Verification Notes
This document explains how BYO provider usage was verified.

## Methods Used
- Timestamp correlation
- Token count matching
- Model name matching
- Provider dashboard confirmation
- Canary key failure testing

## Why Provider IDs Are Missing
Vapi logs normalize provider responses and do not expose
OpenAI response_id or Deepgram request_id.

Verification is performed using correlation instead of direct IDs.
