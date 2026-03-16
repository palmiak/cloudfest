---
theme: default
title: Why we switched to Astro
info: CloudFest 2026 presentation about switching to Astro
aspectRatio: 16/9
canvasWidth: 980
fonts:
  sans: 'Outfit'
  serif: 'Outfit'
  weights: '400,500,600,700'
  provider: google
highlighter: shiki
transition: fade
css: unocss
drawings:
  persist: false
layout: cover
---

<style src="./styles/index.css"></style>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&display=swap');

.terminal-slide {
  font-family: 'Space Mono', monospace;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  padding: 0 clamp(24px, 8%, 90px);
  position: relative;
  z-index: 1;
}

@keyframes logo-float {
  0%, 100% {
    transform: translateY(-50%) rotate(-15deg) translateX(0);
  }
  50% {
    transform: translateY(-50%) rotate(-15deg) translateX(-4px);
  }
}

.astro-logo-bg {
  position: absolute;
  right: -25%;
  top: 50%;
  transform: translateY(-50%) rotate(-15deg);
  width: 35vw;
  height: 35vw;
  background-image: url('https://astro.build/assets/press/astro-icon-light.svg');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  opacity: 0.04;
  z-index: 0;
  pointer-events: none;
  animation: logo-float 4500ms ease-in-out infinite;
}

.scanline-overlay {
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0, 0, 0, 0.06) 2px,
    rgba(0, 0, 0, 0.06) 4px
  );
  pointer-events: none;
  z-index: 3;
  opacity: 0.5;
}

.prompt {
  font-size: clamp(10px, 1.2vw, 14px);
  color: var(--color-green);
  margin-bottom: clamp(16px, 2.5vw, 30px);
  opacity: 0.8;
  font-weight: 400;
}

.terminal-title {
  font-size: clamp(18px, 3.2vw, 40px);
  line-height: 1.5;
  font-weight: 400;
  letter-spacing: -0.01em;
}

.terminal-comment {
  color: rgba(255, 255, 255, 0.2);
}

.terminal-text {
  color: var(--color-text-primary);
}

.terminal-highlight {
  color: var(--color-green);
  font-weight: 400;
}

.terminal-cursor {
  display: inline-block;
  width: 0.55em;
  height: 1.05em;
  background: var(--color-green);
  vertical-align: text-bottom;
  animation: terminal-blink 1000ms step-end infinite;
  margin-left: 2px;
}

@keyframes terminal-blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.terminal-meta {
  margin-top: clamp(24px, 3.5vw, 40px);
  font-size: clamp(8px, 1vw, 12px);
  color: rgba(255, 255, 255, 0.25);
  font-weight: 400;
}
</style>

<div class="scanline-overlay"></div>
<div class="astro-logo-bg"></div>

<div class="terminal-slide">
  <div class="prompt">$ ./present --topic="astro-migration" --audience="cloudfest-2026"</div>

  <div class="terminal-title">
    <span class="terminal-comment"># </span><span class="terminal-text">Why we switched to Astro</span><br>
    <span class="terminal-comment"># </span><span class="terminal-text">and why </span><span class="terminal-highlight">most_of_you</span><span class="terminal-text"> won't</span><span class="terminal-cursor"></span>
  </div>
</div>

<!--
  SLIDE 02 — ABOUT ME
-->

---
layout: full-width
accentColor: green
---

<div style="display: flex; align-items: center; width: 100%;">
  <PhotoFrame src="/mypicture.jpg" alt="Maciek Palmowski" />

  <div style="flex: 1; display: flex; flex-direction: column; gap: clamp(14px, 2.2vw, 26px);">
<div>
<div style="font-family: 'Outfit', sans-serif; font-size: clamp(22px, 4vw, 48px); font-weight: 700; color: #F0F0EC; line-height: 1.05;">Maciek Palmowski</div>
<div style="font-size: clamp(9px, 1.05vw, 12px); color: rgba(255,255,255,0.25); font-family: 'Outfit', sans-serif; margin-top: 4px;">it's "Mat-sek" — yes, really</div>
</div>

<PointsList
:points="[
{ text: 'Growth Manager at <span style=`color:#afe614;`>Patchstack</span>' },
{ text: '20+ years building things in WordPress' },
{ text: 'Now also building things <span class=`em-green`>away</span> from WordPress' }
]"
defaultColor="green"
/>

<div style="font-size: clamp(9px, 1.05vw, 12px); color: rgba(255,255,255,0.35); font-weight: 300;">
gravel cyclist · specialty coffee obsessive · Polish, based in Łódź
</div>
  </div>
</div>

<!--
  SLIDE 03 — CONTEXT / NOT A VENDOR
-->

---
layout: two-column
accentColor: green
label: Context
---

::left::

# Not a vendor<br>A developer who<br><span class="em-green">actually switched</span>

::right::

<div style="display: flex; flex-direction: column; gap: clamp(12px, 2vw, 24px);">
  <SiteCard
    v-click
    iconType="active"
    url="maciekpalmowski.dev"
    description="Personal blog & portfolio · migrated from WordPress"
    tag="Astro · SSG"
    tagType="green"
  />

  <SiteCard
    v-click
    iconType="active"
    url="patchstack.com"
    description="Marketing site · Astro frontend + headless WordPress for blog"
    tag="Astro · Headless WP"
    tagType="green"
  />

  <SiteCard
    v-click
    iconType="muted"
    url="20+ years with WordPress"
    description="developer · community organizer · WP entusiast"
    tag="Not a hater"
    tagType="muted"
    :urlMuted="true"
  />
</div>

<!--
  SLIDE 04 — THE SPECTRUM
-->

---
layout: full-width
accentColor: green
---

<div class="slide-label label-green" style="margin-bottom: clamp(10px, 2vw, 20px);">The landscape</div>

# One is a <span class="em-green">complete platform</span><br>One is a framework you assemble

<div style="margin-top: clamp(20px, 4vw, 44px);">
  <SpectrumVisualization
    leftPlayer="WordPress"
    leftPlayerSub="Platform"
    rightPlayer="Astro"
    rightPlayerSub="SSG / Framework"
    :leftPoints="[
      { text: 'Everything included', color: '#4A90D9' },
      { text: 'Click to install', color: '#4A90D9' },
      { text: 'DB + runtime required', color: '#4A90D9' },
      { text: 'Non-technical editors', color: '#4A90D9' }
    ]"
    :rightPoints="[
      { text: 'You assemble it', color: '#afe614' },
      { text: 'Every feature is a choice', color: '#afe614' },
      { text: 'Just files — or connect any data source', color: '#afe614' },
      { text: 'Developer-first', color: '#afe614' }
    ]"
    allVisible
  />
</div>

<!--
  SLIDE 05 — WHY ASTRO BRIDGE
-->

---
layout: full-width
accentColor: green
---

<div class="slide-label label-green" style="margin-bottom: clamp(10px, 2vw, 20px);">Why Astro?</div>

# Not just fast<br><span class="em-green">Fast by default</span>

<div style="margin-top: clamp(24px, 4vw, 44px); max-width: 70%; font-size: clamp(11px, 1.3vw, 16px); color: rgba(255,255,255,0.5); font-weight: 300; line-height: 1.5;">
Astro doesn't just let you build fast sites — it makes bad performance architecturally difficult. Static-first, zero JS by default, and built for content. Here's what that means in practice.
</div>

<!--
  SLIDE 06 — PERFORMANCE
-->

---
layout: two-column
accentColor: green
label: Performance
---

::left::

# Not configured<br><span class="em-green">Structural</span>

::right::

<PointsList
  :points="[
    { text: 'With WordPress, you fight for performance' },
    { text: 'Static HTML is the default output' },
    { text: 'Zero JS shipped unless you add it' }
  ]"
  defaultColor="green"
/>

<!--
  SLIDE 06 — SECURITY
-->

---
layout: two-column
accentColor: green
label: Security
---

::left::

# The attack surface<br><span class="em-green">almost disappears</span>

::right::

<PointsList
  :points="[
    { text: 'No PHP runtime, no wp-admin, no plugin CVEs' },
    { text: 'Nothing to inject into' }
  ]"
  defaultColor="green"
/>

<StatBox value="91%" label="of WordPress vulnerabilities come from plugins & themes — not core" />

<!--
  SLIDE 07 — SCALABILITY
-->

---
layout: two-column
accentColor: green
label: Scalability
---

::left::

# Starts simple<br><span class="em-green">Grows with you</span>

::right::

<PointsList
  :points="[
    { text: 'Start with local markdown files' },
    { text: 'Connect any headless CMS or data source when ready' },
    { text: 'IKEA and Cloudflare use Astro' }
  ]"
  defaultColor="green"
/>

<!--
  SLIDE 08 — PORTABILITY
-->

---
layout: two-column
accentColor: green
label: Portability
---

::left::

# You own<br><span class="em-green">the files</span>

::right::

<PointsList
  :points="[
    { text: 'Move hosts by moving a folder' },
    { text: 'Dynamic Astro = just a Node process' }
  ]"
  defaultColor="green"
/>

<div class="code-block">
  <span class="code-dim">$ </span><span class="code-green">npm run build</span><br>
  <span class="code-dim">$ </span><span class="code-green">rsync -av ./dist/ user@server:/var/www/</span><br>
  <span class="code-dim"># That's the entire deployment.</span>
</div>

<!--
  SLIDE 09 — AI / FUTURE
-->

---
layout: two-column
accentColor: green
label: The future of maintenance
---

::left::

# Your next developer<br><span class="em-green">might not be human</span>

::right::

<PointsList
  :points="[
    { text: 'Asking an LLM to help with WordPress means explaining your schema, your plugins, your hooks' },
    { text: 'With Astro, I just open the file' },
    { text: 'WordPress is investing heavily in AI tooling — credit where it\'s due — but right now, the file-based model just works' }
  ]"
  defaultColor="green"
/>

<!--
  SLIDE 10 — CONTENT EDITOR PROBLEM
-->

---
layout: two-column
accentColor: amber
label: The honest part
---

::left::

# Your client<br>edits the content<br><span class="em-amber">Not you</span>

::right::

<PointsList
  :points="[
    { text: 'They won\'t edit markdown files in VS Code' },
    { text: 'They won\'t know how to connect a headless CMS' },
    { text: 'Gutenberg just works for them — and that matters' }
  ]"
  defaultColor="amber"
/>

<!--
  SLIDE 11 — EVERYTHING IS AN INTEGRATION
-->

---
layout: two-column
accentColor: amber
label: The honest part
---

::left::

# Everything is<br><span class="em-amber">an integration</span>

::right::

<PointsList
  :points="[
    { text: 'Contact form, cookie banner, search — all require research and work' },
    { text: 'WordPress has a plugin for everything' },
    { text: 'Astro is a framework, not a platform — you assemble it' }
  ]"
  defaultColor="amber"
/>

<!--
  SLIDE 12 — THERE IS A CEILING
-->

---
layout: two-column
accentColor: amber
label: The honest part
---

::left::

# There is<br><span class="em-amber">a ceiling</span>

::right::

<PointsList
  :points="[
    { text: 'Great for content sites and marketing pages' },
    { text: 'Complex user state, auth, real-time data — you\'ll fight it' },
    { text: 'Know what your project will become, not just what it is today' }
  ]"
  defaultColor="amber"
/>

<!--
  SLIDE 13 — THE START COSTS MORE
-->

---
layout: two-column
accentColor: amber
label: The honest part
---

::left::

# The start<br><span class="em-amber">costs more</span>

::right::

<PointsList
  :points="[
    { text: 'WordPress: 5-minute install, working site' },
    { text: 'Astro: higher initial investment — in time and decisions' },
    { text: 'Running cost is lower, but the start is steeper' }
  ]"
  defaultColor="amber"
/>

<!--
  SLIDE 14 — WHY WE LEFT WORDPRESS
-->

---
layout: two-column
accentColor: red
label: Why we left WordPress
---

::left::

# Five years of<br><span class="em-red">death by a thousand cuts</span>

::right::

<PointsList
  :points="[
    { text: 'Maintenance that never really ended' },
    { text: 'Updates that broke things for no obvious reason' },
    { text: 'Sometimes, it just… stopped working' }
  ]"
  defaultColor="red"
/>

<!--
  SLIDE 15 — WHY WE WENT FOR IT
-->

---
layout: two-column
accentColor: green
label: Why we went for it
---

::left::

# We stopped<br>fighting and<br><span class="em-green">just shipped</span>

::right::

<PointsList
  :points="[
    { text: 'Docs and Academy were already on Astro — and just worked' },
    { text: 'We were tired of fighting the CMS' },
    { text: 'We can keep a lightweight WP just for blog management' }
  ]"
  defaultColor="green"
/>

<!--
  SLIDE 16 — WHO EDITS THE CONTENT?
-->

---
layout: two-column
accentColor: green
label: Before you decide
---

::left::

# Who edits<br>the content?<br><span class="em-green">That's your answer</span>

::right::

<PointsList
  :points="[
    { text: '🧑‍💻 <strong>You or a developer</strong> → MDX files, Git-based CMS (Decap, Tina) — full control, zero overhead' },
    { text: '✍️ <strong>Technical editor</strong> → Headless WP, Sanity, Keystatic — familiar UI, Astro frontend' },
    { text: '👩‍💼 <strong>Non-technical client</strong> → Headless WP with Gutenberg, or… just keep WordPress' }
  ]"
  defaultColor="green"
/>

<!--
  SLIDE 17 — THE CHECKLIST
-->

---
layout: two-column
accentColor: green
label: Should you switch?
---

::left::

# Check all five<br><span class="em-green">Then decide</span>

::right::

<ChecklistItems
  :items="[
    { text: 'Your content is mostly text and media' },
    { text: 'Content editing is solved — Git-based, or headless CMS. Not an afterthought.', note: 'not out of the box' },
    { text: 'No need for complex real-time user interactions' },
    { text: 'Security and performance are a priority' },
    { text: 'Budget for setup, not ongoing maintenance' }
  ]"
/>

<!--
  SLIDE 18 — VERDICT
-->

---
layout: cover
---

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&display=swap');

.slidev-layout {
  display: flex !important;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0 14% !important;
}

.accent-bar {
  position: fixed;
  left: 0 !important;
  top: 18%;
  bottom: 18%;
  width: 3px;
  background: var(--color-green);
  border-radius: 0 2px 2px 0;
  z-index: 10;
  margin: 0 !important;
}

.rule-top {
  position: fixed;
  top: 11%;
  left: 9%;
  right: 9%;
  height: 1px;
  background: rgba(255, 255, 255, 0.1);
  z-index: 10;
}

.rule-bottom {
  position: fixed;
  bottom: 11%;
  left: 9%;
  right: 9%;
  height: 1px;
  background: rgba(255, 255, 255, 0.1);
  z-index: 10;
}

.corner-dot {
  position: fixed;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: var(--color-green);
  opacity: 0.6;
  z-index: 10;
}

.dot-tr {
  top: 11%;
  right: 9%;
  transform: translate(50%, -50%);
}

.dot-bl {
  bottom: 11%;
  left: 9%;
  transform: translate(-50%, 50%);
}

.slide-label-center {
  font-size: clamp(8px, 0.95vw, 11px);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-green);
  font-weight: 400;
  margin-bottom: clamp(14px, 2.5vw, 28px);
  font-family: 'Outfit', sans-serif !important;
}

.claim-text {
  font-family: 'Outfit', sans-serif !important;
  font-size: clamp(32px, 6vw, 72px) !important;
  font-weight: 700 !important;
  line-height: 1.1 !important;
  color: var(--color-text-primary) !important;
  letter-spacing: -0.02em !important;
}

.claim-text em {
  font-style: normal !important;
  color: var(--color-green) !important;
  font-family: 'Outfit', sans-serif !important;
  font-weight: 700 !important;
}

.contact-info-centered {
  margin-top: clamp(32px, 4vw, 48px);
  font-size: clamp(10px, 1.2vw, 14px);
  color: rgba(255, 255, 255, 0.35);
  font-family: 'Outfit', sans-serif !important;
  line-height: 1.6;
}

.contact-name {
  font-weight: 500;
  color: rgba(255, 255, 255, 0.5);
}
</style>

<div class="accent-bar"></div>
<div class="rule-top"></div>
<div class="rule-bottom"></div>
<div class="corner-dot dot-tr"></div>
<div class="corner-dot dot-bl"></div>

<div class="slide-label-center">Our verdict</div>
<div class="claim-text">
  We'd do it<br><em>again</em>
</div>

<!--
  SLIDE 19 — Q&A
-->

---
layout: cover
---

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&display=swap');

.slidev-layout {
  display: flex !important;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0 14% !important;
}

.accent-bar {
  position: fixed;
  left: 0 !important;
  top: 18%;
  bottom: 18%;
  width: 3px;
  background: var(--color-green);
  border-radius: 0 2px 2px 0;
  z-index: 10;
  margin: 0 !important;
}

.rule-top {
  position: fixed;
  top: 11%;
  left: 9%;
  right: 9%;
  height: 1px;
  background: rgba(255, 255, 255, 0.1);
  z-index: 10;
}

.rule-bottom {
  position: fixed;
  bottom: 11%;
  left: 9%;
  right: 9%;
  height: 1px;
  background: rgba(255, 255, 255, 0.1);
  z-index: 10;
}

.corner-dot {
  position: fixed;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: var(--color-green);
  opacity: 0.6;
  z-index: 10;
}

.dot-tr {
  top: 11%;
  right: 9%;
  transform: translate(50%, -50%);
}

.dot-bl {
  bottom: 11%;
  left: 9%;
  transform: translate(-50%, 50%);
}

.slide-label-center {
  font-size: clamp(8px, 0.95vw, 11px);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-green);
  font-weight: 400;
  margin-bottom: clamp(14px, 2.5vw, 28px);
  font-family: 'Outfit', sans-serif !important;
}

.claim-text {
  font-family: 'Outfit', sans-serif !important;
  font-size: clamp(32px, 6vw, 72px) !important;
  font-weight: 700 !important;
  line-height: 1.1 !important;
  color: var(--color-text-primary) !important;
  letter-spacing: -0.02em !important;
}

.claim-text em {
  font-style: normal !important;
  color: var(--color-green) !important;
  font-family: 'Outfit', sans-serif !important;
  font-weight: 700 !important;
}
</style>

<div class="accent-bar"></div>
<div class="rule-top"></div>
<div class="rule-bottom"></div>
<div class="corner-dot dot-tr"></div>
<div class="corner-dot dot-bl"></div>

<div class="slide-label-center">Time for questions</div>
<div class="claim-text">
  What questions<br>do <em>you</em> have?
</div>