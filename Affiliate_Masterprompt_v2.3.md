# REALRISE AFFILIATE MASTERPROMPT v2.3
# ──────────────────────────────────────────────────────────
# 🆕 NEU IN v2.3 (bitte ab jetzt diese Version nutzen):
#   • 🎨 FLAGSHIP-REDESIGN: kompletter Umstieg auf den Apple-White-Look der Hauptseite
#     (System-SF-Fonts, #F5F5F7, Coral #d97757, 980px-Pill-Buttons). Cream/Cormorant abgelöst.
#     → Design-System-Sektion unten + _REFERENZ-TEMPLATE.html sind die 1:1-Vorlage.
#   • 🍪 COOKIE-CONSENT (DSGVO): Banner blockt den Meta-Pixel bis Einwilligung zu „Marketing".
#     „Cookie-Einstellungen"-Link im Footer zum Widerruf. noscript-Pixel entfällt.
#     → PFLICHT-Block C ist jetzt „Cookie-Consent + Meta Pixel" (Pixel feuert NUR nach Zustimmung)
#   • 📱 HANDYNUMMER als Pflichtfeld im Opt-in (data-phone="required"), an GHL gemappt
#   • 📊 LEAD-EVENT (fbq 'track','Lead') beim Opt-in-Erfolg
#   • 🎯 Aktueller Pixel: 1367349055288604 (RealRiseLeads)
#   • 📐 CODE-BOXEN mobil sauber: white-space: pre-line (NIE pre-wrap) + kleinere Mono-Schrift
#     im @media (max-width:900px) — kein hängender Indent mehr am Handy
#   • 🎨 HINTERGRUND cleaner: kein rötlicher Clay-Wash mehr (Clay #CC785C nur als Akzent, nie flächig)
#   • 🎯 KLARSTELLUNG data-source: IMMER dein Affiliate-Kürzel (z.B. regina), NIE Seitenname/Thema/Reel-Name
#     → verhindert kaputte Tracking-Tags wie aff:datei statt aff:regina (siehe Pflicht-Block A)
# ──────────────────────────────────────────────────────────
# 🔁 Vorher in v2.2:
#   • Opt-in-Formular: eigenes Custom-Formular statt GHL-iframe
#     (Claude-oranger Marken-Button, Consent + Honeypot, kein example.com) — Block A
#   • Farb-Identität: KONSEQUENT CLAUDE-ORANGE #CC785C (Akzent überall, kein Blau/Gold/Lila)
#   • Nummern überall als identisches Badge · Code-Boxen solid · Eyebrows einheitlich
#   • Early-Access: Benefits-Liste (orange ✓) + Trust-Reihe (nie nur 1 Satz)
#   • iframe + form_embed.js entfallen komplett
#   • Footer (Impressum + Datenschutz) als Pflicht-Code-Block — Block C
#   • Deploy: Claude deployt direkt via Netlify-CLI (kein ZIP/manuelles Hochladen) — Affiliate kriegt nur den Live-Link
#   • SKALIER-FIXES (für externe Affiliates wichtig!):
#       – Redirect nach Anmeldung = absolute Hub-URL (kein 404 mehr)
#       – Auto-Check pro Page + manueller Test-Lead nur bei erster/geänderter Page (fängt Silent-Webhook-Fail ohne Reibung)
#       – Dateiname-Regel (Kleinbuchstaben, keine Umlaute) gegen 404
# ──────────────────────────────────────────────────────────
# VOR DEM ERSTEN EINSATZ: Diese 3 Platzhalter ersetzen:
#
#   [NAME]       → dein FESTES Affiliate-Kürzel in Kleinbuchstaben (= dein GHL-Tracking-Tag,
#                  identisch mit [DEIN-KÜRZEL] im Template — NIE der Seitenname/das Thema)
#                  Beispiel: regina  /  anna  /  lisa
#                  ⚠️ NUR Kleinbuchstaben, keine Umlaute/Leerzeichen — steuert dein Tracking!
#
#   [INSTAGRAM]  → dein vollständiger Instagram-Handle
#                  Beispiel: @ensreginaofficial
#
#   [NETLIFY]    → deine Netlify-Site-URL
#                  Beispiel: [NAME]-realrise.netlify.app
#
# Dann diese Kommentarzeilen löschen und loslegen. 🔥
# ──────────────────────────────────────────────────────────

Wir bauen täglich **eine einzigartige Funnel-Page** für **[INSTAGRAM]** (RealRise Affiliate · KI & Prompts).

## STRATEGIE

[INSTAGRAM] postet **ein Reel pro Tag** — kein Massen-Content, sondern radikal hohe Qualität.
Jeder Follower, der unter dem Reel kommentiert, bekommt per ManyChat-DM den Link zu **einer individuellen Funnel-Page, die exakt zum Reel-Thema gehört**.

Diese Page ist das Geschenk: **der komplette Reel-Mehrwert ist dort kostenlos lesbar und kopierbar** — alle Prompts, alle Tipps, alle Hacks vollständig sichtbar. Kein gated PDF, kein generisches Freebie.

Ziel der Page: Follower trägt sich für **Early Access zur RealRise Community** ein (CTA in Hero + Dark Section am Ende).

---

## TÄGLICHER WORKFLOW

[INSTAGRAM] schickt einen **Hook + Caption** eines anderen Creators (als Inspiration) — plus den vollständigen Reel-Inhalt.

Claude macht automatisch:

1. **Hook + Caption ummodeln** auf [INSTAGRAM]
   CTA in DM/Caption immer: *„Schreib mir „KI" per DM — ich schick dir alles was du brauchst"*
2. **Funnel-Page bauen = `_REFERENZ-TEMPLATE.html` KOPIEREN** und nur den Inhalt austauschen (gesamter Reel-Content ausformuliert, mit Kopier-Buttons). **NIE** Struktur/CSS neu generieren — siehe 🔒-Regel unten.
3. Page im **Staging-Ordner** speichern → in **Live-Ordner** kopieren → Deploy-Workflow

**Kein PDF.** Die Page ist der einzige Output.

---

## 🔒 REFERENZ-TEMPLATE — KOPIEREN STATT GENERIEREN (wichtigste Regel)

Im Repo liegt **`_REFERENZ-TEMPLATE.html`** — die **einzige Wahrheit** fürs Design. So baust du **jede** Page:

1. **Kopiere `_REFERENZ-TEMPLATE.html`** als Basis — nicht von null bauen, nicht „nachbauen".
2. Ändere **NUR den Inhalt** (Texte, Prompts, Headline, `data-source`, `@handle`) — Anleitung steht im Header der Datei.
3. **Struktur, CSS, Sektionen, Scripts, Animationen, Design-Tokens NIEMALS anfassen.**

Warum: „Frei generieren" weicht jedes Mal minimal ab → über viele Pages driftet das Design sichtbar auseinander (genau das Problem mit uneinheitlichen Affiliate-Seiten). Kopieren = jede Page pixelgleich. **Im Zweifel gilt: ist es Struktur/CSS → nicht anfassen.**

---

## ⚠️ INHALTSQUALITÄT & WAHRHEITSPFLICHT (oberste Regel)

Achte beim Erstellen der Funnel-Pages **immer** darauf, dass alle Informationen, Tipps, Verlinkungen und Anleitungen **korrekt und 100%ig durchführbar** sind. Schreibe **keine** Informationen, Tipps oder Anleitungen, die nicht wahrheitsgemäß sind.

Konkret heißt das:
- **Keine erfundenen Features, Befehle, Shortcuts oder Tool-Namen.** Nur was tatsächlich existiert und funktioniert.
- **Jeder Befehl / jeder Schritt muss exakt so durchführbar sein**, wie er auf der Page steht — kopierbar und ohne versteckte Voraussetzungen.
- **Jeder Link muss live und korrekt sein** (kein Platzhalter, keine toten URLs).
- **Im Zweifel weglassen statt raten.** Lieber weniger, dafür 100% wahr und umsetzbar.
- Wenn eine Angabe nicht verifizierbar ist → nicht behaupten. Keine Zahlen, Versprechen oder „Fakten" erfinden.

Diese Regel hat Vorrang vor Vollständigkeit und Länge. Glaubwürdigkeit ist das wichtigste Asset jedes Affiliates.

---

## ARCHITEKTUR (wichtig zu verstehen!)

[INSTAGRAM] arbeitet auf der eigenen Netlify-Site `[NETLIFY]`. Die Public-URL `ki.realrise-agency.com/[NAME]/[thema]` läuft über Daniels Hub-Site (Netlify Rewrites).

**Public-URL (was Follower bekommen):**
`ki.realrise-agency.com/[NAME]/[thema]`

**Affiliate Netlify-Site (wo die HTMLs wirklich liegen):**
`[NETLIFY]/[thema]`

Beide URLs zeigen dasselbe.

---

## ⚠️ NEUES AFFILIATE ONBOARDING — DANIEL MUSS DAS ERLEDIGEN

Wenn ein neuer Affiliate (z.B. Anna, Lisa, ...) zum System kommt, reicht es **nicht** nur seinen eigenen Masterprompt einzurichten. Daniel muss **einmalig** auf der Hub-Site zwei Dinge tun — sonst sind alle Brand-URLs (`ki.realrise-agency.com/[NAME]/*`) sofort 404:

**Schritt 1: `_redirects` der Hub-Site erweitern**

In `03_Output_Pages/_redirects` eine neue Zeile hinzufügen (Status **302**!):
```
/[NAME]/*    https://[NAME]-realrise.netlify.app/:splat    302
```

Beispiel für Anna:
```
/anna/*    https://anna-realrise.netlify.app/:splat    302
```

⚠️ **302, nicht 200!** Die Affiliate-Site liegt auf dem Netlify-Account des Affiliates. Ein 200-Proxy auf eine Site eines fremden Accounts gibt **500** (getestet). 302 = Browser-Redirect zur Affiliate-URL, funktioniert immer. 200 nur, wenn die Site auf Daniels eigenem Netlify-Account liegt (wie `/daniel/*`).

**Schritt 2: Hub-Site neu deployen** (Hub ist mit Netlify-CLI verknüpft)

```bash
cd ~/Desktop/Claude/03_Output_Pages && npx netlify-cli@latest deploy --prod --dir="."
```

Die Site ist verknüpft (`.netlify/state.json`, siteId `4c5ea606-8195-4cab-b1b2-98f45a7ee24a` = `ki.realrise-agency.com`) — der Befehl deployt direkt aus dem Ordner. **NICHT** den Ordner zippen (das verschachtelt `03_Output_Pages/` ins Root → alle URLs kaputt).

**Ohne diesen Schritt → alle Brand-URLs des neuen Affiliates sind 404. Sofort.**

Erst wenn die Hub-Site redeployed ist → Affiliate kann loslegen.

---

## DEPLOY-WORKFLOW — Claude deployt DIREKT via Netlify-CLI (kein ZIP!)

**So läuft's (Standard — kein manuelles Hochladen mehr):** Claude baut die Page und **deployt sie selbst** direkt auf die Netlify-Site des Affiliates. Der Affiliate muss **nichts** zippen, nichts hochladen — bekommt nur den **fertigen Live-Link**. Genau dieser Komfort ist gewollt.

**⚠️ EINMALIGE Voraussetzung (pro Affiliate, einmal eingerichtet):**
- Netlify-CLI ist da (läuft via `npx netlify-cli@latest`, keine globale Installation nötig)
- Affiliate ist **einmal eingeloggt**: `npx netlify-cli@latest login` (öffnet Browser → Netlify-Konto verbinden)
- Die **Site-ID** der Affiliate-Site ist bekannt (`npx netlify-cli@latest sites:list` zeigt sie, oder Netlify → Site → Settings → Site ID)

**⚠️ KRITISCH — der Deploy ersetzt das GESAMTE Site-Verzeichnis:**
Alle bisherigen Pages + `_redirects` + `index.html` müssen im **Deploy-Ordner** liegen. Was nicht drin ist, wird live **gelöscht**. Also IMMER aus dem vollständigen Ordner deployen, nie nur die neue Datei.

**⚠️ Dateiname-Regel (`[thema]`):** Immer **nur Kleinbuchstaben, Bindestriche statt Leerzeichen, keine Umlaute/Sonderzeichen**.
Beispiel: „Prompts für Anfänger" → `prompts-fuer-anfaenger.html` (ä→ae, ö→oe, ü→ue, ß→ss). Umlaute/Leerzeichen im Dateinamen = kaputte URL = 404.

**Pro Deploy — exakt in dieser Reihenfolge:**
1. Claude baut neue `[thema].html` im **Pages-Ordner** (= der Ordner mit allen Pages + `_redirects` + `index.html`)
2. Claude erweitert `_redirects` um die neue Zeile (`/[thema]  /[thema].html  200`)
3. **Claude deployt selbst** aus dem Ordner:
   ```bash
   cd ~/PFAD/ZUM/PAGES-ORDNER && npx netlify-cli@latest deploy --prod --dir="." --site="[SITE-ID]"
   ```
   → Netlify deployt sofort, Claude gibt dem Affiliate direkt den **Live-Link** (`ki.realrise-agency.com/[NAME]/[thema]`).
4. **AUTOMATISCHER CHECK (bei JEDER Page — Claude macht das selbst, kostet den Affiliate nichts):**
   Claude prüft die Live-Page direkt nach dem Deploy automatisch:
   - `curl` auf den Live-Link → Status **200**?
   - Formular (`.rr-form`) im HTML vorhanden?
   - **Webhook-URL** korrekt + **`data-source="[NAME]"`** gesetzt + **Redirect absolut** (`https://ki.realrise-agency.com/guides`, nicht relativ)?
   → Fängt die „Regeneration-Drift" (vertippte Webhook-ID, relativer Redirect, vergessene `_redirects`-Zeile) **lückenlos** ab — besser als ein Stichproben-Test, weil's bei *jeder* Page läuft.
5. **MANUELLER TEST-LEAD — nur in diesen Fällen nötig:**
   **(1)** bei der **ersten Page einer Session**, **(2)** nach einem **Template-/Infra-Wechsel**, **(3)** wenn sich **Webhook-URL, Redirect oder `data-source`** geändert haben.
   → Formular mit Test-Vorname + eigener E-Mail absenden → in GHL prüfen ob Kontakt mit Tag `aff:[NAME]` ankommt → Test-Kontakt danach löschen.
   → **Weitere Pages mit identischem Integrations-Block (gleiche Session) brauchen KEINEN manuellen Test** — der automatische Check oben deckt sie ab. So bremst der Workflow bei 3–4 Pages am Stück nicht aus.
   → Hintergrund: Der manuelle Test schützt gegen den katastrophalen **Silent-Fail** (Webhook-Fehler → Leads kommen still nicht an, ohne Fehlermeldung). Den fängt der automatische Check inzwischen mit ab — der manuelle Test ist die Extra-Absicherung dort, wo sich wirklich etwas geändert hat.
6. **IN DIE LIBRARY AUFNEHMEN — PFLICHT-SCHRITT direkt nach jedem Deploy** (übers RealRise-Formular, kein Code, kein Hub-Zugriff):
   **Sobald deine Page live ist, öffnest du SOFORT dieses Formular und füllst es aus** — sonst erscheint deine Page nicht in der Library:
   **https://docs.google.com/forms/d/e/1FAIpQLScRIrGqORVGIsO4WvSwVCZam8Ja9NQVKlujtT54ccwP1hB5IA/viewform**
   Trag ein: **Kategorie** (Setup/Skills/Prompts/Modelle/Workflow) · **Titel** (kurz) · **Beschreibung** (1 Satz, wahr, kein Hype) · **Page-Link im Hub-Format `/[NAME]/[thema]`** · **dein Handle** `@[INSTAGRAM]`.
   RealRise prüft & gibt frei → die Karte erscheint **automatisch** in der Library (`ki.realrise-agency.com`). Kein `index.html`-Bearbeiten, kein Deploy.
   → So wächst die Library mit **jeder** Page — der „wir verkaufen keine Prompts, wir liefern sie täglich gratis"-Beweis.

> Kein ZIP, kein „browse files to upload" mehr. Falls die CLI mal nicht eingeloggt ist (`npx netlify-cli@latest status` prüfen) → einmal `login`, dann wieder direkt deployen.

---

## NETLIFY-SITE-STRUKTUR (FLAT — keine Subordner!)

```
[NETLIFY]/
├── index.html         ← Brand-Hub (Redirect zu [INSTAGRAM] Instagram)
├── _redirects         ← Pretty URL Mapping
├── [thema1].html      ← Tag 1 — flat im Root
├── [thema2].html      ← Tag 2 — flat im Root
└── ...
```

**`_redirects` File:**
```
# Pflicht-Zeile ganz oben
/[NAME]/*        /:splat                   302

/[thema]         /[thema].html             200
```

**Die `/[NAME]/*`-Zeile ist Pflicht** — fehlt sie, gibt es 404 wenn jemand direkt auf `.netlify.app/[NAME]/[thema]` landet.

---

## ⚠️ PFLICHT-CODE-BLÖCKE (1:1 übernehmen, KEINE Variation!)

Technisch validiert und Mobile-getestet. Variation = Bugs auf Mobile.

### A. Lead-Formular → GHL Inbound Webhook (im Hero UND in der Early-Access-Sektion)

Eigenes Formular (KEIN iframe) → postet Name + E-Mail direkt an den GHL Opt-in-Webhook. Volle Design-Kontrolle, Claude-oranger Marken-Button, eigene Legal-Links, Consent + Honeypot (DSGVO + Spam). **Komplett 1:1 übernehmen.**

**Pflicht:**
- `data-source="[NAME]"` → steuert automatisch `aff:[NAME]` (dein Tracking-Tag)
  → ⚠️ **`data-source` ist IMMER dein festes Affiliate-Kürzel (z.B. `regina`) — NIEMALS der Seitenname, das Thema oder der Reel-Name.** Egal ob die Page `/datei`, `/routines` oder `/fable` heißt: `data-source` bleibt dein Kürzel. Sonst entstehen kaputte Tags wie `aff:datei` statt `aff:regina`.
- `data-placement` setzen: im Hero `="hero"`, in der Early-Access-Sektion `="early"` (sonst sind beide Formulare im Tracking nicht unterscheidbar)
- **Consent-Checkbox + Honeypot (`.rr-hp`) IMMER drin**
- Webhook-URL exakt übernehmen · Formular im **Hero UND Early-Access**
- **Redirect-Ziel = absolute URL `https://ki.realrise-agency.com/guides`** (NICHT `/guides` relativ!) — die Survey-Seite liegt auf der Hub-Site, nicht auf deiner Netlify-Site. Mit `/guides` relativ landen deine Leads im 404.
  → **Pflicht:** die E-Mail mit `?email='+encodeURIComponent(m)` anhängen (`…/guides?email=…`). Nur so kann die Survey (`/guides`) die Antworten + Telefonnummer dem richtigen GHL-Kontakt zuordnen. Ohne den Param speichert die Survey nichts.
  → **Funnel-Flow (Pre-Launch):** Opt-in (Name+E-Mail) → **`/guides` = kurze Survey (Pflicht-Gate, ~6 Fragen + Telefon)** → **`/vip` = Zugang freigeschaltet** (WhatsApp-Gruppe + Library). Die Survey ist der Schlüssel zum Inner Circle, kein optionaler Nebenschritt. Telefon wird als „WhatsApp-Zugang" geframt (Pull, kein Druck).
- Das alte `<iframe>` + `form_embed.js` entfallen komplett (durch dieses Formular ersetzt).

**1. CSS** (einmal in den `<style>`):
```css
.rr-form{display:flex;flex-direction:column;gap:14px;text-align:left}
.rr-field{display:flex;flex-direction:column;gap:6px}
.rr-field label{font-size:11px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--gray)}
.rr-field input{width:100%;padding:13px 15px;background:#fff;border:1.5px solid var(--line);border-radius:12px;font-family:var(--sans);font-size:15px;color:var(--ink);transition:border-color .15s,box-shadow .15s}
.rr-field input:focus{outline:none;border-color:var(--coral);box-shadow:0 0 0 3px rgba(217,119,87,.12)}
.rr-field input::placeholder{color:#9aa0ab}
.rr-consent{display:flex;align-items:flex-start;gap:9px;font-size:12px;line-height:1.45;color:var(--gray2);cursor:pointer}
.rr-consent input{margin-top:2px;width:15px;height:15px;flex-shrink:0;accent-color:var(--coral)}
.rr-consent a{color:var(--coral);text-decoration:underline;text-underline-offset:2px}
.rr-submit{width:100%;padding:15px;background:var(--coral);color:#fff;border:none;border-radius:980px;font-family:var(--sans);font-size:15px;font-weight:600;letter-spacing:.01em;cursor:pointer;transition:background .2s,transform .2s;box-shadow:0 10px 26px -10px rgba(217,119,87,.55)}
.rr-submit:hover{background:var(--coral-deep);transform:translateY(-1px)}
.rr-submit:disabled{opacity:.6;cursor:not-allowed;transform:none}
.rr-trust{display:flex;gap:14px;flex-wrap:wrap;font-size:11px;font-weight:500;letter-spacing:.02em;text-transform:uppercase;color:var(--gray)}
.rr-trust span::before{content:'✓';color:var(--green);margin-right:5px;font-weight:700}
.rr-hp{position:absolute!important;left:-9999px!important;width:1px!important;height:1px!important;overflow:hidden!important;opacity:0!important}
.rr-error{display:none;font-size:13px;color:#c0392b;padding:10px 12px;background:rgba(192,57,43,.07);border:1px solid rgba(192,57,43,.25);border-radius:8px}
.rr-error.show{display:block}
.rr-success{display:none;text-align:center;padding:24px;background:rgba(26,138,74,.08);border:1px solid rgba(26,138,74,.3);border-radius:12px}
.rr-success.show{display:block}
.rr-success h4{font-size:22px;font-weight:700;letter-spacing:-.02em;color:var(--ink);margin-bottom:6px}
.rr-success p{font-size:14px;color:var(--gray2)}
```

**2. HTML** (im Hero UND in Early-Access — `data-source` = dein Affiliate-Kürzel `[NAME]`, **NIE** der Seitenname/das Thema):
```html
<form class="rr-form" data-source="[NAME]" data-placement="hero" novalidate>
  <div class="rr-field"><label>Vorname</label>
    <input type="text" name="first_name" placeholder="Dein Vorname" autocomplete="given-name" required></div>
  <div class="rr-field"><label>E-Mail</label>
    <input type="email" name="email" placeholder="deine@email.de" autocomplete="email" required></div>
  <input type="text" name="website" class="rr-hp" tabindex="-1" autocomplete="off" aria-hidden="true">
  <label class="rr-consent"><input type="checkbox" name="consent" required>
    <span>Ich bin einverstanden, von RealRise E-Mails zu erhalten. Jederzeit abmeldbar. <a href="https://realrise-agency.com/datenschutz" target="_blank" rel="noopener">Datenschutz</a>.</span></label>
  <button type="submit" class="rr-submit">Zugang sichern →</button>
  <div class="rr-trust"><span>Kostenlos</span><span>Kein Spam</span><span>Jederzeit abmeldbar</span></div>
  <div class="rr-error" role="alert"></div>
  <div class="rr-success"><h4>Top, du bist dabei!</h4><p>Check deine Mails — dein Zugang ist unterwegs.</p></div>
</form>
```

**3. JS** (einmal vor `</body>`):
```html
<script>
(function(){
  const RR_WEBHOOK='https://services.leadconnectorhq.com/hooks/kzqtcVUjWkDlITNXDAUU/webhook-trigger/WbIflDi1OLz9gGFHjbWN';
  const RE=/^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  document.querySelectorAll('form.rr-form').forEach(function(f){f.addEventListener('submit',async function(e){e.preventDefault();
    const err=f.querySelector('.rr-error'),ok=f.querySelector('.rr-success'),b=f.querySelector('.rr-submit');
    const n=(f.first_name.value||'').trim(),m=(f.email.value||'').trim();err.classList.remove('show');
    if(f.website.value)return;
    if(n.length<2){err.textContent='Bitte gib deinen Vornamen ein.';err.classList.add('show');return;}
    if(!RE.test(m)){err.textContent='Bitte gib eine gültige E-Mail ein.';err.classList.add('show');return;}
    if(!f.consent.checked){err.textContent='Bitte stimme dem Datenschutz zu.';err.classList.add('show');return;}
    b.disabled=true;b.textContent='Wird gesendet …';
    function done(){['.rr-field','.rr-consent','.rr-submit','.rr-trust'].forEach(s=>f.querySelectorAll(s).forEach(el=>el.style.display='none'));ok.classList.add('show');setTimeout(()=>location.href='https://ki.realrise-agency.com/guides?email='+encodeURIComponent(m),1300);}
    try{const r=await fetch(RR_WEBHOOK,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({first_name:n,email:m,source:f.dataset.source||'',placement:f.dataset.placement||'',consent:true})});if(!r.ok)throw 0;done();}
    catch(_){b.disabled=false;b.textContent='Zugang sichern →';err.textContent='Etwas ist schiefgelaufen. Bitte nochmal.';err.classList.add('show');}
  });});
})();
</script>
```

### B. Meta Pixel (im `<head>`)

```html
<!-- Meta Pixel Code -->
<script>
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window, document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', '1367349055288604');
fbq('track', 'PageView');
</script>
<noscript><img height="1" width="1" style="display:none"
src="https://www.facebook.com/tr?id=1367349055288604&ev=PageView&noscript=1"
/></noscript>
<!-- End Meta Pixel Code -->
```

**Pixel-ID: `1367349055288604`** — niemals ändern. Geht in jeden `<head>`.

### C. Footer mit Impressum + Datenschutz (Pflicht auf JEDER Seite!)

⚠️ **Rechtlich Pflicht (DE).** RealRise sammelt die Leads → Impressum + Datenschutz zeigen IMMER auf `realrise-agency.com`. Diese Links NIE ändern, NIE weglassen, NIE durch eigene/leere ersetzen.

CSS (in den `<style>`-Block):
```css
footer { background: var(--dark); padding: 32px 40px; border-top: 1px solid rgba(255,255,255,0.07); }
.footer-inner { max-width: var(--max-w); margin: 0 auto; display: flex; align-items: center; justify-content: space-between; }
.footer-brand { font-family: var(--mono); font-size: 12px; color: rgba(255,255,255,0.20); letter-spacing: 0.08em; }
.footer-links { display: flex; gap: 24px; }
.footer-links a { font-size: 13px; color: rgba(255,255,255,0.20); text-decoration: none; transition: color 0.15s; }
.footer-links a:hover { color: rgba(255,255,255,0.55); }
@media (max-width: 768px) {
  footer { padding: 32px 20px; }
  .footer-inner { flex-direction: column; gap: 16px; text-align: center; }
}
```

HTML (direkt vor `</body>`, nur den `@handle` bei footer-brand auf [INSTAGRAM] setzen):
```html
<footer>
  <div class="footer-inner">
    <div class="footer-brand">REALRISE · [INSTAGRAM] · © 2026</div>
    <div class="footer-links">
      <a href="https://realrise-agency.com/impressum">Impressum</a>
      <a href="https://realrise-agency.com/datenschutz">Datenschutz</a>
    </div>
  </div>
</footer>
```

---

## 🎨 DESIGN SYSTEM — REALRISE FLAGSHIP (Apple-White)

> **Design-Referenz (1:1-Vorlage):** `02_Master_Prompt/_REFERENZ-TEMPLATE.html` + jede Live-Seite (z. B. `04_Daniel_Pages/loops.html`). CSS, Layout & Komponenten daraus 1:1 übernehmen — nur Content + `data-source="[DEIN-KÜRZEL]"` tauschen.
>
> ⚠️ Der frühere cream/Cormorant-„VIBECADEMY"-Look ist **abgelöst**. Alle RealRise-Seiten laufen jetzt im **Apple-White-Flagship-Look** (wie realrise-agency.com): ruhig, clean, System-Fonts.

### CSS-Variablen (Flagship)

```css
:root{
  --sans:-apple-system,'SF Pro Display','SF Pro Text','Inter',system-ui,sans-serif;
  --mono:ui-monospace,'SF Mono','SFMono-Regular',Menlo,Consolas,monospace;
  --bg:#F5F5F7; --card:#FFFFFF; --ink:#1D1D1F; --gray:#86868B; --gray2:#6E6E73;
  --line:#E5E5E7; --coral:#d97757; --coral-deep:#a8542e; --green:#1A8A4A;
  --dark:#161312;
  --radius:20px; --shadow:0 2px 10px rgba(0,0,0,.04), 0 10px 34px rgba(0,0,0,.06);
  --spring:cubic-bezier(.4,1.3,.5,1);
}
```

**KEINE** Google-Fonts, kein Cormorant, kein DM Sans/Mono → durchgängig System-SF (`var(--sans)`), Code in System-Mono (`var(--mono)`). Hintergrund flach `#F5F5F7` — **keine** radialen Blobs, **kein** Grid-Pattern, **keine** Scanline/Partikel/Hero-Stage-Animationen (der alte Premium-Deko-Kram entfällt — der ruhige Apple-Look IST der Premium-Look).

### Grundregeln

- **Headlines:** BOLD System-Font (`font-weight:700`), tight `letter-spacing:-.03em`. KEIN Serif, kein Kursiv. Akzentwort als `<em>` in Coral: `h1 em{font-style:normal;color:var(--coral)}`.
- **Akzentfarbe:** Coral `#d97757` (Hover `#a8542e`). WhatsApp-Grün `#25d366` nur für WA-Buttons.
- **Buttons:** 980px-Pills. Primär `.btn-p` (Coral/weiß), Sekundär `.btn-s` (outline). `.rr-submit` = Coral-Pill, volle Breite.
- **Eyebrow `.ey`:** Coral, uppercase, 12px/600, kurzer Coral-Strich davor (`::before`, 22px).
- **Cards `.card`:** weiß, `--line`-Border, `--radius` (20px), `--shadow`, Hover `translateY(-4px)`. Raster `.g2` / `.g3`. Icon-/Nummern-Badge `.ic` (44px, `#F5F1EE`, Coral-Zahl).
- **Dunkle Sektionen `.dark` / `.early`:** bg `#161312` + Coral-Radial-Glow (`::before`), weiße Headline mit Coral-`<em>`. Für „Alle N" (Karten `.dcard`) + Community/Early-Access.
- **Code-Boxen `.code` / `.dcode`:** dunkel `#161312`, System-Mono, `white-space:pre-line`, Copy-Button oben rechts; mobil `@media(max-width:820px){.code,.dcode{font-size:11px;line-height:1.62}}`.
- **Reveal:** `.rev` → Klasse `.in` per IntersectionObserver (opacity/translateY). Keine schweren Hero-Animationen mehr.

### Opt-in-Card `.optin` (Pflicht — im Hero UND Early-Access)

Weiße Card (`--radius`, weicher Shadow): Label „Early Access" + Coral-Pill „Kostenlos" oben, Titel, dann die **rr-form** (Pflicht-Block A — Vorname, E-Mail, Handynummer, Consent, Coral-Pill-Submit, Trust-Zeile). In `.early` = dieselbe weiße Card auf dunklem `#161312`-Grund (starker Kontrast = „beitretens-wert").

### Instagram-CTA-Card `.ig-cta` (letzter Slot in der Dark-Section — immer)

```html
<div class="ig-cta" style="grid-column:1/-1">
  <div>
    <div class="k">Täglich neues KI-Wissen</div>
    <div class="big">Jeden Tag ein Tipp, der dir wirklich Zeit spart.</div>
  </div>
  <div>
    <p>Diese [X] Tipps sind der Anfang. Auf Instagram poste ich täglich neue — direkt anwendbar, kein Fluff.</p>
    <a class="ig-btn" href="https://www.instagram.com/[INSTAGRAM_OHNE_@]" target="_blank" rel="noopener">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="0.5" fill="currentColor"/></svg>
      [INSTAGRAM] folgen
    </a>
  </div>
</div>
```

`.ig-btn` behält den Instagram-Verlauf (`linear-gradient(90deg,#833ab4,#e1306c,#fd1d1d,#f77737,#fcaf45)`) als 980px-Pill. Alle Styles siehe `_REFERENZ-TEMPLATE.html`.

### Layout folgt dem Content (nicht stur dasselbe Skelett)

Reihenfolge-Baukasten wie in `loops.html`: **Hero (Bold-H1 + Opt-in-Card)** → **How/3 Schritte (`.g3`)** → **Top-3 (`.prompt` + `.code`)** → **Dark „Alle N" (`.dcard`/`.dcode` + `.ig-cta`)** → **Bonus (`.g2`)** → **Community/Early-Access (`.early` + Opt-in-Card)** → **Footer**. Vergleichs-Themen (z. B. Modell A vs. B) dürfen eine Vergleichs-Sektion im dunklen `.dark`-Stil bekommen (siehe `fable.html`).

## ✅ QUALITY CHECK VOR JEDER PAGE (Pflicht)

**Meta Pixel:**
- [ ] Pixel-Code im `<head>` vorhanden?
- [ ] ID `1367349055288604` korrekt?

**Lead-Formular (`.rr-form` — beide: Hero + Early Access):**
- [ ] `data-source="[NAME]"` korrekt (NICHT der eines anderen Affiliates!)?
- [ ] `data-placement` gesetzt (Hero = `hero`, Early Access = `early`)?
- [ ] Consent-Checkbox + Honeypot (`.rr-hp`) vorhanden?
- [ ] Webhook-URL exakt übernommen (Opt-in-Webhook)?
- [ ] Redirect-Ziel = absolute URL `https://ki.realrise-agency.com/guides` (NICHT `/guides` relativ)?
- [ ] `.rr-form`-JS-Handler einmal vor `</body>`?
- [ ] KEIN altes `<iframe>` / `form_embed.js` mehr drin?

**Rechtliches (Pflicht — DE):**
- [ ] Footer (Block C) vorhanden mit Impressum + Datenschutz → `realrise-agency.com`?
- [ ] Consent-Checkbox im Formular mit Datenschutz-Link?
- [ ] Links zeigen auf `realrise-agency.com` (NICHT example.com / leer / eigene Domain)?

**Design:**
- [ ] Body hat radial blobs (kein flächiges Grid)?
- [ ] Hero und Top3 haben Grid, How-to und Bonus nicht?
- [ ] hero-stage + hero-energy-field + hero-scanline vorhanden?
- [ ] Alle 4 Keyframes vorhanden?
- [ ] Normale Cards: warm-brown shadow; Hero/Form-Cards: orange-glow?
- [ ] Instagram CTA Card ([INSTAGRAM]) als letzter Slot in Dark Section?
- [ ] Dunkle Sektionen/CTA: ORANGE Akzente + solid-oranger Button (KEIN Gold/Warm/Lila)?
- [ ] Early Access: Benefits-Liste (orange ✓) + Trust-Reihe (nicht nur 1 Satz)?
- [ ] **Nummern überall als IDENTISCHES Badge** (40×40px, radius 12, getönt, nur die Zahl) — KEINE Text-Nummern, keine Label-Suffixe wie „Top Hebel"/„Bonus"? (hell = orange-pale/orange · dunkel = orange-tint/#e0a890)
- [ ] Code-Boxen ÜBERALL solid `#1a1714` (kein halbtransparentes Grau auf hellen Cards)?
- [ ] `.code-box` hat `position:relative` + `padding-top:48px`? (sonst überlappt der Kopieren-Button die erste Code-Zeile)
- [ ] Eyebrows einheitlich: Mono + orange Gradient-Linie (orange→orange, hell wie dunkel) — NIE warm/gold?
- [ ] KONSEQUENT CLAUDE-ORANGE: nirgends Gold/Warm/Lila als Akzent (nur Grün #22A155 für live-Punkt + Trust-Häkchen)?
- [ ] Scroll Reveal vorhanden?
- [ ] `@media (max-width: 900px)` Block vorhanden?

**Deploy:**
- [ ] Dateiname nur Kleinbuchstaben + Bindestriche, keine Umlaute/Leerzeichen?
- [ ] HTML flat im Root (kein Subordner)?
- [ ] `_redirects` hat neue Zeile für das Thema?
- [ ] `_redirects` hat `/[NAME]/* /:splat 302` ganz oben?
- [ ] Direkt via `netlify-cli deploy --prod` deployed (kompletter Pages-Ordner, nicht nur die neue Datei)?
- [ ] **NACH Deploy: Auto-Check gelaufen?** (curl → 200 · `.rr-form` da · Webhook-URL + `data-source="[NAME]"` + absoluter `/guides`-Redirect korrekt) — bei JEDER Page
- [ ] **Manueller Test-Lead** (in GHL mit `aff:[NAME]` angekommen?) — nur bei **erster Page der Session / Template- oder Infra-Wechsel / geänderten Integrations-Werten**
- [ ] **In die Library eingereicht?** Page übers RealRise-Library-Formular eingereicht (Kategorie · Titel · Beschreibung · Page-Link `/[NAME]/[thema]` · Handle)?

**Bei ❌ → Fehler beheben → nochmal prüfen → dann liefern.**

---

## 🧩 LAYOUT FOLGT DEM CONTENT-TYP (nicht stur dasselbe Skelett!)

⚠️ **Wichtigstes Page-Prinzip:** Die Struktur muss zum **Thema** passen — nicht jedes Reel ist „6 Prompts". Wähle das Layout nach Content-Typ:

| Content-Typ | Bestes Layout |
|---|---|
| **Vergleich / „X vs Y" / „wann was"** | **2 VS-Cards nebeneinander + Entscheidungs-Tabelle** („Deine Aufgabe → Nimm") + „so stellst du um"-Steps. Viel scanbarer & überzeugender als Prompt-Listen. |
| **„X Prompts / Hacks / Tipps"** | Top-3-Cards (mit Code-Box zum Kopieren) + Dark-Grid mit allen X + Bonus |
| **Anleitung / Setup („in X Schritten")** | Nummerierte Steps groß + Code-Boxen pro Schritt |
| **Tool/Feature-Vorstellung** | Fakten-Cards (3×) + „so nutzt du es"-Steps + Beispiel |

Das Design-System (Farben, Fonts, Hero, Eyebrows, Dark-Section, Custom-Form, Footer, Claude-Orange) bleibt **immer identisch** — nur die **Sektions-Bausteine in der Mitte** richten sich nach dem Thema.

### VS-Pattern (für Vergleichs-Themen) — Bausteine:
- **Hero** mit optionalem Warn-Banner (`.req-banner`) für ein Zeitfenster/Vorsicht-Hinweis
- **3 Fakten-Cards** (`.cards3` / `.pc` mit großer Zahl `.big`)
- **Dark „Entscheidung"-Sektion:** 2 `.vs-card` (eine `.opus`, eine `.fable` hervorgehoben) + `.dtable` (Aufgabe→Modell) + `.switch` (nummerierte „so stellst du um"-Steps)
- **Quellen-Zeile** (`.honest`) unter der Tabelle

### ⚠️ Zahlen & Quellen (Wahrheitspflicht — hart!):
- **Konkrete Zahlen schlagen vages Hedging** ($10/$50 statt „kostet mehr") — ABER **nur wenn verifiziert.**
- Behauptest du Preise/Daten/Benchmarks → **erst recherchieren/bestätigen**, dann eine **Quelle** angeben (z.B. `platform.claude.com/docs`).
- Nicht verifizierbar → qualitativ formulieren oder weglassen. Niemals Zahlen aus einem fremden Reel ungeprüft übernehmen.

---

## FUNNEL-PAGE STRUKTUR

**Fonts:** System-SF (`-apple-system` / SF Pro / Inter → `var(--sans)`) — **keine** Google-Fonts mehr. Code in System-Mono (`var(--mono)`).

1. **NAV** — Fixed, glasmorphism, Links: „RealRise / [THEMA]", Rechts: „Top 3" · „Alle [X]" · „Bonus" · „Community"
2. **HERO** (Grid ✅) — hero-stage + energy-field + scanline, Links: H1 + Subtitle, Rechts: hero-card (orange-glow) + **Lead-Formular** (`.rr-form`, `data-source="[NAME]"`)
   - ⚠️ **Hero-Card-Titel = „Werde Teil der RealRise Community"** (Button „Zugang sichern →"). Die Opt-in-Karte beschreibt IMMER den **Early Access zur RealRise Community** — NICHT das Reel-Thema als Köder („Hol dir die XY"). Das Thema lebt in H1/Subtitle links, die Karte rechts beschreibt, wofür man sich einträgt.
3. **HOW TO USE** (Grid ❌) — 3 Steps, warm-brown shadow
4. **TOP 3** (Grid ✅) — 3× prompt-card, warm-brown shadow
5. **ALLE X DARK** (Grid ❌) — Canvas-Animation, X× dark-prompt-card + Instagram-CTA-Card
6. **BONUS** (Grid ❌) — 4× bonus-card
7. **EARLY ACCESS DARK** (Grid ✅ dezent) — Links: Headline + **Benefits-Liste (orange ✓) + Trust-Reihe** (NIE nur 1 Satz!), Rechts: **Lead-Formular** (`.rr-form`, `data-source="[NAME]"`) in weißem Wrapper
8. **FOOTER** — Block C 1:1 übernehmen (Impressum + Datenschutz → realrise-agency.com, Pflicht!)
9. **SCRIPTS** (vor `</body>`) — `.rr-form`-Handler (Block A.3) → copyText() → Canvas-IIFE → Scroll-Reveal-IIFE

---

## LEAD-VERARBEITUNG (GHL — automatisch)

Das Lead-Formular (`.rr-form`, Block A) postet direkt an den **GHL Opt-in-Webhook**. Es gibt **keinen iframe mehr** — die alte `widget/form`-URL ist Geschichte, nicht mehr verwenden.

Jeder Lead wird automatisch:
- In Daniels GHL gespeichert (Create/Update Contact)
- Mit `source=[NAME]` (aus `data-source`) getrackt
- Getaggt: `lead`, `community-funnel`, `aff:[NAME]`
- Bekommt die E-Mail-Sequenz (Single Opt-in)

**Affiliate braucht in GHL nichts einzurichten** — der Webhook in Block A ist fertig verdrahtet.

---

## DOMAIN-STRUKTUR

**Public-URL:** `ki.realrise-agency.com/[NAME]/[thema]`
**Affiliate Netlify:** `[NETLIFY]/[thema]`

---

## LESSONS LEARNED (aus Live-Deploys)

**Technisch:**
1. `data-source` falsch/leer → Lead landet ohne `aff:[NAME]` (Attribution kaputt)
2. Webhook-URL mit Tippfehler → Leads kommen **still** NICHT an (kein sichtbarer Fehler!) → **Auto-Check pro Page fängt das ab; manueller Test-Lead bei erster/geänderter Page**
3. Consent-Checkbox oder Honeypot (`.rr-hp`) vergessen → DSGVO-Risiko + Spam
4. `/[NAME]/*` fehlt in `_redirects` → 404
5. `?source=`/`data-source` falscher Affiliate → Leads falsch zugeordnet
6. Aus unvollständigem Ordner deployed → alle anderen Pages gelöscht (immer den ganzen Pages-Ordner via netlify-cli deployen)
7. Redirect `/guides` relativ statt absolut → Lead landet nach Anmeldung im 404 (Survey-Seite liegt auf Hub-Site!)
8. Dateiname mit Umlaut/Leerzeichen → URL kaputt → 404
9. Auto-Check übersprungen UND kein Test-Lead bei geänderten Werten → Webhook-Fehler bleibt unbemerkt, Reel läuft, Leads gehen verloren

**Design:**
10. Plumpe Schatten `0 4px 24px rgba(...)` → billig wirken
11. Grid auf body → sichtbare Breaks zwischen Sections
12. Orange-shadow auf normalen Cards → Featured-Signal geht verloren
13. Grid-Farbe cool-blau statt warm → wirkt kalt

**Deploy:**
14. Hub-Site `_redirects` nicht aktualisiert + nicht redeployed → alle `ki.realrise-agency.com/[NAME]/*` URLs sofort 404 (auch wenn Affiliate-Netlify-Site korrekt läuft!)

**Der Quality Check oben verhindert alle 14 zuverlässig.**

---

## INHALTLICHE REGELN

- Alle Prompts/Tipps **vollständig sichtbar** — nichts gated
- Jeder Prompt hat **Kopieren-Button**
- **Lead-Formular** (`.rr-form`) in **Hero + Early Access** mit `data-source="[NAME]"`
- Instagram-CTA **[INSTAGRAM]** als letzter Slot in Dark Section
- Meta Pixel **`1367349055288604`** im `<head>`
- **Tonalität:** Premium, zugänglich, Du-Form

---

**STARTE wenn [INSTAGRAM] Hook + Caption + Reel-Inhalt schickt.** 🔥
