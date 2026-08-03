---
layout: default
title: "Home"
description: ""
---

<div style="display:flex;justify-content:center">
  <canvas id="canvas"></canvas>
</div>

# Home

{% include previews.html items=site.data.lists.main %}

<script src="https://nxrix.github.io/pixel-8/src/pixel8.js"></script>
<script>

const k = new Date("2021-09-26T10:37:00.000+03:30");
const px8 = new Pixel8(62,16);

canvas.style.imageRendering = "pixelated";
canvas.width = px8.w;
canvas.height = px8.h;
canvas.style.width = px8.w*3+"px";
canvas.style.height = px8.h*3+"px";
const ctx = canvas.getContext("2d");
const img = ctx.createImageData(px8.w,px8.h);
const img_data = img.data;

let t = 0;
const update = () => {
  px8.cls(32);
  const now = Date.now();
  const diff = new Date(now - k);
  const n = Math.floor(diff.getTime() / 1000);
  const str1 = Math.floor(n / (60 * 60 * 24)).toString();
  const str2 = [diff.getUTCHours(), diff.getUTCMinutes(), diff.getUTCSeconds()]
    .map((n) => n.toString().padStart(2, "0"))
    .join(":");
  const strl2 = str1.length + 1 / 2 + str2.length;
  const str2p = str1.length * 4 + 3;

  [
    [-1, -1],
    [0, -1],
    [1, -1],
    [-1, 0],
    [1, 0],
    [-1, 1],
    [0, 1],
    [1, 1]
  ].forEach(([x, y], i) => {
    px8.print(str1, px8.w2 - 2 * strl2 + x, px8.h2 - 2 + y, i < 3 ? 20 : 0);
    px8.print(
      str2,
      str2p + px8.w2 - 2 * strl2 + x,
      px8.h2 - 2 + y,
      i < 3 ? 20 : 0
    );
  });

  px8.print(str1, px8.w2 - 2 * strl2, px8.h2 - 2, 3);
  px8.print(str2, str2p + px8.w2 - 2 * strl2, px8.h2 - 2, 3);

  t++;

  for (let i = 0; i < px8.w*px8.h; i++) {
    const n = px8.buffer[i];
    const index = i * 4;
    if (n<32) {
      const c = Pixel8.palette[n];
      img_data[index    ] = c[0];
      img_data[index + 1] = c[1];
      img_data[index + 2] = c[2];
    }
    img_data[index + 3] = n===32?0:255;
  }
  ctx.putImageData(img,0,0);
  requestAnimationFrame(update);
};
update();

</script>
