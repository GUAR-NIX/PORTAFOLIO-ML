🇺🇸 **English** · 🇪🇸 [Español](README.es.md)

# Machine learning with temporal validation and APIs

Six projects on public data with confidence intervals, explicit baselines and tested FastAPI services.

| Project | Measured result | Code | Tests |
|---|---|---|---|
| [Cost-based calling threshold](bank-marketing-umbral-costo/README.md) | AUC **0.815** on a stratified split and **0.704** under a temporal stress test; both reported | [code](bank-marketing-umbral-costo/src/campana) | [tests](bank-marketing-umbral-costo/tests) |
| [Customer lifetime value](clv-retail-bgnbd/README.md) | Repurchase AUC **0.810** vs. 0.800 for LightGBM; portfolio revenue error −10.0% | [code](clv-retail-bgnbd/src/clv) | [tests](clv-retail-bgnbd/tests) |
| [Demand forecast by station and hour](demanda-citibike-pronostico/README.md) | WAPE **50.6%** vs. 72.9% for the seasonal baseline, 24 h ahead | [code](demanda-citibike-pronostico/src/demanda_citibike) | [tests](demanda-citibike-pronostico/tests) |
| [Card fraud detection](deteccion-fraude-tarjetas/README.md) | AUPRC **0.782** [0.682; 0.865] for the served model; best unsupervised 0.489 | [code](deteccion-fraude-tarjetas/src/fraude) | [tests](deteccion-fraude-tarjetas/tests) |
| [Land use from satellite images](eurosat-uso-de-suelo/README.md) | **96.98%** accuracy on 5,400 unseen scenes, trained on CPU | [code](eurosat-uso-de-suelo/src/eurosat_suelo) | [tests](eurosat-uso-de-suelo/tests) |
| [Movie recommender](recomendador-movielens/README.md) | NDCG@10 **0.166** vs. 0.125 for recent popularity; ties with EASE | [code](recomendador-movielens/src/recomendador) | [tests](recomendador-movielens/tests) |

## Start here

| If you are looking for… | Go to |
|---|---|
| **A model behind an API** | [Card fraud detection](deteccion-fraude-tarjetas/README.md) · [API code](deteccion-fraude-tarjetas/api) |
| **Validation discipline** | [Cost-based threshold](bank-marketing-umbral-costo/README.md): the temporal test that lowers the headline figure |
| **How it is checked** | [CI workflow](.github/workflows/ci.yml): Ruff, Markdown links and the tests of the six projects, including their APIs |
| **Design and decisions** | The full README of each project (Spanish) has the architecture, limits and reproduction commands |

## How results were measured

- Temporal splits for customer value, demand, fraud and recommendations; the bank campaign reports a stratified and a temporal test.
- Tuning on validation data and reporting on a test set.
- 95% confidence intervals and paired bootstrap for differences between models.
- Cost figures use assumptions that each project states.
- Data are public and historical; nothing here serves real users.

## How to use this repository

```bash
git clone https://github.com/GUAR-NIX/PORTAFOLIO-ML.git
cd PORTAFOLIO-ML/<project>
```

Each project has its own README, tests and `docs/GUIA_PASO_A_PASO.md` (Spanish). Raw data are not versioned: a script gets them from
the official source. The English page of each project is a summary; the full documentation is in Spanish.
See [CONTRIBUTING.md](CONTRIBUTING.md) to run the checks.

## Author

**Erick Guarnizo** · [LinkedIn](https://www.linkedin.com/in/erick-g-571a7b3b4) · [GitHub profile](https://github.com/GUAR-NIX)

## License

Code is under the [MIT](LICENSE) license. Each project's data keep the license of their source, stated in its README.
