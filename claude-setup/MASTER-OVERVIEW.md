# 🗺️ MASTER-OVERVIEW — Wo liegt was, wer nutzt was, nach Prio

> Stand 2026-07-20. Merge-OK für die 7 Rollout-PRs kam explizit von Robert („DU DARFST DAS AUCH! ZIEH DURCH").

---

## 1️⃣ Wo finde ich was — pro Repo

| Repo | Was liegt dort | Besonderes |
|------|----------------|------------|
| **ClaudeSkills** 🏛️ | ZENTRALER HUB: `claude-setup/` komplett (README, MEDIA-QUEUE, beide Installer) + `.claude/skills/` + `.mcp.json` + die offiziellen Anthropic-Skills (Repo-Basis) | **Erste Anlaufstelle.** Neue Skills immer zuerst hierhin |
| **realrise-academy** | `claude-setup/` komplett + MEDIA-QUEUE (Arbeitskopie) + Video-Skills + `.mcp.json` | Ursprung des Setups; MEDIA-QUEUE wird HIER gepflegt |
| **faos-core** | `claude-setup/` komplett + MEDIA-QUEUE-Kopie + Video-Skills + `.mcp.json` | Selbstbedienung für FAOS/Hermes/Neo |
| **aimpact-brain** | `claude-setup/` komplett + MEDIA-QUEUE-Kopie + Video-Skills + `.mcp.json` | Selbstbedienung für AIMPACT |
| **daily-ads** | `claude-setup/` (ohne MEDIA-QUEUE) + Video-Skills + `.mcp.json` | Ads-Repo |
| **finance-academy** | `claude-setup/` (ohne MEDIA-QUEUE) + `.mcp.json` — KEINE `.claude/skills` (gitignored!) | Skills kommen dort NUR über globalen Installer |
| **crm-ultra** | `claude-setup/` (ohne MEDIA-QUEUE) + Video-Skills + `.mcp.json` | CRM/Outreach-Repo |

**Nur lokal auf Roberts Mac (nicht versioniert):** SEO-Suite-Altbestand, Outreach-5-Stufen (`skill-1…5`), gstack, GitNexus, `Media`, `video`, `ContentAnalysis`, cold-email etc. → bei Gelegenheit ins Hub-Repo pushen!

**In `~/.claude/skill-sources/` (klont der Installer):** anthropics/skills · tapestry (youtube-transcript) · awesome-claude-skills · alirezarezvani (358 Skills) · **claude-seo (25 SEO/AEO/GEO-Skills + 18 Agents)** · dazu geklont: OmniRoute (Gateway, separat evaluieren)

---

## 2️⃣ PRIO-PLAN — was WER als erstes nutzen muss

### 🥇 PRIO 1 — Geld: SEO/AEO/GEO auf die Funnels (Robert + Daniel)
- `claude-seo` auf **academy.realrise-agency.com** + **phase1-Funnel** + Blogs fahren: `/seo audit` → Action-Plan abarbeiten
- Danach: gleiche Audits für Affiliates anbieten (Skalierung, Roberts erklärtes Ziel)
- Werkzeug: läuft nach `install-claude-skills.sh` lokal sofort

### 🥈 PRIO 2 — Wissen: MEDIA-QUEUE abarbeiten (Robert, 1 Abend)
- Lokal: *„Gehe claude-setup/MEDIA-QUEUE.md durch — jeden 🟡-Eintrag: Transkript + Zusammenfassung + Kernaussagen nach claude-setup/media-notes/"*
- Ergebnis: ~45 Videos/Reels als Text — nie wieder schauen. Erkenntnisse (Company OS, FableOS, Orchestrator, „10 Repos") fließen in FAOS/Hermes
- Die 3 NotebookLM-Sachen (Emails, Yassine/Team, IG-Content) danach hochladen

### 🥉 PRIO 3 — Outreach: SDR-Stack (Robert holt Blueprint, dann Team)
- johnpeslar-Artikel „31 drop-in skills for automated outbound" lokal öffnen → Text an Claude → Skills nach crm-ultra/Hub integrieren
- Kombinieren mit vorhandenem 5-Stufen-System (`skill-1-prospector` … `skill-5-deal-tracker`) + Clay
- Nutzer: Robert/Yassine-Team für RealRise-Closes

### 4️⃣ PRIO 4 — Content-Maschine (Larissa + Daniel)
- Video-Skills + `ContentAnalysis` für Repurposing; `linkedin-social` + „Marketing organic for free"-Reel-Learnings
- Repo: realrise-content-larissa (Setup bei Bedarf dorthin ausrollen — 2 Min)

### 5️⃣ PRIO 5 — Infrastruktur: OmniRoute + Landingpage (Robert, wenn Luft)
- OmniRoute lokal via Docker testen → ggf. `hermes-llm-router` ersetzen/ergänzen (~1,4 Mrd. Free-Tokens/Monat)
- Neue Homepage: Three.js + 3D-/Scroll-Effekte (eigenes Projekt; Skills `frontend-design`, `web-artifacts-builder` helfen)

---

## 3️⃣ Was Claude NICHT selbst herausfinden konnte — und WIE DU HILFST

| Fehlt | Warum blockiert | Dein Move (exakt) |
|-------|-----------------|-------------------|
| Inhalte der ~45 YouTube/IG-Links | Cloud-Firewall | **Lokal 1 Befehl** (MEDIA-QUEUE-Batch) — oder Transkript pasten (YouTube: „…mehr" → „Transkript anzeigen") |
| Die 31 SDR-Skills (johnpeslar) | Blog geblockt | Artikel lokal öffnen → Volltext in die Session pasten → Claude baut die Skills ein |
| Instagram-Blueprints („Kommentiere X → DM") | Braucht DEINEN Account | Du kommentierst/DMst → erhaltenen Link/Text einfach reinwerfen — jedes Format ok |
| IG-Reels ohne Untertitel | Login/Cookies | Lokal: `yt-dlp --cookies-from-browser chrome <reel-url>` → claudetube transkribiert |
| Deine lokalen Skills (SEO-alt, Outreach 1–5, gstack, Media, video, ContentAnalysis) | Liegen nur auf deinem Mac | Einmalig: Ordner aus `~/.claude/skills` ins Hub-Repo `ClaudeSkills` committen → für immer versioniert |
| NotebookLM | Kein Zugang | Du lädst hoch; Claude bereitet Inhalte vorher auf |

**Faustregel bleibt:** GitHub-Link → Claude sofort selbst. Social/Login/Lokal → du holst es (1 Kommentar, 1 Copy-Paste, 1 Befehl), Claude verarbeitet.
