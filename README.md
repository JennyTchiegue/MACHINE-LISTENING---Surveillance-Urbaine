<div align="center">
# 🎧 Surveillance Sonore Urbaine
 
**Pipeline audio complet : du fichier WAV au modèle déployé**
 
Détection automatique de sons urbains pour la smart city — sirènes, klaxons, coups de feu et plus encore.
 
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?logo=pytorch&logoColor=white)](https://pytorch.org)
[![Gradio](https://img.shields.io/badge/Gradio-Interface-F97316?logo=gradio&logoColor=white)](https://gradio.app)
[![Dataset](https://img.shields.io/badge/UrbanSound8K-8732_sons-00B4D8)](https://urbansounddataset.weebly.com)
 
</div>
---
 
## 📋 Contexte
 
Ce projet s'inscrit dans le cadre du module **Machine Listening**. Le scénario : une municipalité souhaite détecter automatiquement les événements sonores dans ses rues pour déclencher des alertes en temps réel.
 
Notre mission : construire un classifieur de **10 types de sons urbains**, comparer **3 approches** (ML classique, CNN, Transfer Learning) et déployer une **interface interactive**.
 
## 🎯 Objectifs
 
- Classifier des sons urbains en **10 classes** avec une accuracy cible **> 85%**
- Comparer **3 modèles** de complexité croissante
- Déployer une **interface Gradio** utilisable par un non-technique
- Analyser les erreurs et améliorer le modèle par **data augmentation audio**
## 📊 Dataset — UrbanSound8K
 
| | |
|---|---|
| **Sons** | 8 732 fichiers audio |
| **Classes** | 10 |
| **Durées** | 0.1s à 4s (variables) |
| **Folds** | 10 folds prédéfinies (anti data leakage) |
 
**Les 10 classes :**
 
| Classe | Description |
|---|---|
| `air_conditioner` | Climatiseur / ventilation |
| `car_horn` | Klaxon |
| `children_playing` | Enfants qui jouent |
| `dog_bark` | Aboiement |
| `drilling` | Perceuse |
| `engine_idling` | Moteur au ralenti |
| `gun_shot` | Coup de feu |
| `jackhammer` | Marteau-piqueur |
| `siren` | Sirène |
| `street_music` | Musique de rue |
 
## 🛠️ Stack technique
 
| Catégorie | Outils |
|---|---|
| **Audio** | Librosa · torchaudio · NumPy |
| **ML classique** | Scikit-learn (Random Forest, SVM, Gradient Boosting) |
| **Deep Learning** | PyTorch (CNN 3 couches) |
| **Transfer Learning** | HuggingFace Transformers (Audio Spectrogram Transformer) |
| **Augmentation** | SpecAugment (FrequencyMasking + TimeMasking) |
| **Visualisation** | Matplotlib · Seaborn |
| **Déploiement** | Gradio |
| **Données** | HuggingFace Datasets |
 
## 🔄 Pipeline — 10 étapes
 
```
WAV → Resample 16kHz → Normaliser → Padding 4s → Mel-spectrogramme → dB → Modèle → Prédiction
```
 
1. **Explorer & écouter** — Charger UrbanSound8K, écouter les 10 classes, analyser distributions et durées
2. **Preprocessing** — Resample → normalisation → padding/troncature → mel-spectrogramme (128 mels) → conversion dB
3. **Baseline ML** — Random Forest / SVM / Gradient Boosting sur MFCC moyennées (13 coefficients)
4. **Dataset PyTorch** — Classe `Dataset` custom + `DataLoader` respectant les folds (train: 1–8, val: 9, test: 10)
5. **CNN from scratch** — 3 blocs Conv2D + BatchNorm + ReLU + MaxPool, pooling adaptatif, couche dense
6. **Transfer Learning** — Fine-tuning de l'AST (Audio Spectrogram Transformer) pré-entraîné sur AudioSet
7. **Analyse d'erreurs** — Matrice de confusion, écoute des erreurs confiantes, SpecAugment
8. **Interface Gradio** — Upload / micro → prédiction top-5 + spectrogramme, lien public partageable
9. **Peer review** — Audit croisé avec checklist 10 critères
10. **Démo finale** — Pitch 5 min + démo live
## 📈 Résultats
 
| Modèle | Accuracy | Paramètres |
|---|---|---|
| Random Forest (MFCC) | ~65% | — |
| CNN from scratch | ~75% | ~50K |
| AST (Transfer Learning) | **~90%** | 87M (7K entraînés) |
 
> *Les scores exacts dépendent du run. Le gain total RF → AST est d'environ +25 points.*
 
## 🚀 Lancer le projet
 
```bash
# 1. Installer les dépendances
pip install librosa transformers datasets evaluate accelerate torchaudio gradio
 
# 2. Ouvrir le notebook
jupyter notebook Track_A_Surveillance_urbaine_UrbanSound8K.ipynb
 
# 3. Exécuter les cellules dans l'ordre
```
 
## 🖥️ Interface Gradio
 
L'interface permet de :
- **Uploader** un fichier audio ou **enregistrer** depuis le micro
- Voir les **5 classes les plus probables** avec leurs scores de confiance
- Visualiser le **mel-spectrogramme** du son analysé
- Partager un **lien public** (valide 72h) via `share=True`
## 📁 Structure du projet
 
```
.
├── Track_A_Surveillance_urbaine_UrbanSound8K.ipynb   # Notebook principal
├── solutions_urbansound8k.py                         # Solutions complètes
└── README.md
```

# Lien gradio
https://ad52de998b3051307d.gradio.live

## ✍️ Auteurs
 
- **Davis TCHEDJOU**
- **Jenny TCHIEGUE**
---

<div align="center">
<sub>Module Machine Listening — 2025</sub>
</div>
 
