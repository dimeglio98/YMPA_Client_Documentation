---
sidebar_position: 1
sidebar_label: "Introduzione"
---

# Introduzione
Descrizione delle API per **YMPA Client**

## Database presenti

Il backend è composto da due database, di tipi diversi:
- SQL, in Postgresql
- MongoDB

## Modelli presenti

### SQL
- [Ricambi](/docs/model-description/Ricambi)
- [Fornitori](/docs/model-description/Fornitori)
- [FornitoriRicambi](/docs/model-description/FornitoriRicambi)

### MongoDB
- Prenotazioni
- Preventivi
- Giorni del calendario
- Fatture
- Sconti applicabili
- Lavorazioni disponibili

I metodi utilizzati sono get e post, per tutti i db
:::danger
Tutte le query sono **case sensitive**
:::
<!-- 
## Getting Started

Get started by **creating a new site**.

Or **try Docusaurus immediately** with **[docusaurus.new](https://docusaurus.new)**.

## Generate a new site

Generate a new Docusaurus site using the **classic template**:

```shell
npm init docusaurus@latest my-website classic
```

## Start your site

Run the development server:

```shell
cd my-website

npx docusaurus start
```

Your site starts at `http://localhost:3000`.

Open `docs/intro.md` and edit some lines: the site **reloads automatically** and displays your changes. -->
