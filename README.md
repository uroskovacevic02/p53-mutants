# p53 Mutants klasifikacija

Seminarski rad iz predmeta Istraživanje podataka 2 (Matematički fakultet, Univerzitet u Beogradu).

Cilj je predvideti transkripcionu aktivnost mutanata p53 proteina (`active` vs `inactive`)
na osnovu biofizičkih atributa, metodom klasifikacije.

## Skup podataka

UCI "p53 Mutants" (dataset #188), verzija K8 (2010):

- 16772 sloga, 5408 numeričkih atributa i jedna ciljna kolona.
- Atributi 1-4826: 2D elektrostatičke i površinske osobine.
- Atributi 4827-5408: 3D osobine zasnovane na rastojanjima.
- Klasa: `active` (143 sloga) ili `inactive` (16629 slogova).
- Skup je jako nebalansiran (samo ~0.85% aktivnih) i ima nedostajuće vrednosti.

## Struktura projekta

```
p53-mutation/
├── README.md
├── requirements.txt
├── p53_classification.ipynb   glavni notebook
├── data/
│   ├── raw/         p53+mutants.zip i K8.data (veliko, van gita)
│   └── processed/   train_test.npz (van gita)
├── models/          sacuvani modeli i skaler (.joblib, van gita)
├── figures/         grafici (.png)
├── results/         metrics.csv i cv_metrics.csv
└── docs/            dokumentacija.tex i dokumentacija.pdf
```

Sirovi i preprocesirani podaci, kao i modeli, izostavljeni su iz git repozitorijuma zbog
veličine, ali se u celosti regenerišu pokretanjem notebook-a.

## Pokretanje

1. Instalirati zavisnosti:

   ```
   pip install -r requirements.txt
   ```

2. Postaviti `p53+mutants.zip` u `data/raw/`
   (preuzima se sa https://archive.ics.uci.edu/dataset/188/p53+mutants).

3. Otvoriti `p53_classification.ipynb` i pokrenuti sve ćelije (Run All). Prva ćelija raspakuje
   `K8.data` iz arhive ako već nije raspakovan. Notebook redom radi: učitavanje, EDA i
   vizuelizaciju, preprocesiranje, redukciju atributa, treniranje 18 modela, unakrsnu
   validaciju, podešavanje hiperparametara i poređenje. Grafici se snimaju u `figures/`, a
   metrike u `results/`.
   
## Rezultati ukratko

Pošto je skup jako nebalansiran, modeli se porede po F1-meri, ROC-AUC i PR-AUC za klasu
`active`, a ne po tačnosti. Random Forest se pokazao kao najbolji i najstabilniji model
(u unakrsnoj validaciji na svim atributima F1 oko 0.52 i PR-AUC oko 0.55). Detaljni rezultati
i tumačenje nalaze se u dokumentaciji.

## Autor

Uroš Kovačević 76/2021
