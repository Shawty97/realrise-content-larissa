# REALRISE AFFILIATE MASTERPROMPT v2.2
# ──────────────────────────────────────────────────────────
# 🆕 NEU IN v2.2 (bitte ab jetzt diese Version nutzen):
#   • Opt-in-Formular: eigenes Custom-Formular statt GHL-iframe
#     (Claude-oranger Marken-Button, Consent + Honeypot, kein example.com) — Block A
#   • Farb-Identität: KONSEQUENT CLAUDE-ORANGE #CC785C (Akzent überall, kein Blau/Gold/Lila)
#   • Nummern überall als identisches Badge · Code-Boxen solid · Eyebrows einheitlich
#   • Early-Access: Benefits-Liste (orange ✓) + Trust-Reihe (nie nur 1 Satz)
#   • iframe + form_embed.js entfallen komplett
#   • Footer (Impressum + Datenschutz) als Pflicht-Code-Block — Block C
#   • SKALIER-FIXES (für externe Affiliates wichtig!):
#       – Redirect nach Anmeldung = absolute Hub-URL (kein 404 mehr)
#       – Pflicht-Test-Lead nach jedem Deploy (fängt Silent-Webhook-Fail)
#       – Dateiname-Regel (Kleinbuchstaben, keine Umlaute) gegen 404
# ──────────────────────────────────────────────────────────
# VOR DEM ERSTEN EINSATZ: Diese 3 Platzhalter ersetzen:
#
#   [NAME]       → dein Affiliate-Name in Kleinbuchstaben (= dein GHL-Tracking-Tag)
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
2. **Funnel-Page (HTML) erstellen** — der gesamte Reel-Content komplett ausformuliert mit Kopier-Buttons
3. Page im **Staging-Ordner** speichern → in **Live-Ordner** kopieren → Deploy-Workflow

**Kein PDF.** Die Page ist der einzige Output.

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

## DEPLOY-WORKFLOW — ZWEI ORDNER SYSTEM (kritisch!)

**⚠️ KRITISCH — Live-Ordner ≠ Staging-Ordner:**
Das ZIP muss IMMER aus dem **Live-Ordner** gebaut werden. Netlify-Deploys ersetzen das gesamte Site-Verzeichnis — was nicht im ZIP ist, wird live **gelöscht**.

**Ordner-Struktur:**
```
Staging-Ordner (neue Pages werden hier gebaut):
→ [thema].html kommt hier zuerst hin

Live-Ordner (enthält ALLE bisherigen Pages + _redirects + index.html):
→ Von hier wird das ZIP gebaut und auf Netlify hochgeladen
```

**⚠️ Dateiname-Regel (`[thema]`):** Immer **nur Kleinbuchstaben, Bindestriche statt Leerzeichen, keine Umlaute/Sonderzeichen**.
Beispiel: „Prompts für Anfänger" → `prompts-fuer-anfaenger.html` (ä→ae, ö→oe, ü→ue, ß→ss). Umlaute/Leerzeichen im Dateinamen = kaputte URL = 404.

**Pro Deploy — exakt in dieser Reihenfolge:**
1. Claude baut neue `[thema].html` im **Staging-Ordner**
2. Claude kopiert die Page in den **Live-Ordner**
3. Claude erweitert `_redirects` im **Live-Ordner** um neue Zeile
4. Claude zippt den **kompletten Live-Ordner**
5. Affiliate lädt ZIP auf `[NETLIFY]` hoch (über „browse files to upload")
6. Netlify entpackt + deployt → Public-URL funktioniert sofort
7. **PFLICHT-TEST: einen echten Test-Lead absenden** — Formular mit Test-Vorname + eigener E-Mail ausfüllen, abschicken, dann in GHL prüfen ob der Kontakt mit Tag `aff:[NAME]` ankommt. Erst danach das Reel posten.
   → Das ist die EINZIGE Absicherung gegen den Silent-Fail (Webhook-Tippfehler → Leads kommen still nicht an, ohne Fehlermeldung). Test-Kontakt danach in GHL löschen.

**ZIP-Befehl Windows (PowerShell):**
```powershell
$src = "PFAD\ZUM\LIVE-ORDNER"
$dst = "PFAD\ZUM\DESKTOP\[NAME]-netlify-deploy.zip"
if (Test-Path $dst) { Remove-Item $dst -Force }
Compress-Archive -Path "$src\*" -DestinationPath $dst -Force
```

**ZIP-Befehl Mac (Bash):**
```bash
cd ~/PFAD/ZUM/LIVE-ORDNER && zip -r ~/Desktop/[NAME]-netlify-deploy.zip . -x ".DS_Store"
```

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
- `data-placement` setzen: im Hero `="hero"`, in der Early-Access-Sektion `="early"` (sonst sind beide Formulare im Tracking nicht unterscheidbar)
- **Consent-Checkbox + Honeypot (`.rr-hp`) IMMER drin**
- Webhook-URL exakt übernehmen · Formular im **Hero UND Early-Access**
- **Redirect-Ziel = absolute URL `https://ki.realrise-agency.com/vip`** (NICHT `/vip` relativ!) — die VIP-Seite liegt auf der Hub-Site, nicht auf deiner Netlify-Site. Mit `/vip` relativ landen deine Leads im 404.
- Das alte `<iframe>` + `form_embed.js` entfallen komplett (durch dieses Formular ersetzt).

**1. CSS** (einmal in den `<style>`):
```css
.rr-form{display:flex;flex-direction:column;gap:14px;text-align:left}
.rr-field{display:flex;flex-direction:column;gap:6px}
.rr-field label{font-family:'DM Mono',monospace;font-size:10px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted)}
.rr-field input{width:100%;padding:13px 15px;background:#fff;border:1.5px solid var(--border-med);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:15px;color:var(--dark-nav)}
.rr-field input:focus{outline:none;border-color:var(--blue);box-shadow:0 0 0 3px rgba(204,120,92,.12)}
.rr-consent{display:flex;align-items:flex-start;gap:9px;font-size:12px;line-height:1.45;color:var(--muted);cursor:pointer}
.rr-consent input{margin-top:2px;width:15px;height:15px;flex-shrink:0;accent-color:var(--blue)}
.rr-consent a{color:var(--blue);text-decoration:underline}
.rr-submit{width:100%;padding:15px;background:var(--blue);color:#fff;border:none;border-radius:10px;font-family:'DM Mono',monospace;font-size:13px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;box-shadow:0 10px 26px -10px rgba(204,120,92,.55)}
.rr-submit:hover{background:#b5634a;transform:translateY(-1px)}
.rr-submit:disabled{opacity:.6;cursor:not-allowed}
.rr-trust{display:flex;gap:14px;flex-wrap:wrap;font-family:'DM Mono',monospace;font-size:10px;text-transform:uppercase;color:var(--muted)}
.rr-trust span::before{content:'✓';color:#22A155;margin-right:5px;font-weight:700}
.rr-hp{position:absolute!important;left:-9999px!important;width:1px!important;height:1px!important;overflow:hidden!important;opacity:0!important}
.rr-error{display:none;font-size:13px;color:#c0392b;padding:10px 12px;background:rgba(192,57,43,.07);border:1px solid rgba(192,57,43,.25);border-radius:8px}
.rr-error.show{display:block}
.rr-success{display:none;text-align:center;padding:24px;background:rgba(34,161,85,.08);border:1px solid rgba(34,161,85,.3);border-radius:12px}
.rr-success.show{display:block}
.rr-success h4{font-family:'Cormorant Garamond',serif;font-size:24px;font-weight:500;color:var(--dark-nav);margin-bottom:6px}
.rr-success p{font-size:14px;color:var(--muted)}
```

**2. HTML** (im Hero UND in Early-Access — `data-source` = dein `[NAME]`):
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
    function done(){['.rr-field','.rr-consent','.rr-submit','.rr-trust'].forEach(s=>f.querySelectorAll(s).forEach(el=>el.style.display='none'));ok.classList.add('show');setTimeout(()=>location.href='https://ki.realrise-agency.com/vip',1300);}
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
fbq('init', '1343968131131688');
fbq('track', 'PageView');
</script>
<noscript><img height="1" width="1" style="display:none"
src="https://www.facebook.com/tr?id=1343968131131688&ev=PageView&noscript=1"
/></noscript>
<!-- End Meta Pixel Code -->
```

**Pixel-ID: `1343968131131688`** — niemals ändern. Geht in jeden `<head>`.

### C. Footer mit Impressum + Datenschutz (Pflicht auf JEDER Seite!)

⚠️ **Rechtlich Pflicht (DE).** RealRise sammelt die Leads → Impressum + Datenschutz zeigen IMMER auf `realrise-agency.com`. Diese Links NIE ändern, NIE weglassen, NIE durch eigene/leere ersetzen.

CSS (in den `<style>`-Block):
```css
footer { background: var(--dark); padding: 32px 40px; border-top: 1px solid rgba(255,255,255,0.07); }
.footer-inner { max-width: var(--max-w); margin: 0 auto; display: flex; align-items: center; justify-content: space-between; }
.footer-brand { font-family: 'DM Mono', monospace; font-size: 12px; color: rgba(255,255,255,0.20); letter-spacing: 0.08em; }
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

## 🎨 DESIGN SYSTEM v2.2 — VIBECADEMY LEVEL

> **Design-Referenz:** Die zuletzt erstellte Page im Live-Ordner ist die 1:1 Vorlage.
> Layout, CSS, Animationen bleiben identisch — nur Inhalte + `?source=[NAME]` tauschen.

### CSS-Variablen

```css
:root {
  --cream:         #f8f4eb;
  --cream-card:    #fffdf8;
  --dark:          #0f0f0f;
  --dark-2:        #1a1714;
  --dark-nav:      #20283a;
  /* ⚠️ Akzentfarbe = Claude-Terracotta #cc785c. Variable heißt historisch --blue, enthält aber ORANGE. */
  --blue:          #cc785c;
  --blue-pale:     #f8efe9;
  --gold:          #d8b45a;
  --warm:          #b46b4e;
  --muted:         #586174;
  --border:        rgba(32,40,58,0.10);
  --border-med:    rgba(32,40,58,0.16);
  /* Warm-brown: normale Cards */
  --shadow-card-warm: 0 24px 70px -46px rgba(55,39,25,0.55);
  /* Blue-glow: nur hero-card & early-right-card */
  --shadow-card-blue: 0 20px 70px -58px rgba(32,40,58,0.70), 0 28px 80px -54px rgba(204,120,92,0.48);
  --shadow-dark:   0 26px 80px -56px rgba(23,19,18,0.90), 0 30px 90px -54px rgba(204,120,92,0.50);
  --code-bg:       #1a1714;
  --code-fg:       #f0ece4;
  --max-w:         1200px;
  --grid-line:     rgba(23,19,18,0.055);   /* warm — NICHT cool-blau */
  --grid-size:     44px;
}
```

### Body (radial blobs — kein flächiges Grid!)

```css
body {
  background-color: var(--cream);
  background-image:
    radial-gradient(circle at 12% 0%, rgba(204,120,92,0.18) 0%, transparent 28rem),
    radial-gradient(circle at 88% 6%, rgba(204,120,92,0.12) 0%, transparent 30rem);
}
```

### Grid — selektiv, nicht überall

| Section | Grid |
|---------|------|
| Hero | ✅ |
| How-to | ❌ |
| Top 3 | ✅ |
| Dark Section | ❌ |
| Bonus | ❌ |
| Early Access | ✅ (sehr dezent, weiß auf dunkel) |

### Shadow-Regel

```
Normale Cards (step / prompt-card / bonus-card) → NUR warm-brown
Hero-Card & Early-Access-Card → Blue-Glow (= Featured-Signal)
```

### Hero Stage (Pflicht — macht den Premium-Look)

```css
.hero-stage {
  box-shadow: inset 0 1px rgba(255,255,255,0.90), 0 34px 100px -64px rgba(32,40,58,0.68);
  animation: hero-stage-rise 0.7s cubic-bezier(.16,1,.3,1) both;
}
```

+ `.hero-energy-field` (animierte Diagonallinien)
+ `.hero-scanline` (animierte orange Linie)
+ Alle 4 Keyframes: `hero-stage-rise`, `hero-energy-pan`, `hero-scanline-pass`, `hero-word-pop`

### Eyebrow-Stil

```css
.eyebrow {
  font-family: 'DM Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.32em;   /* sehr weit — Erkennungsmerkmal */
  color: rgba(204,120,92,0.76);   /* IMMER Claude-Orange (#CC785C) — kein Blau/Gold */
}
.eyebrow::before {
  background: linear-gradient(90deg, var(--blue), var(--blue) 52%, transparent);
}
/* auf dunklen Sektionen: identisch, nur minimal heller */
.eyebrow-dark { color: rgba(204,120,92,0.72); }
.eyebrow-dark::before { background: linear-gradient(90deg, var(--blue), var(--blue) 52%, transparent); }
```

### Section Title — tight

```css
.section-title {
  font-size: clamp(2rem, 6vw, 3.75rem);
  line-height: 0.96;
  letter-spacing: -0.035em;
}
```

### Instagram CTA Card (letzter Slot in Dark Section — immer!)

```html
<div class="dark-prompt-card" style="background: linear-gradient(135deg, rgba(204,120,92,0.10), rgba(204,120,92,0.04)); border-color: rgba(255,255,255,0.10); display:flex; flex-direction:column; justify-content:space-between; gap:24px;">
  <div>
    <div style="font-family:'DM Mono',monospace; font-size:10px; letter-spacing:0.28em; color:var(--blue); text-transform:uppercase; margin-bottom:16px;">Täglich neues KI-Wissen</div>
    <p style="font-family:'Cormorant Garamond',serif; font-size:clamp(22px,3vw,30px); font-weight:400; line-height:1.15; letter-spacing:-0.02em; color:#f0ece4;">
      Jeden Tag ein Tipp der dir wirklich Zeit spart.
    </p>
  </div>
  <div>
    <p style="font-size:13px; color:rgba(240,236,228,0.42); line-height:1.65; margin-bottom:20px;">
      Diese [X] Tipps sind der Anfang. Auf Instagram poste ich täglich neue — direkt anwendbar, kein Fluff.
    </p>
    <a href="https://www.instagram.com/[INSTAGRAM_OHNE_@]" target="_blank" rel="noopener"
       style="display:inline-flex; align-items:center; gap:10px; background:linear-gradient(90deg, #833ab4, #e1306c, #fd1d1d, #f77737, #fcaf45); color:#fff; font-family:'DM Sans',sans-serif; font-size:13px; font-weight:600; letter-spacing:0.02em; padding:11px 20px; border-radius:10px; text-decoration:none; box-shadow: 0 16px 34px -20px rgba(225,48,108,0.65);"
       onmouseover="this.style.opacity='0.88'; this.style.transform='translateY(-2px)'"
       onmouseout="this.style.opacity='1'; this.style.transform='translateY(0)'">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="0.5" fill="currentColor"/></svg>
      [INSTAGRAM] folgen
    </a>
  </div>
</div>
```

### Scroll Reveal

```js
(function() {
  const els = document.querySelectorAll('section:not(#hero), .step, .prompt-card, .bonus-card, .dark-prompt-card');
  const obs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.style.opacity='1'; e.target.style.transform='translateY(0)'; obs.unobserve(e.target); }
    });
  }, { threshold: 0.08 });
  els.forEach((el, i) => {
    el.style.cssText += `opacity:0; transform:translateY(28px); transition:opacity 0.7s cubic-bezier(.16,1,.3,1) ${i*0.04}s, transform 0.7s cubic-bezier(.16,1,.3,1) ${i*0.04}s;`;
    obs.observe(el);
  });
})();
```

### Early Access — Bühne mit Benefits + Trust (Pflicht — macht's „beitretens-wert")

Die linke Spalte der Early-Access-Sektion **NIE leer lassen** (nur Headline + 1 Satz wirkt schwach, nicht wie etwas wo man beitreten will). Immer:
- 3–4 **konkrete Benefits** mit **orangem Checkmark** — nur **WAHRE** Aussagen, keine erfundenen Zahlen (Wahrheitspflicht!)
- Eine **Trust-Reihe** unten: Kostenlos · Kein Spam · Jederzeit verlassen

```css
.early-benefits { list-style:none; margin:28px 0 0; display:flex; flex-direction:column; gap:13px; }
.early-benefits li { display:flex; align-items:flex-start; gap:12px; font-size:14.5px; color:rgba(240,236,228,0.82); line-height:1.5; }
.early-benefits li::before { content:'✓'; color:var(--blue); font-weight:700; font-size:13px; margin-top:1px; flex-shrink:0; }
.early-trust { display:flex; align-items:center; gap:10px; flex-wrap:wrap; margin-top:30px; padding-top:22px; border-top:1px solid rgba(255,255,255,0.08); font-family:'DM Mono',monospace; font-size:10px; letter-spacing:0.16em; text-transform:uppercase; color:rgba(240,236,228,0.42); }
.early-trust .trust-dot { opacity:0.4; }
```
```html
<ul class="early-benefits">
  <li>Täglich neue Prompts, Workflows &amp; KI-Tools — direkt anwendbar</li>
  <li>Direkter Draht zu uns: stell deine Fragen, bekomm echte Antworten</li>
  <li>Alle RealRise Guides &amp; Funnel-Pages komplett kostenlos</li>
  <li>Immer als Erstes informiert, wenn neue Inhalte &amp; Tools erscheinen</li>
</ul>
<div class="early-trust">
  <span>Kostenlos</span><span class="trust-dot">•</span>
  <span>Kein Spam</span><span class="trust-dot">•</span>
  <span>Jederzeit verlassen</span>
</div>
```

### Dunkle Sektionen & CTA — KONSEQUENT CLAUDE-ORANGE (kein Gold/Lila!)

⚠️ **Wichtigste Farb-Regel:** Claude-Orange (`--blue` = `#cc785c`) ist die **EINZIGE Akzentfarbe** — auf hell UND auf dunkel. **Kein Gold, kein Warm, kein Lila-Gradient.** Gemischte Akzente wirken „zusammengewürfelt / AI-gebastelt". Einzige Ausnahme: **Grün `#22A155`** nur für den live-Punkt + Trust-Häkchen (✓ Kostenlos etc.).
- **Eyebrow:** Claude-orange (`rgba(204,120,92,0.72)`) mit Gradient-Linie orange→orange
- **Headline-em:** **solid orange** via `background:var(--blue); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;` (oder schlicht `color:var(--blue)`) — KEIN blue→lila→warm-Gradient
- **Buttons auf Dunkel:** **solid orange** (`background:var(--blue); color:#fff`) — KEIN Gold
- **Glows:** orange radial-gradients (kein Gold/Braun)
- **Textur:** dezentes weißes Grid (radial-maskiert) + optionale **orange Haarlinie** oben

```css
/* Blue-Button auf Dunkel */
.btn-cta { background:var(--blue); color:#fff; font-weight:600; box-shadow:0 10px 30px -10px rgba(204,120,92,0.55); }
.btn-cta:hover { background:var(--blue-2); transform:translateY(-2px); box-shadow:0 16px 40px -10px rgba(204,120,92,0.65); }
/* Dunkles CTA-Banner: orange Glows + Grid + orange Hairline */
.cta-inner {
  background: var(--dark-2);
  background-image:
    radial-gradient(ellipse at 82% 0%, rgba(204,120,92,0.14) 0%, transparent 55%),
    radial-gradient(ellipse at 2% 100%, rgba(204,120,92,0.08) 0%, transparent 52%);
  border: 1px solid rgba(255,255,255,0.07);
}
.cta-inner::before { /* dezentes Grid, radial-maskiert */ }
.cta-inner::after  { /* 1px orange Haarlinie oben: linear-gradient(90deg, transparent, var(--blue), transparent) */ }
```

### Nummern-Badge (ÜBERALL identisch — Steps, Top-N, Dark-Section, Bonus)

Jede Nummerierung = **dasselbe Badge**. KEINE Text-Nummern, keine Suffixe wie „Top Hebel"/„Bonus" — nur die Zahl.

```css
/* hell (Steps, Top-N, Bonus) */
.num-badge { display:inline-flex; align-items:center; justify-content:center; width:40px; height:40px; border-radius:12px; background:var(--blue-pale); border:1px solid rgba(204,120,92,0.15); font-family:'DM Mono',monospace; font-size:12px; font-weight:500; color:var(--blue); margin-bottom:16px; flex-shrink:0; }
/* dunkel (Dark-Section) */
.num-badge--dark { background:rgba(204,120,92,0.16); border-color:rgba(204,120,92,0.26); color:#e0a890; }
```
HTML: `<div class="num-badge">01</div>` — nur die Zahl, nichts dahinter.

### Code-Box (ÜBERALL identisch)
Immer solid `#1a1714` (`var(--code-bg)`) — auch auf hellen Cards (Bonus). NIE halbtransparentes Schwarz (`rgba(0,0,0,0.38)`) auf hellem Grund → wird zu hässlichem Grau.

---

### 🔧 Farb-Korrektur (Alt-Seite auf Claude-Orange umfärben)

Falls eine bestehende Seite noch Gold/Warm/Lila-Akzente hat (alte Generation), diesen Befehl an Claude geben:

> Mach die Seite konsequent Claude-Orange. Ersetze ALLE Gold-/Warm-/Lila-Akzente durch Claude-Orange `#cc785c`:
> Eyebrows, Buttons (auch auf Dunkel = solid orange), Checkmarks, Glows/Radial-Gradients, Headline-Kursiv-Betonungen (`em`), Body-Blobs, Card-Hintergründe.
> Einzige Ausnahmen, die bleiben: Grün `#22A155` für live-Punkt + Trust-Häkchen, der warm-braune Card-Schatten, die Grid-Linie und der Instagram-Marken-Button (Instagrams eigene Farben).
> Kein Gold, kein `--warm` als Akzent, kein Lila-Gradient mehr.

---

## ✅ QUALITY CHECK VOR JEDER PAGE (Pflicht)

**Meta Pixel:**
- [ ] Pixel-Code im `<head>` vorhanden?
- [ ] ID `1343968131131688` korrekt?

**Lead-Formular (`.rr-form` — beide: Hero + Early Access):**
- [ ] `data-source="[NAME]"` korrekt (NICHT der eines anderen Affiliates!)?
- [ ] `data-placement` gesetzt (Hero = `hero`, Early Access = `early`)?
- [ ] Consent-Checkbox + Honeypot (`.rr-hp`) vorhanden?
- [ ] Webhook-URL exakt übernommen (Opt-in-Webhook)?
- [ ] Redirect-Ziel = absolute URL `https://ki.realrise-agency.com/vip` (NICHT `/vip` relativ)?
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
- [ ] Normale Cards: warm-brown shadow; Hero/Form-Cards: blue-glow?
- [ ] Instagram CTA Card ([INSTAGRAM]) als letzter Slot in Dark Section?
- [ ] Dunkle Sektionen/CTA: ORANGE Akzente + solid-oranger Button (KEIN Gold/Warm/Lila)?
- [ ] Early Access: Benefits-Liste (orange ✓) + Trust-Reihe (nicht nur 1 Satz)?
- [ ] **Nummern überall als IDENTISCHES Badge** (40×40px, radius 12, getönt, nur die Zahl) — KEINE Text-Nummern, keine Label-Suffixe wie „Top Hebel"/„Bonus"? (hell = blue-pale/blau · dunkel = blue-tint/#e0a890)
- [ ] Code-Boxen ÜBERALL solid `#1a1714` (kein halbtransparentes Grau auf hellen Cards)?
- [ ] Eyebrows einheitlich: Mono + orange Gradient-Linie (orange→orange, hell wie dunkel) — NIE warm/gold?
- [ ] KONSEQUENT CLAUDE-ORANGE: nirgends Gold/Warm/Lila als Akzent (nur Grün #22A155 für live-Punkt + Trust-Häkchen)?
- [ ] Scroll Reveal vorhanden?
- [ ] `@media (max-width: 900px)` Block vorhanden?

**Deploy:**
- [ ] Dateiname nur Kleinbuchstaben + Bindestriche, keine Umlaute/Leerzeichen?
- [ ] HTML flat im Root (kein Subordner)?
- [ ] `_redirects` hat neue Zeile für das Thema?
- [ ] `_redirects` hat `/[NAME]/* /:splat 302` ganz oben?
- [ ] ZIP aus **Live-Ordner** gebaut (nicht Staging)?
- [ ] **NACH Deploy: echter Test-Lead abgesendet + in GHL mit `aff:[NAME]` angekommen?** (Pflicht — fängt den Silent-Webhook-Fail)

**Bei ❌ → Fehler beheben → nochmal prüfen → dann liefern.**

---

## FUNNEL-PAGE STRUKTUR

**Fonts:** Cormorant Garamond · DM Mono · DM Sans (Google Fonts)

1. **NAV** — Fixed, glasmorphism, Links: „RealRise / [THEMA]", Rechts: „Top 3" · „Alle [X]" · „Bonus" · „Community"
2. **HERO** (Grid ✅) — hero-stage + energy-field + scanline, Links: H1 + Subtitle, Rechts: hero-card (blue-glow) + **Lead-Formular** (`.rr-form`, `data-source="[NAME]"`)
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
2. Webhook-URL mit Tippfehler → Leads kommen **still** NICHT an (kein sichtbarer Fehler!) → **immer Test-Lead nach Deploy**
3. Consent-Checkbox oder Honeypot (`.rr-hp`) vergessen → DSGVO-Risiko + Spam
4. `/[NAME]/*` fehlt in `_redirects` → 404
5. `?source=`/`data-source` falscher Affiliate → Leads falsch zugeordnet
6. ZIP aus Staging statt Live → alle anderen Pages gelöscht
7. Redirect `/vip` relativ statt absolut → Lead landet nach Anmeldung im 404 (VIP-Seite liegt auf Hub-Site!)
8. Dateiname mit Umlaut/Leerzeichen → URL kaputt → 404
9. Kein Test-Lead gemacht → Webhook-Fehler bleibt unbemerkt, Reel läuft, Leads gehen verloren

**Design:**
10. Plumpe Schatten `0 4px 24px rgba(...)` → billig wirken
11. Grid auf body → sichtbare Breaks zwischen Sections
12. Blue-shadow auf normalen Cards → Featured-Signal geht verloren
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
- Meta Pixel **`1343968131131688`** im `<head>`
- **Tonalität:** Premium, zugänglich, Du-Form

---

**STARTE wenn [INSTAGRAM] Hook + Caption + Reel-Inhalt schickt.** 🔥
