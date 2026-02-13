# Voice Pipeline BYO-Key Debug Lab

**Vapi + Deepgram + OpenAI + TTS — Support & Deployment Case Study**

## Objective

Build and debug a real-time voice AI pipeline using multiple providers and Bring-Your-Own API keys (BYOK), then verify provider routing using support-style diagnostics.
This lab focuses on **integration debugging**, **credential verification**, and **log-based root cause analysis** — not just getting a demo to work.

Target roles:

* AI Support Engineer
* Technical Support / Success Engineer
* Deployment Engineer
* Voice AI Support
* LLM Platform Support

---
## Final Architecture

User Audio
→ Vapi Assistant
→ Deepgram (nova-3) — Speech-to-Text
→ OpenAI (gpt-4.1-mini) — LLM
→ TTS Provider — Voice Output
→ Caller hears synthesized speech

---

## Providers Used

| Layer         | Provider                | Mode                      |
| ------------- | ----------------------- | ------------------------- |
| STT           | Deepgram nova-3         | BYO key                   |
| LLM           | OpenAI gpt-4.1-mini     | BYO key                   |
| TTS           | ElevenLabs → Vapi voice | Switched during debugging |
| Orchestration | Vapi                    | Assistant config          |

---

## What This Lab Demonstrates

* Multi-provider voice pipeline setup
* BYO API key configuration
* Provider misrouting detection
* 401 / permission debugging
* TTS voice ID failures
* Plan limitation failures
* Browser audio routing issues
* Cross-system timestamp correlation
* Provider usage verification
* Canary key testing method
* Support-style failure documentation

---

## Major Issues Encountered

### 1️⃣ Provider 401 Errors

Cause: API key permission scope
Fix: recreate keys + validate with curl

---

### 2️⃣ ElevenLabs Voice Failures

Errors:
* voice_id_does_not_exist
* plan blocked free usage

Fix:
* switched voice provider
* updated assistant config
---
### 3️⃣ “No Audio” Despite Successful Call

Symptoms:

* transcript present
* model response present
* recording had audio
* live monitor silent

Root cause:
Browser (Safari) audio output routing

Fix:
Change output device → audio restored

---

### 4️⃣ Provider Key Verification Challenge

Problem:
Logs do not expose provider request IDs.

Solution:
Used **timestamp + token + model correlation** across:
* Vapi logs
* OpenAI usage dashboard
* Deepgram request logs

Confirmed BYO keys were used.
---
## Verification Methods Used
### Provider Routing Proof Methods
* Timestamp correlation
* Token count matching
* Model name matching
* Duration matching
* Transcript matching
* Canary key failure tests
---

## Canary Key Test Method
Replace provider key with invalid key.
Expected:
* Auth failure → proves BYO key is used
* Still succeeds → platform-managed key in use
Reusable support technique.
---

## Repo Contents
configs/ — assistant configurations
logs/ — redacted real logs
docs/ — architecture + troubleshooting
scripts/ — key validation helpers
writeups/ — support-style case study
---

## Skills Demonstrated
* Voice AI pipeline debugging
* Multi-provider API integration
* Credential verification
* Log analysis
* Failure isolation
* Cross-system tracing
* Support playbook creation
---

## Next Planned Labs
* Hallucination & Ambiguity Debug Lab
* Tool / Function Calling Failure Lab
* Latency & Cost Tradeoff Lab
* Failure Injection Playbook Expansion
---
