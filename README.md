# Orbittype

<img width="100" height="100" alt="orbit" src="https://github.com/user-attachments/assets/b1f10b67-0d2b-4ec0-90f1-2083ec49f033" />

**A free, minimal circular text generator — type it, shape it, orbit it.**

Orbittype turns any word or sentence into rotating text arranged in a perfect ring, with a live preview and a copy-ready **HTML + CSS + jQuery** snippet you can drop straight into your own project. No build tools, no frameworks, no sign-up.

🔗 **Live demo:** [samanway-koley.github.io/orbittype](https://samanway-koley.github.io/orbittype/)

<img width="2639" height="1685" alt="orbittype-ss" src="https://github.com/user-attachments/assets/feb9b4e9-20d3-4f85-8b04-f656f8f6b8e5" />

---

## ✨ Features

- **🔄 Rotating circular text** — any text you type is laid out along a ring and animated with a smooth CSS keyframe rotation.
- **♾️ No character limit** — short text automatically repeats to fill the circle; longer text wraps around exactly once.
- **🔡 Text case control** — switch between `ABC` (uppercase), `abc` (lowercase), and `Abc` (title case) with one click.
- **📐 Fully adjustable geometry** — control width, height, font size, letter spacing, and rotation speed with live sliders and numeric inputs.
- **⭕ True ellipse mode** — toggle between a perfect circle and a true ellipse layout.
- **⏯️ Playback controls** — pause, resume, and reverse the rotation direction at any time.
- **📋 Copy-ready code export** — instantly generates a minimal, framework-free `HTML + CSS + jQuery` snippet reflecting your exact settings, ready to paste anywhere.
- **⚡ Zero dependencies to build** — runs entirely client-side in the browser; the only runtime dependency in the exported snippet is the jQuery CDN.

---

## 🧭 How it works

1. **Type your text** into the input box (no character limit).
2. **Choose a text case** — UPPERCASE, lowercase, or Title Case.
3. **Tune the ring** — drag the Width, Height, Font Size, Letter Spacing, and Rotation Speed sliders until it looks right.
4. **Preview live** — the ring rotates in real time as you adjust settings.
5. **Copy the snippet** — click **Copy code** to grab the generated HTML/CSS/jQuery and paste it into your own site, logo, badge, stamp, or button.

Under the hood, each character is measured and placed on the circle using basic trigonometry (`Math.cos` / `Math.sin`), with the circle's circumference computed via an ellipse-perimeter approximation (Ramanujan's formula) so that letter spacing stays visually consistent regardless of ring size.

---

## 🛠️ Tech stack

| Layer         | Technology                     |
|---------------|---------------------------------|
| Structure     | HTML5                           |
| Styling       | CSS3 (custom properties, `@keyframes` animation) |
| Interactivity | JavaScript + jQuery 3.7.1        |
| Hosting       | GitHub Pages                     |

No bundlers, no package manager, and no backend — everything runs in a single static page.

---

## 🚀 Getting started

### Use it online
Just visit the live demo — no installation needed:
👉 [samanway-koley.github.io/orbittype](https://samanway-koley.github.io/orbittype/)

### Run it locally
```bash
git clone https://github.com/samanway-koley/orbittype.git
cd orbittype
```
Then simply open `index.html` in your browser — no server or build step required.

---

## 📋 Example output snippet

Here's a simplified example of the kind of code Orbittype generates for you:

```html
<div class="rotate-text">SET YOUR TEXT IN ORBIT.</div>

<style>
.rotate-text {
    position: relative;
    width: 500px;
    height: 500px;
    margin: auto;
    font-size: 50px;
    letter-spacing: 7px;
    animation: rotateText 22s linear infinite;
}
.rotate-text span {
    position: absolute;
    font-weight: 900;
}
@keyframes rotateText {
    to { transform: rotate(360deg); }
}
</style>

<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
<script>
$(function () {
    var $r = $(".rotate-text"), t = $r.text();
    var w = $r.width(), h = $r.height();
    var font = parseFloat($r.css("font-size")) || 16;
    var spacing = parseFloat($r.css("letter-spacing")) || 0;
    var rx = w * 0.44, ry = h * 0.44;
    var circ = Math.PI * (3 * (rx + ry) - Math.sqrt((3 * rx + ry) * (rx + 3 * ry)));
    var step = font * 1.3 + spacing * 2;
    var n = Math.max(t.length, Math.min(400, Math.max(6, Math.round(circ / step))));
    while (t.length < n) t += t;
    t = t.slice(0, n);
    $r.empty();
    $.each(t.split(""), function (i, ch) {
        var a = (i * 360 / n - 90) * Math.PI / 180;
        $("<span>").text(ch).css({
            left: w / 2 + rx * Math.cos(a) + "px",
            top: h / 2 + ry * Math.sin(a) + "px",
            transform: "translate(-50%, -50%) rotate(" + (a * 180 / Math.PI + 90) + "deg)"
        }).appendTo($r);
    });
});
</script>
```

> 💡 If your page already loads jQuery, you can safely remove the CDN `<script>` line.

---

## 🎯 Use cases

- Logos and brand marks
- Circular badges and stamps
- Seals, emblems, and rotating buttons
- Favicon and hero-banner animations
- Fun UI flourishes for portfolios and landing pages

---

## 🗺️ Roadmap / ideas

- [ ] Export as animated SVG / GIF
- [ ] Custom color and gradient controls
- [ ] Multiple concentric rings
- [ ] Preset templates (badge, seal, logo, loader)

Have an idea? Feel free to open an issue or a pull request.

---

## 🤝 Contributing

Contributions, bug reports, and feature suggestions are welcome!

1. Fork the repo
2. Create a branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is open source. Feel free to use, modify, and distribute it — a credit/link back to the project is appreciated but not required. *(Add a `LICENSE` file, e.g. MIT, to make this explicit.)*

---

## 👤 Author

**Developed by [Samanway Koley](https://github.com/samanway-koley)**

© 2026 Orbittype. All rights reserved.
