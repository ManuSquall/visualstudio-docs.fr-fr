---
title: Installer des outils d’intelligence artificielle
description: Explique comment installer des outils d’intelligence artificielle pour Visual Studio.
keywords: ia, visual studio
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: ffa8c7634c0d97dd24ff69814ae73ad5ff12928b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800201"
---
# <a name="installation"></a>Installation

Visual Studio Tools pour IA peut être installé sur les systèmes d’exploitation Windows 64 bits.

## <a name="install-visual-studio-tools-for-ai"></a>Installer Visual Studio Tools for AI

Cette extension fonctionne avec Visual Studio 2015 et Visual Studio 2017 Community Edition ou version ultérieure.

Vous pouvez télécharger les outils sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017) ou dans Visual Studio :

1. Sélectionnez **Outils**  >  **extensions et mises à jour**.

   ![Menu Extensions et mises à jour dans Visual Studio](media/installation/extensions.png)

2. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez **En ligne** sur le côté gauche.
3. Dans la zone de recherche en haut à droite, tapez ou entrez « Tools for AI ».
4. Sélectionnez **Visual Studio Tools for AI** dans les résultats.
5. Sélectionnez **Télécharger**.

## <a name="prepare-your-local-machine"></a>Préparer votre ordinateur local
Avant d’entraîner des modèles de Deep Learning sur votre ordinateur local, vérifiez que les composants requis applicables sont installés, y compris la dernière version des pilotes et des bibliothèques de votre GPU NVIDIA (si vous en avez un). Veillez également à installer Python et les bibliothèques Python, notamment NumPy et SciPy, ainsi que les frameworks de Deep Learning, comme Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch ou Chainer, que vous prévoyez d’utiliser dans votre projet.

> [!NOTE]
> La présentation des logiciels dans les sous-sections suivantes provient de leurs pages d’accueil.

### <a name="nvidia-gpu-driver"></a>Pilote GPU NVIDIA

Les frameworks deep learning tirent parti de la GPU NVIDIA pour permettre aux machines d’apprendre à une vitesse, avec une précision et à une échelle proches de l’intelligence artificielle réelle. Si votre ordinateur possède des cartes GPU NVIDIA, consultez [Téléchargements de pilotes NVIDIA](https://www.nvidia.com/Download/index.aspx) ou essayez de mettre à jour le système d’exploitation pour installer le pilote le plus récent.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) est une plateforme de calcul parallèle et un modèle de programmation inventé par NVIDIA. Il permet d’améliorer considérablement les performances de calcul en exploitant la puissance de la GPU. Actuellement, CUDA Toolkit 8.0 est requis par les frameworks deep learning.

Pour installer CUDA

- Visitez ce [site](https://developer.nvidia.com/cuda-80-ga2-download-archive), téléchargez CUDA et installez-le.
- Veillez à installer les bibliothèques runtime CUDA, puis ajoutez le chemin binaire CUDA à la variable d’environnement %PATH% ou $Path.
- Sous Windows, ce chemin est « C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin » par défaut.

![Installer CUDA sous Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

La bibliothèque [cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network) est une bibliothèque avec accélération GPU de primitives pour les réseaux neuronaux profonds par NVIDIA. cuDNN v6 est requis par les frameworks deep learning les plus récents.

Pour installer cuDNN

- Accédez au site [NVIDIA Developer](https://developer.nvidia.com/rdp/cudnn-download) pour télécharger et installer le package le plus récent.
- Veillez à ajouter le répertoire contenant le chemin binaire cuDNN à la variable d’environnement %PATH% ou $Path.
- Sous Windows, vous pouvez copier cudnn64_6.dll dans « C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin ».

> [!NOTE]
> Les frameworks deep learning précédents comme CNTK 2.0 et TensorFlow 1.2.1 nécessitent cuDNN v5.1. Toutefois, vous pouvez installer plusieurs versions cuDNN ensemble.

### <a name="python"></a>Python

Python a représenté le langage de programmation principal pour les applications deep learning. Une distribution Python **64 bits** est nécessaire et [Python 3.5.4](https://www.python.org/downloads/release/python-354/) est recommandé pour une compatibilité optimale.

### <a name="to-install-python-on-windows"></a>Pour installer Python sous Windows

- Nous vous conseillons d’installer le lanceur Python pour vous-même uniquement et d’ajouter Python à la variable d’environnement %PATH%.
- Veillez à installer pip, qui est le système de gestion des packages pour installer et gérer des packages logiciels écrits dans Python.

Les frameworks deep learning s’appuient sur pip pour leur propre installation.

![Installer Python sur Windows](media/installation/install_python_win.png)

Ensuite, nous devons vérifier si Python 3.5 est installé correctement, et mettre à niveau pip vers la dernière version en exécutant les commandes suivantes dans un terminal :

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python sous Visual Studio

Python est entièrement pris en charge dans Visual Studio via les extensions.
Découvrez plus en détail l’installation de [Python pour Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) pour plus d’informations.

### <a name="numpy-and-scipy"></a>NumPy et SciPy

- **NumPy** est un package de traitement de tableaux à usage général conçu pour manipuler efficacement des tableaux multidimensionnels volumineux d’enregistrements arbitraires sans pour autant sacrifier trop de vitesse pour les tableaux multidimensionnels de petite taille.

- **SciPy** est un logiciel open source pour les mathématiques, les sciences et l’ingénierie, dépendant de NumPy. Depuis la version 1.0.0, SciPy a maintenant un package wheel prédéfini officiel pour Windows.

Pour installer NumPy et SciPy, exécutez la commande suivante dans un terminal :

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> La commande ci-dessus met à niveau les packages NumPy et SciPy anciens ou non officiels (par exemple, les packages tiers de http://www.lfd.uci.edu/~gohlke/pythonlibs/ pour Windows) avec les packages officiels les plus récents.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) est une boîte à outils deep learning unifiée qui décrit les réseaux neuronaux comme une série d’étapes de calculs via un graphique orienté. CNTK prend en charge les langages de programmation Python et BrainScript.

> [!NOTE]
> CNTK ne prend actuellement pas en charge macOS.

Pour installer le package CNTK Python, consultez [Guide pratique pour installer CNTK](/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) est une bibliothèque de logiciels open source utilisée pour le calcul numérique à l’aide de graphiques de flux de données. Pour obtenir des instructions d’installation détaillées, rendez-vous [ici](https://www.tensorflow.org/install/).

> [!NOTE]
> À compter de la version 1.2, TensorFlow n’assure plus la prise en charge GPU pour macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) est un framework deep learning léger, modulaire et scalable. Basé sur le produit Caffe d’origine, Caffe2 a été conçu en privilégiant l’expression, la vitesse et la modularité.

Pour l’instant, aucun package wheel python Caffe2 prédéfini n’est disponible.

Rendez-vous [ici](https://caffe2.ai/docs/getting-started.html) pour une génération à partir du code source.

### <a name="mxnet"></a>MXNet

[Apache MXNet (en développement)](https://mxnet.incubator.apache.org/) est un framework deep learning conçu pour l’efficacité et la flexibilité. Il vous permet de **mélanger une ** [programmation symbolique et impérative](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) afin d’optimiser l’efficacité et la productivité.

Pour installer MXNet, exécutez la commande suivante dans un terminal :

- Avec GPU

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Sans GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) est une API de réseaux neuronaux de haut niveau, écrite dans Python et capable de s’exécuter sur CNTK, TensorFlow ou Theano. Elle a été développée dans le but de permettre des expérimentations rapides. Pour effectuer des recherches optimales, il est essentiel de pouvoir passer de l’idée à son résultat dans un délai le plus court possible.

Pour installer Keras, exécutez la commande suivante dans un terminal :

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) est une bibliothèque Python qui vous permet de définir, d’optimiser et d’évaluer des expressions mathématiques impliquant des tableaux multidimensionnels efficacement.

Pour installer Theano, exécutez la commande suivante dans un terminal :

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) est un package python qui fournit deux fonctionnalités principales :

- Calcul de tenseur (comme NumPy) avec une accélération GPU forte
- Réseaux neuronaux profonds basés sur un système de rétrogradation de bande

Pour installer PyTorch, exécutez la commande suivante dans un terminal :

- **Windows**

  Il n’existe encore aucun package wheel officiel. Vous pouvez télécharger un package tiers à partir d’[Anaconda](https://anaconda.org/pytorch/repo?type=all) ou [University of California](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Décompressez-le dans votre répertoire de base, par exemple, *C:\Users\test\pytorch*.
  - Ajoutez *C:\Users\test\pytorch\Lib\site-packages* à la variable d’environnement %PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **MacOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > Les binaires macOS ne prenant pas en charge CUDA, installez-le à partir de la source si CUDA est nécessaire

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Ce package unique prend en charge les GPU et UC.

Enfin, installez torchvision ailleurs que sur Windows :

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) est un framework deep learning basé sur Python visant la flexibilité. Il fournit des API de différenciation automatique basées sur l’approche de définition par exécution (également appelées graphes de calcul dynamique), ainsi que des API de haut niveau orientées objet pour créer et former des réseaux neuronaux.

Pour activer la prise en charge CUDA, installez [CuPy](https://github.com/cupy/cupy) :

```bash
pip3.5 install cupy
```

> [!NOTE]
> Sur Windows, vous avez besoin de la version 2015 de [Visual Studio](https://visualstudio.microsoft.com/) ou de [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) pour compiler CuPy avec CUDA 8.0.

Pour installer Chainer, exécutez la commande suivante dans un terminal :

```bash
pip3.5 install chainer==3.0.0
```
