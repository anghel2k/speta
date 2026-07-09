# SPETA — Workspace juridic AI

Aplicație web într-un singur fișier (`index.html`), fără pas de build.
Frontend static; backend pe Supabase (bază de date + Edge Functions); AI prin OpenAI.

## Ce conține repo-ul
- `index.html` — aplicația completă (landing + dashboard + auth).
- `vercel.json` — configurare de găzduire (servește `index.html` pe orice rută, plus câteva anteturi de securitate).
- `README.md` — acest fișier.

## Arhitectură (pe scurt)
- Motor: RAG (căutare semantică + citarea surselor) prin Edge Functions Supabase.
- Conturi: Supabase Auth, roluri (student / avocat / admin), limite lunare (metering).

© 2026 VELIUMIN SRL. SPETA™.
