---
# ✅ 4️⃣ Failure Injection Checklist (Support Lab Style)
# Voice Pipeline Failure Injection Checklist

## API Credential Failures
[ ] Replace OpenAI key with invalid key → expect 401  
[ ] Replace Deepgram key with revoked key → expect STT failure  
[ ] Remove TTS key → expect voice generation failure  
[ ] Use restricted-scope key → expect permission error  

---
## Model Failures
[ ] Select model not enabled in account  
[ ] Use deprecated model name  
[ ] Set max_tokens extremely low  
[ ] Set temperature to edge values  

---
## TTS Failures
[ ] Use invalid voice_id  
[ ] Use voice not available in plan  
[ ] Switch provider without updating config  
[ ] Remove fallback voice  

---

## STT Failures
[ ] Change language mismatch  
[ ] Use unsupported sample rate  
[ ] Disable microphone input  
[ ] Inject noise audio  

---
## Pipeline Routing Failures

[ ] Switch voice provider but keep old voiceId  
[ ] Change assistant config but don’t redeploy  
[ ] Use wrong credential slot  
[ ] Mix BYO + managed providers  

---
## Verification Tests

[ ] Timestamp correlation check  
[ ] Token usage match  
[ ] Provider dashboard check  
[ ] Canary key test  
[ ] Log provider field check  

---
## Client-Side Failures

[ ] Browser audio output mismatch  
[ ] Wrong device selected  
[ ] Muted monitoring console  
[ ] OS audio routing issue  

---
## Support Validation Artifacts
[ ] Save redacted logs  
[ ] Save timestamps  
[ ] Save provider dashboards  
[ ] Save config snapshot  
[ ] Document root cause

---
