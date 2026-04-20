# MACHINE-LISTENING---Surveillance-Urbaine

Ce projet s’inscrit dans le cadre du module Machine Listening et vise à construire un pipeline audio complet, depuis un fichier .wav jusqu’à un modèle de classification déployé.
 Objectif principal : détecter automatiquement des sons urbains dans une logique de smart city.
Objectifs du projet
Classifier des sons urbains en 10 classes
 Comparer 3 modèles de Machine Learning / Deep Learning (ML, CNN, Transfer Learning)
 Atteindre une accuracy > 85%
 Déployer une interface interactive avec Gradio

Dataset utilisé : UrbanSound8K
8 732 fichiers audio
10 classes :
air_conditioner
car_horn
children_playing
dog_bark
drilling
engine_idling
gun_shot
jackhammer
siren
Street_music

Technologies utilisées
Langage : Python
Audio :
Librosa — preprocessing (resampling, spectrogrammes)
NumPy — traitement du signal
Machine Learning :
Scikit-learn — Random Forest (baseline)
Deep Learning :
PyTorch — CNN audio
Audio Spectrogram Transformer — Transfer Learning
Visualisation :
Matplotlib
Déploiement :
Gradio — interface utilisateur

Pipeline du projet (10 étapes)

1. Explorer et écouter les données afin de comprendre les spécificités.

2. Mettre en place le pipeline de preprocessing : resample → normalisation → padding/troncature → mel-spectrogramme → conversion en dB afin de gérer les durées variables.

3. Construire un modèle baseline avec un Random Forest sur des features MFCC pour établir un score de référence simple avant d’utiliser des modèles complexes.

4. Créer un Dataset custom PyTorch et des DataLoaders en respectant les folds (train : 1–8, val : 9, test : 10) pour éviter le data leakage.

5. Implémenter un CNN simple sur spectrogrammes et optimiser ses performances pour battre le modèle baseline.

6. Adapter un modèle AST (Audio Spectrogram Transformer) pré-entraîné sur AudioSet pour classifier les 10 classes d’UrbanSound8K via fine-tuning.

7. Analyser les erreurs du modèle (écoute + inspection) et appliquer des techniques de data augmentation audio (SpecAugment) pour améliorer la généralisation.

8. Déployer une interface web avec Gradio permettant d’uploader ou enregistrer un son et d’afficher la prédiction (top classes + spectrogramme).

9. Évaluer la qualité du pipeline et identifier des axes d’amélioration.

10. Présenter le projet de manière claire et convaincante.


Déploiement
Interface utilisateur avec :
upload audio
prédiction en temps réel
Auteur
 Davis TCHEDJOU & Jenny TCHIEGUE
