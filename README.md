# p53 Mutants klasifikacija

Seminarski rad iz predmeta Istraživanje podataka 2 (Matematički fakultet).

Cilj je predvideti transkripcionu aktivnost mutanata p53 proteina
(`active` vs `inactive`) na osnovu biofizičkih atributa, metodom klasifikacije.

## Skup podataka

UCI "p53 Mutants" (dataset #188), verzija K8 (2010):

- 16772 sloga, 5409 kolona.
- Atributi 1-4826: 2D elektrostatičke i površinske osobine.
- Atributi 4827-5408: 3D osobine zasnovane na rastojanjima.
- Atribut 5409: klasa (`active` / `inactive`).
- Nedostajuće vrednosti označene su sa `?`.
- Skup je jako nebalansiran: samo 143 od 16772 sloga je `active` (~0.85%).

Klasa `active` označava transkripciono kompetentan p53, a `inactive`
kancerozni, neaktivni p53.

## Struktura projekta

```
p53-mutation/
├── README.md
├── requirements.txt
├── p53_classification.ipynb   glavni notebook
├── data/
│   ├── raw/         sirovi podaci (p53+mutants.zip, K8.data)
│   └── processed/   preprocesirani skup
├── models/          sačuvani modeli (.joblib)
├── figures/         grafici (.png)
└── results/         tabele metrika (.csv)
```

## Pokretanje

1. Postaviti `p53+mutants.zip` u `data/raw/`
   (preuzima se sa https://archive.ics.uci.edu/dataset/188/p53+mutants).
2. Instalirati zavisnosti:

   ```
   pip install -r requirements.txt
   ```

3. Pokrenuti `p53_classification.ipynb`. Prva ćelija raspakuje `K8.data`
   iz arhive ako već nije raspakovan.

Sirovi podaci su veliki (~617MB raspakovano) i nisu deo git repozitorijuma.
