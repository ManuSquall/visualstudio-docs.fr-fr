---
title: "Former un modèle TensorFlow localement"
description: "Exécuter un modèle TensorFlow localement dans Visual Studio Tools pour IA"
keywords: ia, visual studio, tensorflow, local
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.technology: visual studio
ms.devlang: python
ms.service: multiple
ms.openlocfilehash: 2b48acc8cfea97a89c32ce7180d693246ca6ab26
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="train-a-tensorflow-model-locally"></a>Former un modèle TensorFlow localement 

Dans ce démarrage rapide, nous allons former un modèle TensorFlow avec le jeu de données [MNIST](http://yann.lecun.com/exdb/mnist/) localement dans Visual Studio Tools pour IA. La base de données MNIST a un jeu d’apprentissage constitué de 60 000 exemples et un jeu de test de 10 000 exemples de chiffres manuscrits. 

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, vérifiez que les composants suivants sont installés :

### <a name="google-tensorflow"></a>Google TensorFlow 

Exécutez la commande suivante dans un terminal. 
```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy et SciPy 
Installez [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) et [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy). 

### <a name="download-sample-code"></a>Télécharger un exemple de code
Téléchargez ce [dépôt GitHub](https://github.com/Microsoft/samples-for-ai) contenant des exemples pour démarrer le deep learning sur TensorFlow, CNTK, Theano et bien plus encore. 

## <a name="open-solution-and-train-model"></a>Ouvrir une solution et former un modèle

- Lancez Visual Studio et sélectionnez **Fichier > Ouvrir > Projet/Solution**.

- Sélectionnez le dossier **Exemples TensorFlow** dans le dépôt des exemples téléchargé et ouvrez le fichier **TensorflowExamples.sln**. 

![Ouvrir un projet](media\tensorflow-local\open-project.png)

![Ouvrir une solution](media\tensorflow-local\open-solution.png)

- Recherchez le projet MNIST dans **l’Explorateur de solutions**, cliquez avec le bouton droit et sélectionnez **Définir comme projet de démarrage**.

- Cliquez sur **Démarrer**. 

- La sortie est imprimée dans la console.

![Exemple de sortie de console](media\tensorflow-local\console-output.png)

> [!div class="nextstepaction"]
> [Former un modèle TensorFlow dans le cloud](tensorflow-vm.md)