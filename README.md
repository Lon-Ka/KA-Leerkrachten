# KA-Leerkrachten Volgsysteem

> Personeelsopvolgingssysteem voor de drie basisscholen van de Scholengemeenschap Kapelle-op-den-Bos BaO.

> ⚠️ **Privacy:** Gebruikersnamen en e-mailadressen worden niet in deze repo opgeslagen. Toegang wordt beheerd via `beheer.html` (SharePoint — niet publiek zichtbaar).

## Scholen

| Sleutel | School |
|---------|--------|
| KIE | Het Kiezeltje |
| KEI | De Kei |
| MUL | 't Mulderke |

## Applicatie

**Live URL:** https://lon-ka.github.io/KA-Leerkrachten/

| Bestand | Functie | Wie |
|---------|---------|-----|
| `index.html` | Hoofdapplicatie: leerkrachten + sollicitanten | Directies + coördinator |
| `beheer.html` | Beheerpanel: toegang, GDPR, competenties | ICT-verantwoordelijke |
| `setup.html` | Eenmalige setup: SharePoint-lijsten aanmaken | ICT-verantwoordelijke (eenmalig) |

## Technologie

- **Frontend:** HTML/CSS/JavaScript (geen framework)
- **Authenticatie:** Microsoft MSAL v3 (inline, geen CDN)
- **Backend:** Microsoft Graph API + SharePoint Online
- **Hosting:** GitHub Pages
- **Dataopslag:** SharePoint Online (gebaskabe.sharepoint.com)

## Azure App Registration

| Parameter | Waarde |
|-----------|--------|
| Client ID | `2ada9cb7-83e9-450b-a632-193715bec13f` |
| Tenant ID | `165074eb-b8b7-49e8-a9b4-54cac7939ed2` |
| Tenant | gebaska-tenant |

**Redirect URIs:**
```
https://lon-ka.github.io/KA-Leerkrachten/
https://lon-ka.github.io/KA-Leerkrachten/index.html
https://lon-ka.github.io/KA-Leerkrachten/beheer.html
https://lon-ka.github.io/KA-Leerkrachten/setup.html
```

**API-machtigingen:**
- `Sites.ReadWrite.All` (Gedelegeerd)
- `Sites.FullControl.All` (Gedelegeerd — voor setup)
- `Mail.Send` (Gedelegeerd — toekomstig)

## SharePoint

**Site:** `https://gebaskabe.sharepoint.com/sites/BaOKA-Leerkrachten`

**SharePoint-lijsten (19):**

| Lijst | Type | Beschrijving |
|-------|------|-------------|
| BEHEER_Toegang | Beheer | Toegangsmatrix gebruikers |
| KIE_Leerkrachten | School | Personeelsdata Het Kiezeltje |
| KIE_Gesprekken | School | Functioneringsgesprekken KIE |
| KIE_Opmerkingen | School | Directienota's KIE |
| KIE_POP | School | Persoonlijk Ontwikkelingsplan KIE |
| KEI_Leerkrachten | School | Personeelsdata De Kei |
| KEI_Gesprekken | School | Functioneringsgesprekken KEI |
| KEI_Opmerkingen | School | Directienota's KEI |
| KEI_POP | School | Persoonlijk Ontwikkelingsplan KEI |
| MUL_Leerkrachten | School | Personeelsdata 't Mulderke |
| MUL_Gesprekken | School | Functioneringsgesprekken MUL |
| MUL_Opmerkingen | School | Directienota's MUL |
| MUL_POP | School | Persoonlijk Ontwikkelingsplan MUL |
| SOL_Sollicitanten | Sollicitant | Sollicitantendossiers |
| SOL_Gesprekken | Sollicitant | Gespreksverslagen sollicitanten |
| SOL_Documenten | Sollicitant | Documentmetadata |
| SOL_Referenties | Sollicitant | Referentiegesprekken |
| SOL_Communicatie | Sollicitant | Communicatielog |
| SOL_Bijlagen | Document Library | Geüploade bijlagen sollicitanten |

## Modules

### Leerkrachtenmodule
- Functiebeschrijving per leerkracht
- Gesprekken (functionering, evaluatie, planning, informeel)
- Opmerkingen (directienota's)
- POP — Persoonlijk Ontwikkelingsplan met voortgangsbalk

### Sollicitantenmodule (scholengroep-breed)
- Statusflow: Nieuw → Uitgenodigd → Gesprek → Beslissing → Afgesloten
- Competentiebeoordeling (20 competenties, 4 domeinen, schaal 1–5)
- Bijlagen uploaden (PDF/Word, max. 10 MB)
- Referenties en communicatielog

## Toegang

| Gebruiker | Email | Scholen | Niveau |
|-----------|-------|---------|--------|
| Directie school 1 + 2 | *(via beheer.html)* | KIE, KEI, MUL | Directie |
| Coördinator | *(via beheer.html)* | KIE, KEI, MUL | Directie |
| ICT-verantwoordelijke | *(via beheer.html)* | KIE, KEI, MUL | Systeembeheer |

## GDPR

- Persoonsdata opgeslagen in Microsoft 365 (EU-datacenters)
- Bewaartermijn sollicitaties: 6 maanden na afwijzing
- GDPR-verwijdering via beheer.html (cascade delete alle gekoppelde records)
- Audittrail via SharePoint versiegeschiedenis

## Contacten

| Rol | Naam | Contact |
|-----|------|---------|
| ICT-verantwoordelijke | *(zie schoolsecretariaat)* | *(intern)* |
| Directie | *(zie schoolsecretariaat)* | *(intern)* |
| Coördinator | *(zie schoolsecretariaat)* | *(intern)* |

---

*Versie 1.0 — 2 juni 2026 — Scholengemeenschap Kapelle-op-den-Bos BaO*
