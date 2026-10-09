# Edge Function `wine-pairing-ai`

La pagina chiama questa funzione Supabase, che invia al modello OpenAI la ricetta e le sole bottiglie disponibili nella cantina corrente. La chiave OpenAI non è inclusa nel browser o nell'archivio.

## Configurazione e deploy

1. In Supabase, apri **Project Settings → Edge Functions → Secrets** (oppure usa la CLI).
2. Crea il secret `OPENAI_API_KEY` con la tua chiave API OpenAI. Non inserirla in `index.html`.
3. Dalla cartella del progetto Supabase, salva `index.ts` in `supabase/functions/wine-pairing-ai/index.ts` e pubblica:

```bash
supabase functions deploy wine-pairing-ai
supabase secrets set OPENAI_API_KEY=la_tua_chiave
```

Esegui il deploy dal progetto collegato al riferimento Supabase usato dal sito. La funzione usa la verifica JWT predefinita di Supabase; l'utente deve avere una sessione valida. Verifica in **Edge Functions → Logs** in caso di errori.

Le chiamate OpenAI consumano credito API del relativo account. La chiave API è distinta da un eventuale abbonamento ChatGPT.
