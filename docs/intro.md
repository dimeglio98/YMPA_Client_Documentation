---
slug: /
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
- [Ricambi](/model-description/Ricambi)
- [Fornitori](/model-description/Fornitori)
- [FornitoriRicambi](/model-description/FornitoriRicambi)

### MongoDB
- [Prenotazioni](/model-description/Prenotazioni)
- [Preventivi](/model-description/Preventivi)
- [Giorni del calendario](/model-description/Giorni%20del%20calendario)
- [Fatture](/model-description/Fatture)
- [Sconti applicabili](/model-description/Sconti)
- [Lavorazioni disponibili](/model-description/Lavori)
- [Spese Ricorrenti](/model-description/Spese)
#### In più sono disponibili query aggiuntive per l'admin [qui](/admin/Riepilogo)

**I metodi utilizzati sono get e post, per tutti i db**

:::info
Tutti i modelli disponogno di campi **created_at**, **updated_at**, **id** (o **_id**, nel caso di modelli di *MongoDB*) gestiti direttamente dall'engine
:::

:::danger ATTENZIONE
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
