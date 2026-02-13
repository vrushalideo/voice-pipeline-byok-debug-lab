ASCII Diagram
                
                ┌──────────────┐
User Speech ───▶│     Vapi     │
                │  Assistant   │
                └──────┬───────┘
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
  Deepgram STT     OpenAI LLM        TTS
   (nova-3)       (gpt-4.1-mini)   (Voice)
        │              │              │
        └──── transcript│              │
                       response text ──┘
                               │
                               ▼
                        Synthesized Audio
                               │
                               ▼
                            Caller

                            


flowchart LR
A[User Speech] --> B[Vapi Assistant]

B --> C[Deepgram STT nova-3]
C --> B

B --> D[OpenAI gpt-4.1-mini]
D --> B

B --> E[TTS Provider]
E --> F[Audio Output]
F --> G[Caller]
