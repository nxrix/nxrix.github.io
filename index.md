---
layout: default
title: "Home"
description: "My personal homepage"
---

<div style="display:flex;justify-content:center;margin-bottom:calc(16px + 1rem)">
  <h3 id="time"></h3>
</div>

# Home
<br>
{% include previews.html items=site.data.lists.main %}

<hr>
## Fractals
<br>
{% include previews.html items=site.data.lists.fractals %}

<hr>
## Contact
[![Telegram](https://img.shields.io/badge/-Telegram-26a5e4?style=flat&logo=telegram&logoColor=fff)](https://t.me/nxrix)
[![Gmail](https://img.shields.io/badge/-Gmail-ea4335?style=flat&logo=gmail&logoColor=fff)](mailto:nxrixz@gmail.com)
[![X](https://img.shields.io/badge/-X-000?style=flat&logo=x&logoColor=fff)](https://x.com/nxrixwastaken)

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
