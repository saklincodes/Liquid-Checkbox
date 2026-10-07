# 💧 Liquid Checkbox

A modern, highly satisfying, interactive **Liquid Gooey Checkbox** component crafted with pure CSS animations, SVG metaball filters, and real-time procedural Web Audio sound synthesis.

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![SVG Filters](https://img.shields.io/badge/SVG-Gooey%20Filters-FFB13B?style=for-the-badge&logo=svg&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/SVG)
[![Web Audio API](https://img.shields.io/badge/Web%20Audio-Procedural%20FX-00C49F?style=for-the-badge)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen?style=for-the-badge)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE.txt)

---

## ✨ Features

- 🫧 **Fluid SVG Gooey Effect:** Employs SVG `<filter>` with `feGaussianBlur` and `feColorMatrix` for realistic liquid metaball blending.
- 💥 **Explosive Particle Splash:** Dynamic 6-point droplet dispersion created with pure CSS `@keyframes` and multi-stop `box-shadow`.
- 🔊 **Zero-Latency Sound FX:** Procedural audio synthesis powered by the **Web Audio API** (no external `.mp3`/`.wav` files needed, works 100% offline).
- ⚡ **GPU Accelerated:** Smooth 60FPS rendering using hardware-accelerated CSS transforms.
- 🎨 **Fully Customizable:** Easily customize theme colors, scale, timings, and droplet spread.
- 📦 **Zero External Dependencies:** Built with vanilla HTML, CSS, and modern browser APIs.

---

## 📁 Project Structure

```text
liquid-checkbox/
├── dist/
│   ├── index.html       # Production-ready HTML with Web Audio synthesizer
│   └── style.css        # Compiled CSS with centered layout and keyframes
├── src/
│   ├── index.pug        # Source template (Pug)
│   └── style.stylus     # Source styles (Stylus)
├── LICENSE.txt          # MIT License
└── README.md            # Documentation
```

---

## 🛠️ How It Works (Technical Breakdown)

### 1. SVG Gooey / Metaball Filter
The liquid cohesion effect is achieved by applying an SVG filter to the animated element:
```html
<svg class="goo-filter" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <filter id="goo">
      <!-- 1. Blur the graphic to blend overlapping shapes -->
      <feGaussianBlur in="SourceGraphic" stdDeviation="4" result="blur" />
      <!-- 2. Sharpen the alpha channel to create a crisp liquid boundary -->
      <feColorMatrix in="blur" mode="matrix" 
        values="1 0 0 0 0  
                0 1 0 0 0  
                0 0 1 0 0  
                0 0 0 22 -7" result="goo" />
      <feBlend in="SourceGraphic" in2="goo" />
    </filter>
  </defs>
</svg>
```

### 2. Multi-Point Particle Splash
When `:checked`, CSS keyframes animate multi-directional `box-shadow` coordinates while expanding outward:
```css
@keyframes splash {
  0% {
    transform: scale(1.1);
  }
  40% {
    transform: scale(1);
    background: #4c95f7;
    box-shadow: 0 -18px 0 -8px #4c95f7, 16px -8px 0 -8px #4c95f7, 16px 8px 0 -8px #4c95f7,
                0 18px 0 -8px #4c95f7, -16px 8px 0 -8px #4c95f7, -16px -8px 0 -8px #4c95f7;
  }
  100% {
    background: #4c95f7;
    box-shadow: 0 -32px 0 -10px transparent, 28px -16px 0 -10px transparent, 28px 16px 0 -10px transparent,
                0 32px 0 -10px transparent, -28px 16px 0 -10px transparent, -28px -16px 0 -10px transparent;
  }
}
```

### 3. Procedural Audio Synthesis
Sound is generated in real-time on every state change using oscillators and gain envelopes:
```javascript
// Dual-layer bubble splash synthesis
const osc = audioCtx.createOscillator();
osc.frequency.setValueAtTime(260, audioCtx.currentTime);
osc.frequency.exponentialRampToValueAtTime(820, audioCtx.currentTime + 0.09);
```

---

## 🚀 Quick Start

1. Clone or download the repository.
2. Open `dist/index.html` directly in any modern browser.
3. Click the checkbox to enjoy the liquid animation and bubble pop sound!

---

## 🎨 Customization

### Change Primary Color
In `dist/style.css` (or `$primary` variable in `src/style.stylus`), replace `#4c95f7` with your brand color:
```css
/* Example: Neon Purple */
:root {
  --primary-color: #8b5cf6;
}
```

### Adjust Size / Scale
To scale the component, adjust the `transform: scale(...)` property on `.cbx` in `dist/style.css`:
```css
.cbx {
  transform: scale(1); /* Default size (24px) */
  /* transform: scale(8.5); -> Large size for demo/recordings */
}
```

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
Created with passion & precision. Feel free to use and customize it in your own projects! 🚀
