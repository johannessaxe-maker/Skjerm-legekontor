# Legekontor Infoskjerm

Nettbasert infoskjerm med slideshow, NRK P1 radio, lokalt vÃ¦r og rullende helsetips.

## Filstruktur

```
/
â”œâ”€â”€ index.html          â† Selve skjermen (Ã¥pnes i nettleseren)
â”œâ”€â”€ slides.json         â† Innhold i slideshowet
â”œâ”€â”€ tips.json           â† Helsetips i bunnteksten
â”œâ”€â”€ admin/
â”‚   â”œâ”€â”€ index.html      â† Decap CMS innloggingsside
â”‚   â””â”€â”€ config.yml      â† CMS-konfigurasjon
â””â”€â”€ bilder/             â† Last opp bilder her (JPEG, PNG)
```

---

## Oppsett pÃ¥ GitHub Pages

1. Lag et nytt repository pÃ¥ [github.com](https://github.com), f.eks. `legekontor-skjerm`
2. Last opp alle filene (behold mappestrukturen)
3. GÃ¥ til **Settings â†’ Pages â†’ Source: Deploy from branch â†’ main**
4. Siden er live pÃ¥ `https://DITT-BRUKERNAVN.github.io/legekontor-skjerm/`

---

## Koble til Netlify + Decap CMS (for nettbasert redigering)

### 1. Importer til Netlify
- GÃ¥ til [app.netlify.com](https://app.netlify.com) â†’ **Add new site â†’ Import an existing project**
- Velg GitHub og ditt repository
- Build-kommando: *(la stÃ¥ tom)*
- Publish directory: `/`
- Klikk **Deploy**

### 2. Aktiver Netlify Identity
- GÃ¥ til **Site settings â†’ Identity â†’ Enable Identity**
- Under **Registration**: velg **Invite only**
- Under **Services â†’ Git Gateway**: klikk **Enable Git Gateway**

### 3. Inviter deg selv
- GÃ¥ til **Identity â†’ Invite users** og skriv inn din e-post
- Klikk lenken i e-posten du mottar og sett passord

### 4. Oppdater config.yml
Ã…pne `admin/config.yml` og bytt ut:
```yaml
repo: DITT-BRUKERNAVN/legekontor-skjerm
```
med ditt faktiske GitHub-brukernavn og repo-navn.

### 5. Rediger innhold
- GÃ¥ til `https://DITT-NETTSTED.netlify.app/admin/`
- Logg inn med e-post og passord
- Rediger slides og helsetips i det grafiske grensesnittet
- Klikk **Publish** â€” siden oppdateres automatisk

---

## Legge til bildeslides

Last opp en JPEG-fil i `bilder/`-mappen, deretter legg til i `slides.json`:

```json
{ "type": "image", "image": "bilder/plakat.jpg" }
```

eller med tekst oppÃ¥:

```json
{
  "type": "image-text",
  "image": "bilder/plakat.jpg",
  "tag": "Tilbud",
  "title": "Overskrift her",
  "body": "Kort beskrivelse her"
}
```

Via Decap CMS kan du laste opp bilder og velge type direkte i nettleseren.

---

## Teknisk info

- **VÃ¦r**: MET Norway API (Ã…gotnes, oppdateres hvert 10. min)
- **Radio**: NRK P1 direktestrÃ¸m via `lyd.nrk.no`
- **Ingen server nÃ¸dvendig** â€” fungerer som statisk nettside
