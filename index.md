---
layout: default
title: "Home"
description: "My personal homepage"
---

<div style="display:flex;justify-content:center;margin-bottom:calc(16px + 1rem)">
  <h3 id="time"></h3>
</div>

# Home
<div style="max-width:90ch;padding:24px;font-size:13px;border-radius:8px;margin:16px 0;outline:1px solid var(--theme-foreground-faintest)">
  <img draggable="false" src="./assets/images/icons/skin-2.png" width="36" height="36" style="display:block;margin-left:-2px;margin-bottom:-50px;image-rendering:pixelated">
  <img draggable="false" src="./assets/images/icons/skin-1.png" width="32" height="32" style="float:left;border-radius:4px;margin:16px 16px 0 0;image-rendering:pixelated">
  <br>
  Hello! I'm nxrix. This is where I share things I make. I love beautiful and colorful things. I mostly work with JavaScript, C, Lua, and GLSL.
</div>
{% include previews.html items=site.data.lists.main %}

<hr>
## Fractals
{% include previews.html items=site.data.lists.fractals %}

<hr>
## Contact
<div>
  <a href="https://t.me/nxrix" style="text-decoration:none">
    <img src="https://img.shields.io/badge/-Telegram-26a5e4?style=flat&logo=telegram&logoColor=fff" alt="Telegram">
  </a>
  <a href="mailto:nxrixz@gmail.com" style="text-decoration:none">
    <img src="https://img.shields.io/badge/-Gmail-ea4335?style=flat&logo=gmail&logoColor=fff" alt="Gmail">
  </a>
  <a href="https://x.com/nxrixwastaken" style="text-decoration:none">
    <img src="https://img.shields.io/badge/-X-000?style=flat&logo=x&logoColor=fff" alt="X">
  </a>
</div>

<script>
const k = new Date("2021-09-26T10:37:00.000+03:30");
const update = () => {
  const d = new Date(Date.now() - k);
  const n = Math.floor(d.getTime() / 1000);
  const s1 = Math.floor(n / (60 * 60 * 24)).toString();
  const s2 = [d.getUTCHours(), d.getUTCMinutes(), d.getUTCSeconds()]
    .map((n) => n.toString().padStart(2, "0"))
    .join(":");
  time.innerText = s1+" "+s2;
  requestAnimationFrame(update);
};
update();
</script>
