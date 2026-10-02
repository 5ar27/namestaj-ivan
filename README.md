# Nameštaj Ivan · Kruševac

Sajt za radionicu nameštaja po meri **Nameštaj Ivan** iz Kruševca: garniture, kreveti i francuski ležajevi, kuhinje, stolovi i stolice.

Statičan sajt (HTML, CSS i JavaScript) koji ne zahteva build, server ni bazu podataka.

## Struktura

```
index.html            cela stranica (stil i skripte su u fajlu)
assets/frames/        141 frejm uvodnog videa (WebP) za animaciju pri skrolovanju
assets/img/           fotografije kolekcija i galerije (WebP)
.nojekyll             isključuje Jekyll obradu na GitHub Pages
```

## Objavljivanje na GitHub Pages

1. Na GitHub-u napravite novi repozitorijum, npr. `namestaj-ivan`.
2. Uploadujte **sadržaj** ovog foldera (ne sam folder), tako da `index.html` bude u korenu repozitorijuma.
   Na sajtu GitHub-a: *Add file → Upload files*, prevucite sve fajlove i foldere, pa *Commit changes*.
3. Idite na *Settings → Pages*, pod **Source** izaberite *Deploy from a branch*, zatim granu `main` i folder `/ (root)`, pa *Save*.
4. Posle jednog do dva minuta sajt je dostupan na `https://<korisnicko-ime>.github.io/namestaj-ivan/`.

### Sopstveni domen (npr. namestajpomerikrusevac.rs)

1. U *Settings → Pages → Custom domain* upišite domen i sačuvajte.
2. Kod registra domena podesite DNS:
   - za `www`: CNAME zapis ka `<korisnicko-ime>.github.io`
   - za goli domen: A zapisi ka `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. Kad se DNS proširi, uključite **Enforce HTTPS**.

## Lokalni pregled

Otvorite folder u terminalu i pokrenite:

```
python -m http.server 8000
```

Zatim otvorite `http://localhost:8000`. Može i dvoklik na `index.html`, ali lokalni server je pouzdaniji.

## Izmene sadržaja

- **Tekstovi i kontakt podaci** su u `index.html`. Pretražite tekst koji želite da promenite.
- **Slike:** zamenite fajl u `assets/img/` fajlom istog imena. Preporuka je WebP, širine 1600–2000 px.
- **Uvodni video:** frejmovi su u `assets/frames/` (`001.webp` … `141.webp`). Ako menjate video, napravite nove frejmove, npr.:
  ```
  ffmpeg -i video.mp4 -vf fps=15 -c:v libwebp -quality 84 assets/frames/%03d.webp
  ```
  i u `index.html` podesite `const N=141` na novi broj frejmova.

## Kontakt forma

Forma je trenutno samo vizuelna: GitHub Pages ne može da šalje mejlove. Da bi upiti stizali na mejl, povežite formu sa servisom kao što su [Formspree](https://formspree.io) ili [Web3Forms](https://web3forms.com):
u `<form id="f">` dodajte `action="…"` i `method="POST"` i uklonite `e.preventDefault()` iz skripte na dnu fajla.

## Napomene

- Fontovi (Bodoni Moda, Jost) se učitavaju sa Google Fonts.
- Ako posetilac ima uključeno smanjenje animacija, sajt automatski isključuje paralaks i horizontalni skrol.
