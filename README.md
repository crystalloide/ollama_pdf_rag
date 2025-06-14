# 🤖 Requêter des fichiers PDF en local grâce à Ollama + LangChain

Cette application locale RAG (Retrieval Augmented Generation) permet de discuter avec vos documents PDF grâce à Ollama et LangChain. 

Ce projet comprend un notebook Jupyter pour l'expérimentation 

et une interface web Streamlit pour une interaction simplifiée.

[![Tests Python](https://github.com/tonykipkemboi/ollama_pdf_rag/actions/workflows/tests.yml/badge.svg)](https://github.com/tonykipkemboi/ollama_pdf_rag/actions/workflows/tests.yml)

## Structure du projet
```
ollama_pdf_rag/
├── src/ # Code source
│ ├── app/ # Application Streamlit
│ │ ├── components/ # Composants d'interface utilisateur
│ │ │ ├── chat.py # Interface de chat
│ │ │ ├── pdf_viewer.py # Affichage PDF
│ │ │ └── sidebar.py # Contrôles de la barre latérale
│ │ └── main.py # Application principale
│ └── core/ # Fonctionnalités principales
│ ├── document.py # Traitement des documents
│ ├── embeddings.py # Incorporations vectorielles
│ ├── llm.py # Configuration LLM
│ └── rag.py # Pipeline RAG
├── data/ # Stockage de données
│ ├── pdfs/ # Stockage PDF
│ │ └── sample/ # Exemples de PDF
│ └── vectors/ # Stockage de base de données vectorielles
├── notebooks/ # Bloc-notes Jupyter
│ └── experiments/ # Bloc-notes expérimentaux
├── tests/ # Tests unitaires
├── docs/ # Documentation
└── run.py # Exécuteur d'application
```

## 📺 Tutoriel vidéo
<a href="https://youtu.be/ztBJqzBU5kc">
<img src="https://img.youtube.com/vi/ztBJqzBU5kc/hqdefault.jpg" alt="Regarder la vidéo" width="100%">
</a>

## ✨ Fonctionnalités

- 🔒 Traitement entièrement local : aucune donnée ne quitte votre machine
- 📄 Traitement PDF avec segmentation intelligente
- 🧠 Récupération multi-requêtes pour une meilleure compréhension du contexte
- 🎯 Implémentation RAG avancée avec LangChain
- 🖥️ Interface Streamlit épurée
- 📓 Bloc-notes Jupyter pour expérimentation

## 🚀 Premiers pas

### Prérequis

0. **Sous Windows**

Installer Microsoft Visual Studio Build Tools
La méthode la plus simple consiste à installer Microsoft C++ Build Tools :

Téléchargez « Microsoft C++ Build Tools » depuis la page de téléchargement de Visual Studio.
Pendant l'installation, assurez-vous de sélectionner :

- "C++ build tools" workload
- Windows 10/11 SDK (latest version)
- MSVC v143 compiler toolset

Alternative : Installer Visual Studio Community (si vous préférez un IDE complet) :
Téléchargez Visual Studio Community (gratuit)
Pendant l'installation, sélectionnez "Desktop development with C++" workload



1. **Installer Ollama**
- Visitez le site web d'Ollama (https://ollama.ai) pour télécharger et installer
- Sous Linux:
```bash
curl -fsSL https://ollama.com/install.sh | sh
```
- Lancer le serveur :
```bash
ollama serve
```
- Lister les modèles déjà présents le cas échéant :
```bash
ollama list
```
- Extraire les modèles requis :
```bash
ollama pull llama3.2 # ou votre modèle préféré
ollama pull nomic-embed-text
```

2. **Cloner le dépôt**
```bash
-- git clone https://github.com/tonykipkemboi/ollama_pdf_rag.git
git clone https://github.com/crystalloide/ollama_pdf_rag.git
cd ollama_pdf_rag
```

3. **Configurer l'environnement**
```bash
sudo apt install python3.12-venv
```

```bash
python -m venv venv

# Sous linux : 
source venv/bin/activate      source ./venv/Scripts/activate
# Sous Windows avec bash :
source ./venv/Scripts/activate
# Sous Windows avec cmd :
.\venv\Scripts\activate

python -m pip install --upgrade pip

pip install -r requirements.txt
```

Dépendances Clés et leurs versions :
```txt
ollama==0.4.4
streamlit==1.40.0
pdfplumber==0.11.4
langchain==0.3.14
langchain-core==0.3.29
langchain-ollama==0.2.2
langchain_community==0.3.14
langchain_text_splitters==0.3.5
unstructured>=0.16.12
unstructured[all-docs]>=0.16.12
onnx>=1.17.0
protobuf==5.29.2
chromadb>=0.4.22
Pillow==10.4.0
numpy==1.26.4
pytest==7.4.4
pytest-cov==4.1.0
coverage==7.4.0
pydantic==2.10.4(venv)
```

### 🎮 Exécution de l'application

#### Option 1 : Interface Streamlit
```bash
python run.py
```
Ouvrez ensuite votre navigateur à l'adresse `http://localhost:8501`

![Interface utilisateur Streamlit](st_app_ui.png)
*Interface Streamlit affichant la visionneuse PDF et les fonctionnalités de chat*

#### Option 2 : Bloc-notes Jupyter

```bash
pip install notebook
```

```bash
jupyter notebook
```
Ouvrez `updated_rag_notebook.ipynb` pour expérimenter et tester avec le code fourni

## 💡 Conseils d'utilisation

1. **Télécharger un PDF** : Utilisez l'outil de téléchargement de fichiers dans l'interface Streamlit ou essayez l'exemple de PDF
2. **Sélectionner un modèle** : Choisissez parmi les modèles Ollama disponibles localement
3. **Poser des questions** : Commencez à discuter avec votre PDF via l'interface de discussion
4. **Ajuster l'affichage** : Utilisez le curseur de zoom pour ajuster la visibilité du PDF
5. **Nettoyer** : Utilisez le bouton « Supprimer la collection » lorsque vous changez de document

## 🤝 Contribuer

N'hésitez pas à :
- Ouvrir des problèmes pour signaler des bugs ou des suggestions
- Soumettre des demandes d'extraction
- Commenter la vidéo YouTube pour poser des questions
- Ajouter une étoile au dépôt si vous le trouvez utile !

## ⚠️ Dépannage

- Assurez-vous qu'Ollama s'exécute en arrière-plan
- Vérifiez que les modèles requis sont téléchargés
- Vérifiez que l'environnement Python est activé
- Pour les utilisateurs Windows, assurez-vous que WSL2 est correctement configuré si vous utilisez Ollama

### Erreurs courantes

#### Erreur DLL ONNX
Si vous rencontrez cette erreur :
```
Échec du chargement de la DLL lors de l'importation de onnx_copy2py_export : une routine d'initialisation de la bibliothèque de liens dynamiques (DLL) a échoué.
```

Essayez ces solutions :
1. Installez Microsoft Visual C++ Redistributable :
- Téléchargez et installez les versions x64 et x86 depuis le site web officiel de Microsoft (https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist)
- Redémarrez votre ordinateur après l'installation

2. Si l'erreur persiste, essayez d'installer ONNX Runtime manuellement :
```bash
pip uninstall onnxruntime onnxruntime-gpu
pip install onnxruntime
```
#### Systèmes CPU uniquement
Si vous utilisez un système CPU uniquement :

1. Assurez-vous de disposer de la version CPU d'ONNX Runtime :
```bash
pip uninstall onnxruntime-gpu # Supprimer la version GPU si installée
pip install onnxruntime # Installer la version CPU uniquement
```

2. Vous devrez peut-être modifier la taille des blocs dans le code pour éviter les problèmes de mémoire :
- Réduisez « chunk_size » à 500-1000 si vous rencontrez des problèmes de mémoire
- Augmentez « chunk_overlap » pour une meilleure préservation du contexte

Remarque : L'application sera plus lente sur les systèmes CPU uniquement, mais fonctionnera toujours efficacement.

## 🧪 Tests

### Exécution des tests
```bash
# Exécution de tous les tests
python -m unittest discover tests

# Exécution détaillée des tests
python -m unittest discover tests -v
```

### Hooks pré-commit
Le projet utilise des hooks pré-commit pour garantir la qualité du code. Pour configurer :

```bash
pip install pre-commit
pre-commit install
```

Cela permet :
- d'exécuter des tests avant chaque commit
- d'effectuer des vérifications linting
- de garantir le respect des normes de qualité du code

### Intégration continue
Le projet utilise GitHub Actions pour l'intégration continue. À chaque requête push et pull :
- Les tests sont exécutés sur plusieurs versions de Python (3.9, 3.10, 3.11)
- Les dépendances sont installées
- Les modèles Ollama sont extraits
- Les résultats des tests sont téléchargés sous forme d'artefacts

## 📝 Licence

Ce projet est open source et disponible sous licence MIT.

---

## ⭐️ Histoire des étoiles

[![Graphique de l'histoire des étoiles](https://api.star-history.com/svg?repos=tonykipkemboi/ollama_pdf_rag&type=Date)](https://star-history.com/#tonykipkemboi/ollama_pdf_rag&Date)

Créé avec ❤️ par [Tony Kipkemboi!](https://tonykipkemboi.com)
