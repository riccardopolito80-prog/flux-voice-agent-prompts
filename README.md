# flux-voice-agent-prompts
# 🎙️ Enterprise AI Voice Agent Architecture

Questa repository contiene l'infrastruttura di **Prompt Engineering** e la logica di gestione per un Assistente Vocale AI di livello Enterprise.

Il progetto è sviluppato per **Flux Digital Solutions** (Demo Agency) ma l'architettura è agnostica e replicabile per qualsiasi scenario di **Inbound Customer Service**.

## 🏗️ Tech Stack & Integrazioni
Il sistema è progettato come modulo "plug-and-play" per la seguente pipeline RAG/Automation:
- **Orchestrator:** N8N (Self-hosted)
- **Telefonia:** Twilio Programmable Voice
- **Generazione Vocale (TTS):** ElevenLabs (Modello Turbo v2)
- **LLM:** OpenAI GPT-4o-mini (Ottimizzato per latenza < 500ms)

## ⚡ Obiettivi Ingegneristici
1.  **Latenza Zero:** Prompting strutturato per generare risposte concise (< 20 parole) per ottimizzare il buffer audio.
2.  **Strict JSON Output:** L'AI non risponde in linguaggio naturale, ma restituisce un oggetto JSON parsabile per il routing delle chiamate (es. *Hangup*, *Transfer*, *Record*).
3.  **Hallucination Guardrails:** Protocolli di sicurezza rigidi per prevenire la generazione di prezzi falsi o consulenze non autorizzate.
4.  **Context Injection:** Gestione dinamica degli orari e della disponibilità tramite variabili di sistema.

## 📂 Struttura della Repository
- `/prompts`: System Prompts versionati con logica condizionale.
- `/tests`: Log dei test di robustezza (Jailbreak attempts & Stress tests).
- `/docs`: Guida all'integrazione del payload JSON in N8N.
