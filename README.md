[README_magazzino.md](https://github.com/user-attachments/files/28950459/README_magazzino.md)
# magazzino-ricambi-test
test magazzino
# 🔧 Gestione Ricambi & Magazzino — Termoflex Srl

Dashboard interattiva con AI integrata per il monitoraggio e la diagnosi del magazzino ricambi in un'azienda di manutenzione industriale.

**→ [Apri la dashboard](#)** *(link disponibile dopo il deploy)*

---

## Il problema

Nelle aziende di manutenzione industriale il magazzino ricambi è una variabile critica spesso gestita a memoria o con fogli Excel non aggiornati. Il risultato è sempre lo stesso: il pezzo manca quando serve, oppure il magazzino è pieno di componenti che non si usano da anni.

Entrambi i casi hanno un costo reale:
- **Rottura di stock su ricambi critici** → intervento bloccato, downtime del cliente, penali
- **Sovrastoccaggio di articoli a bassa rotazione** → capitale immobilizzato, spazio occupato, deterioramento

Il responsabile tecnico o il magazziniere non ha uno strumento semplice per leggere la situazione in modo aggregato e anticipare i problemi.

---

## La soluzione

Una dashboard web che trasforma lo storico degli interventi e i livelli di giacenza in informazioni operative chiare:

- **Alert immediati** — articoli esauriti, sotto scorta minima, fermi da troppo tempo
- **ABC Analysis** — classificazione automatica per valore e rotazione
- **Suggerimenti di riordino** — quantità consigliate, costo stimato, lead time
- **Analisi AI on-demand** — Claude legge la situazione e restituisce un piano d'azione prioritizzato

---

## Cosa mostra la dashboard

| Sezione | Contenuto |
|---|---|
| KPI header | Articoli totali, esauriti, sotto scorta, valore magazzino, valore fermo |
| Alert stock | Esauriti, sotto scorta minima, fermi (bassa rotazione) |
| Suggerimenti riordino | Quantità consigliata, costo stimato, urgenza, lead time |
| ABC Analysis | Valore consumato per classe, distribuzione per categoria, top articoli |
| Anagrafica magazzino | Tabella completa con filtri per classe, alert e articoli fermi |
| Analisi AI | Diagnosi Claude con impatto operativo e piano azioni |

---

## Le criticità nel dataset

Il dataset copre 18 mesi di attività (Gen 2023 – Giu 2024) su 20 articoli in 3 categorie (aria compressa, refrigerazione, meccanica):

**Articolo esaurito:**
- `GAS-R32` — Gas refrigerante R-32: giacenza zero, ogni intervento su impianti frigo è bloccato fino al riordino (lead time 5 giorni)

**Sotto scorta minima:**
- `VAL-012` — Valvola di sicurezza 10 bar: giacenza 1 vs minima 4, componente classe A ad alto valore
- `FLT-001` — Filtro aria compressore: giacenza 7 vs minima 10, articolo ad alta rotazione (24 utilizzi in 18 mesi)
- `POM-CEN` — Pompa centrifuga inox: giacenza 1 vs minima 2, lead time 10 giorni

**Articoli fermi (capitale immobilizzato):**
- `SCM-ALU`, `TUB-RAM`, `ELE-CON`, `RES-ELE` — ultimo utilizzo oltre 6 mesi fa, valore complessivo ~€780

---

## Perché questo progetto

Ho gestito operativamente il coordinamento di tecnici su impianti industriali per anni. La gestione dei ricambi era una delle variabili più critiche: un compressore fermo per un filtro mancante ha un costo che va ben oltre il prezzo del componente.

Questo strumento nasce per rispondere a una domanda semplice che raramente trovava risposta rapida: *cosa rischio di non avere quando serve?*

---

## Stack tecnico

| Strumento | Ruolo |
|---|---|
| HTML / CSS / JS | Dashboard single-file, zero dipendenze server |
| Chart.js | Grafici ABC, distribuzione categorie, top articoli |
| Claude API (`claude-sonnet-4-6`) | Analisi AI on-demand del magazzino |
| Netlify Functions | Proxy serverless per la chiave API |
| Python | Generazione del dataset sintetico |

---

## Note sul dataset

I dati sono **sintetici ma realistici**: 20 articoli su 3 categorie, 121 utilizzi registrati in 18 mesi, con giacenze, scorte minime e lead time coerenti con un magazzino ricambi industriale reale.

La classificazione ABC è calcolata automaticamente sul valore consumato nel periodo: classe A (70% del valore, ~30% degli articoli), B (20%), C (10%).

Il metodo è applicabile direttamente a dati reali esportati da qualsiasi gestionale ERP, CMMS o anche da un semplice foglio Excel strutturato.

---

## Autore

**Alessandro Dardi** — Operations & Digital Automation · Bologna
[Portfolio](https://alessandro-dardi.netlify.app) · [LinkedIn](https://www.linkedin.com/in/alessandro-dardi/)
