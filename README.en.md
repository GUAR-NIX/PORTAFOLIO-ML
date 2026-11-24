🇪🇸 [Español](README.md) · 🇬🇧 **English**

# Machine Learning portfolio

Cost-sensitive classification, forecasting, recommendation, customer lifetime value, computer vision and fraud detection, with
leak-free validation, intervals and APIs.

**Main tools:** scikit-learn · LightGBM · PyTorch · SHAP · FastAPI

Each folder is an independent project with its own README (results first), step-by-step guide, automated tests and
reproduction instructions. Raw data are not versioned: every project ships a script that downloads them from the official
source.

> 🌐 Each project has an English summary with its key results; the full documentation is in Spanish.

## Projects

| Project | What it is about |
|---|---|
| [**📞 Who to call? Term-deposit campaign with ML**](bank-marketing-umbral-costo/README.en.md) | Which customers a bank should call, with calibrated probabilities and a cost/benefit threshold |
| [**💎 Who is still alive and how much are they worth? CLV and retention in retail (BG/NBD + Gamma-Gamma)**](clv-retail-bgnbd/README.en.md) | Which customers are still active, how often they will buy and whom to win back, on 1.07 million lines |
| [**🚲 How many bikes will leave each station tomorrow? Demand forecast by station and hour (Citi Bike + weather)**](demanda-citibike-pronostico/README.en.md) | Global LightGBM over 44.3 million trips, with rolling-origin backtesting |
| [**💳 Card fraud detection: unsupervised anomalies vs. supervised models**](deteccion-fraude-tarjetas/README.en.md) | Is it necessary to label fraud, or is looking for what is unusual enough? Ten models on 284,807 transactions |
| [**🛰️ Land use with Sentinel-2 (EuroSAT): spectral indices vs. transfer learning on CPU**](eurosat-uso-de-suelo/README.en.md) | Five models on 27,000 satellite scenes, trained only on CPU |
| [**🎬 What movie to watch now? Recommender on MovieLens 25M**](recomendador-movielens/README.en.md) | Hybrid recommender over 25 million ratings with a temporal split |

## How to use this repository

```bash
git clone https://github.com/GUAR-NIX/PORTAFOLIO-ML.git
cd PORTAFOLIO-ML/<project>
```

Inside each project, follow the reproduction section of its README and `docs/GUIA_PASO_A_PASO.md` (Spanish).

## Author

**Erick Guarnizo** · [LinkedIn](https://www.linkedin.com/in/erick-g-571a7b3b4)

## License

Code is under the [MIT](LICENSE) license. Each project's data keep the license of their source, stated in its README.
