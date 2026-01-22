# N8N & Twilio Integration Guide

Guida tecnica per mappare l'output JSON di FluxBot nel workflow di automazione.

## 1. JSON Parsing Strategy
Poiché l'output del LLM è un blocco di codice JSON, utilizzare un nodo "Code" in N8N subito dopo la chiamata OpenAI:

```javascript
// N8N Code Node Example
try {
  // Pulisce eventuali backticks markdown ```json
  const rawContent = $input.item.json.content.replace(/```json/g, "").replace(/```/g, "");
  const aiData = JSON.parse(rawContent);
  
  return { json: aiData };
} catch (error) {
  // Fallback in caso di JSON rotto
  return { json: { voice_response: "Scusa, c'è stato un errore tecnico.", backend_action: "TRANSFER_TO_HUMAN" } };
}
