---
name: google-adsense
description: Reference for generating and modifying Google AdSense display ad code based on official documentation.
version: 1.0.0
license: MIT
---

# Google AdSense Display Ad Units — SKILL

> Reference for LLM agents generating/modifying AdSense display ad code.
> Source: 6 Google AdSense official docs (2026-04).

---

## 1. Create a Display Ad Unit

Console path: **Ads → By ad unit → Display ads**

1. Enter a unique descriptive name
2. Select ad size: **Responsive** (default, recommended) or **Fixed**
3. **Save and get code** → copy snippet
4. Paste inside `<body>` tags

---

## 2. Responsive Ads — Default Behavior

- Auto-sizes based on parent container width
- Reloads ad on device rotation (caches original ad for return to prior orientation)
- Auto-expands to full screen width on mobile portrait (improves revenue)

### When Responsive Fails (manual CSS media query required)

| Situation | Cause |
|---|---|
| Third-party JS executes before ad code | Cannot calculate size |
| Parent container has no explicit width (e.g. float) | Cannot calculate size |
| Parent container has fixed/limited height | Clipped on some devices |

---

## 3. Responsive Tag Parameters

### `data-ad-format`

| Value | Effect |
|---|---|
| `"auto"` | Default. Auto size |
| `"rectangle"` | Rectangle shape |
| `"vertical"` | Vertical shape |
| `"horizontal"` | Horizontal shape |
| Combo | `"rectangle, horizontal"` comma-separated |

> Shape applies to desktop only.

### `data-full-width-responsive`

| Value | Behavior |
|---|---|
| `"true"` | Max full-width expansion on mobile (recommended) |
| `"false"` | Disable full-width expansion (may reduce revenue) |
| Absent | Occasional full-width expansion |

---

## 4. Modify Responsive Code (CSS Media Query)

When modifying, **delete** both `data-ad-format="auto"` and `data-full-width-responsive="true"`.

### 4-1. Fixed Size Per Screen Width

```html
<style>
.adslot_1 { width: 320px; height: 100px; }
@media (min-width: 500px) { .adslot_1 { width: 468px; height: 60px; } }
@media (min-width: 800px) { .adslot_1 { width: 728px; height: 90px; } }
</style>
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>
<ins class="adsbygoogle adslot_1"
     style="display:block"
     data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
     data-ad-slot="XXXXXXXXXX"></ins>
<script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
```

Rules:
- Class name: letters, digits, underscores only; must start with a letter
- No duplicate class names on same page
- External stylesheet sizing is not officially supported

### 4-2. Expandable Width + Fixed Height

```html
<ins class="adsbygoogle"
     style="display:block;min-width:400px;max-width:970px;width:100%;height:90px"
     data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
     data-ad-slot="XXXXXXXXXX"></ins>
```

### 4-3. Hide Ad for Specific Screen Sizes

```html
<style>
.adslot_1 { display:block; width: 320px; height: 50px; }
@media (max-width: 400px) { .adslot_1 { display: none; } }
@media (min-width: 500px) { .adslot_1 { width: 468px; height: 60px; } }
@media (min-width: 800px) { .adslot_1 { width: 728px; height: 90px; } }
</style>
```

`display: none` prevents the ad request entirely.

---

## 5. Fixed-Sized Ad Constraints

| Rule | Value |
|---|---|
| Only one dimension may exceed 450px | e.g. 728×90 ✅, 500×500 ❌ |
| Min width | 120px |
| Min height | 50px |
| Max per dimension | 1200px |

- Smaller inventory pool than responsive → potential revenue decrease
- No auto-adaptation to rotation/layout changes
- Non-standard sizes (e.g. 120×60) may have near-zero inventory

---

## 6. Synchronous Ad Code

Only for **fixed-sized** ads. Not available for responsive.

```html
<script type="text/javascript">
    google_ad_client = "ca-pub-XXXXXXXXXXXXXXXX";
    google_ad_slot = "XXXXXXXXXX";
    google_ad_width = 728;
    google_ad_height = 90;
</script>
<script type="text/javascript"
  src="https://pagead2.googlesyndication.com/pagead/show_ads.js">
</script>
```

- Do NOT mix async and sync code on the same page
- Use only when ad server (e.g. Google Ad Manager) requires sync

---

## 7. Default Template — Async Responsive

```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
     data-ad-slot="XXXXXXXXXX"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
```

---

## 8. Decision Flow

```
Ad insertion request
  ├─ Responsive site? → YES → Async responsive (§7)
  │   ├─ Need specific shape? → change data-ad-format (§3)
  │   ├─ Need per-screen sizing? → CSS media query (§4)
  │   └─ Disable mobile full-width? → data-full-width-responsive="false"
  └─ Fixed layout? → YES → Fixed code
      ├─ Validate size constraints (§5)
      └─ Need sync code? → §6
```

---

## 9. Validation Checklist

- [ ] `ca-pub-` publisher ID and `data-ad-slot` replaced with real values
- [ ] CSS media query mods: `data-ad-format` and `data-full-width-responsive` lines removed
- [ ] Fixed size: at most one dimension > 450px
- [ ] No async/sync code mixed on same page
- [ ] Parent container has explicit width (responsive)
- [ ] Parent container has no fixed height constraint (responsive)
