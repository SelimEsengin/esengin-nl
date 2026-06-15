# Esengin Family Site — Developer Notes

## Photo circles (images inside family group circles)

When adding a person image to any family group, always use a **`photo-circle`** div instead of a plain `circle` div, and keep the correct gender/role class alongside it.

### Correct pattern
```html
<div class="photo-circle female" style="width:200px;height:200px;">
  <img src="images/female.png" alt="Name">
</div>
<div class="photo-circle male" style="width:220px;height:220px;">
  <img src="images/male.png" alt="Name">
</div>
```

### Rules that apply automatically (do not override)
- **Background color**: `photo-circle` has no background set — the `.male` / `.female` / `.child-male` / `.child-female` classes supply the correct gray tones by default and the blue/pink tones when the group is expanded. Never add `background` directly to a `photo-circle` div.
- **Grayscale on homepage**: `photo-circle img` has `filter: grayscale(100%)`. Images appear gray at rest.
- **Full color on expand**: `.group.expanded .photo-circle img` removes the filter. Images appear in full color when the group is clicked open.
- **Transparent PNG**: use PNGs with a transparent background so the circle's color shows through around the illustration.
- **Image storage**: save image files under `images/` (e.g. `images/male.png`, `images/female.png`). Do **not** embed base64 data URIs directly in the HTML.

### Standard circle sizes
| Role | Width | Height |
|------|-------|--------|
| Adult female | 200px | 200px |
| Adult male | 220px | 220px |
| Child female | 110px | 110px |
| Child male | 120px | 120px |

### Checklist when adding a new photo
- [ ] Use `photo-circle <gender-class>` (not plain `circle`)
- [ ] Save image as `images/<name>.png` with transparent background
- [ ] Do NOT set a background color on the `photo-circle` div
- [ ] Do NOT touch the grayscale CSS — it applies automatically
