# flash-landing-page (Claude Code skill)

Skill untuk generate **landing page "flash" satu file HTML** buat launching produk baru. Simple tapi berkelas, bahasa Indonesia dengan sedikit frasa Inggris, CTA langsung ke checkout (lynk.id / payment gateway), dan gaya visual yang fresh per produk.

## Isi

```
flash-landing-page/
├── SKILL.md                      # instruksi skill
└── reference/
    └── example-workshop.html     # contoh hasil (Works Smarter with Claude!)
```

## Install

Salin folder `flash-landing-page` ke folder skills Claude Code.

**Windows (PowerShell)**

```powershell
Copy-Item -Recurse .\flash-landing-page "$env:USERPROFILE\.claude\skills\"
```

**macOS / Linux**

```bash
cp -r flash-landing-page ~/.claude/skills/
```

Restart sesi Claude Code, lalu panggil dengan `/flash-landing-page` atau bilang "bikin landing page untuk produk baru gw".

## Cara pakai

1. Kirim brief: nama produk, target, keunggulan, isi paket, harga, link checkout, dan flyer/referensi kalau ada.
2. Skill memilih arah desain, membangun satu file HTML, lalu verifikasi di desktop dan mobile.
3. Ganti `CHECKOUT_URL` di bagian `<script>` dengan link lynk.id lu.

## Catatan

- Default-nya polos: tanpa countdown, testimoni, atau FAQ kecuali diminta.
- Skill tidak akan mengarang testimoni, angka peserta, atau kredensial.
