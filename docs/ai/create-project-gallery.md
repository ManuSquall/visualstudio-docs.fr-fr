---
title: Création d’un projet
description: créer un projet à l’aide d’un exemple de la galerie azure machine learning
keywords: ia, visual studio, azure machine learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: a6813e834af00330b4018f16d4a19be945be2be9
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726642"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Créer un projet IA à partir de la galerie Azure Machine Learning dans Visual Studio

Azure Machine Learning est intégré à Visual Studio Tools pour IA. Vous pouvez l’utiliser pour envoyer des tâches machine learning à des cibles de calcul distantes comme des machines virtuelles Azure, des clusters Spark, et bien plus encore. 

Une fois que vous avez [installé Visual Studio Tools pour IA](installation.md), il est facile de créer un projet Python à l’aide de recettes prédéfinies dans la galerie d’exemples Azure Machine Learning.

> [!NOTE]
> Azure Machine Learning Workbench doit être installé. 

1. Lancez Visual Studio. Ouvrez **l’Explorateur de serveurs** en ouvrant le menu **AI Tools** (Outils IA) et en choisissant **Sélectionner un cluster**

    ![Sélecteur de cluster](media/create-project-gallery/select-cluster.png)

2. Connectez-vous à votre abonnement Azure Machine Learning en cliquant avec le bouton droit sur le nœud **Azure Machine Learning** dans l’Explorateur de serveurs, puis sélectionnez **Connexion** et suivez les instructions.

    ![login](media/create-project-gallery/azureml-login.png)

3. Sélectionnez **AI Tools > Azure Machine Learning Sample Gallery** (Outils IA > Galerie d’exemples Azure Machine Learning).

    ![Galerie d’exemples](media/create-project-gallery/gallery.png)

4. Pour ce démarrage rapide, sélectionnez l’exemple « **MNIST using TensorFlow** » (MNIST avec TensorFlow) et cliquez sur **Installer**. Indiquez les éléments suivants :

   - **Groupe de ressources** : groupe de ressources Azure où vos métadonnées seront stockées
   - **Compte** : compte d’expérimentation Azure Machine Learning
   - **Espace de travail** : espace de travail Azure Machine Learning
   - **Type de projet** : framework machine learning. Dans ce cas, choisissez **TensorFlow**
   - **Ajouter à la solution** : détermine s’il faut ajouter à votre solution Visual Studio ou créer et ouvrir une autre solution
   - **Chemin d’accès du projet** : emplacement où enregistrer le code
   - **Nom du projet** : tapez **TensorFlowMNIST**

   ![Projet résultant lors de l’utilisation du modèle Application Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio crée le fichier projet (un fichier `.pyproj` sur le disque), ainsi que d’autres fichiers définis dans l’exemple. Avec le modèle « MNIST », le projet contient plusieurs fichiers.

    ![Capture d’écran de Visual Studio Explorateur de solutions montrant les fichiers pour le projet TensorFlowMNIST. Le code pour tf_mnist. py est affiché dans la fenêtre principale.](media/create-project-gallery/azml-mnist.png)

6. Envoyez la tâche à Azure Machine Learning.

    ![Capture d’écran de l’Explorateur de solutions Visual Studio montrant le menu contextuel du projet TensorFlowMNIST avec « envoyer le travail... » sélectionné.](media/create-project-gallery/submit-azml.png)

7. Procédez à l’exécution dans un conteneur Docker ou sur votre ordinateur local

    ![Capture d’écran de la boîte de dialogue Envoyer un travail avec utiliser le cluster défini sur « azureml:/local » et le script de démarrage défini sur « tf_mnist. py ».](media/create-project-gallery/azml-local.png)
