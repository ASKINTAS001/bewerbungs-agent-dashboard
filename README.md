# bewerbungs-agent-dashboard

Freigabe-Dashboard für den INNOVIA-TAS Bewerbungs-Agenten (BWB).

## Dateien
- `index.html` — Login (Supabase Auth)
- `dashboard.html` — Übersicht, Freigabe-Queue, Bewerbungsverlauf, Chat mit BWB_AGENT
- `manifest.json` — PWA-Manifest
- `icons/` — App-Icons (192px/512px), aus dem Content-Agent-Cockpit-Repo übernehmen oder eigene hinterlegen

## Einrichtung
1. In `index.html` und `dashboard.html` jeweils `SUPABASE_ANON_KEY` eintragen
   (Supabase → Project Settings → API → anon/public key — **nicht** den service_role-Key).
2. Unter Supabase → Authentication → Users einen Nutzer (Askins E-Mail) anlegen.
3. Repo als GitHub Pages veröffentlichen (Settings → Pages → main-Branch).

## Architektur
- Daten kommen direkt per Supabase-JS-Client aus dem Browser (RLS auf Rolle `authenticated`).
- Freigeben/Ablehnen setzt nur `applications.status` — kein automatischer Versand.
- Chat läuft über den bestehenden öffentlichen Webhook von BWB_AGENT
  (`https://n8n.innovia-tas.de/webhook/bwb-agent-chat/chat`).
