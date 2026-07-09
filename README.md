# SPETA — Workspace juridic AI

Aplicație web într-un singur fișier (`index.html`), fără pas de build.
Frontend static; backend pe Supabase (bază de date + Edge Functions); AI prin OpenAI.

## Ce conține repo-ul
- `index.html` — aplicația completă (landing + dashboard + auth).
- `vercel.json` — configurare de găzduire (servește `index.html` pe orice rută, plus câteva anteturi de securitate).
- `README.md` — acest fișier.

## De ce dădea 404
Vercel servește implicit `index.html` din rădăcina repo-ului. Fișierul se numea
`SPETA_dashboard.html`, deci rădăcina nu avea `index.html`. Redenumit / copiat în
`index.html` → se rezolvă.

## Deploy pe Vercel
1. Pune în repo, la rădăcină: `index.html`, `vercel.json`, `README.md`
   (poți șterge `SPETA_dashboard.html` din repo).
2. Vercel → Add New Project → Import repo-ul.
3. Framework Preset: **Other**. Fără build command, fără output directory special.
4. Deploy.
5. Project → Settings → Domains → adaugă `speta.io` și `www.speta.io` și urmează
   instrucțiunile DNS (de obicei un CNAME către `cname.vercel-dns.com`).

## Actualizări
Orice `git push` în repo redeployează automat site-ul. Fișierul de editat rămâne `index.html`.

## De configurat înainte de a fi public
- Supabase → Authentication → URL Configuration: adaugă `https://speta.io` (și subdomeniile)
  la **Site URL** și **Redirect URLs**, ca Google login și resetarea parolei să funcționeze.
- Supabase → Authentication → Providers → Email: dezactivează „Confirm email" (pentru demo)
  sau lasă-l activ pentru producție.
- Securizare: închiderea funcțiilor deschise (`embed-pending`) și rate limiting.

## Arhitectură (pe scurt)
- Bază legislativă: ~7.356 articole din 15 acte, indexate cu embeddings (pgvector).
- Motor: RAG (căutare semantică + citarea surselor) prin Edge Functions Supabase.
- Conturi: Supabase Auth, roluri (student / avocat / admin), limite lunare (metering).

© 2026 VELIUMIN SRL. SPETA™.
