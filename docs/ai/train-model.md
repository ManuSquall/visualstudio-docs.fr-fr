---
title: Envoyer une tâche pour l’apprentissage du modèle dans Azure Batch AI
description: former modèle cloud
keywords: ai, visual studio, former un modèle, cloud
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: ec0db69bbde1e2abab7022759ed0f7a3d2a88530
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31046327"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Former des modèles IA dans Azure Batch AI

Batch AI est un service managé qui permet aux chercheurs de données et dans le domaine IA de former des modèles IA et d’autres modèles Machine Learning sur des clusters de machines virtuelles Azure, dont celles avec prise en charge GPU. Vous décrivez les exigences de votre tâche, où trouver les entrées et stocker les sorties, et Batch AI gère le reste. [En savoir plus sur Azure Batch AI](https://docs.microsoft.com/azure/batch-ai/overview)

Comme il est intégré à Visual Studio Tools pour IA, vous pouvez dynamiquement augmenter la taille des instances des modèles d’apprentissage dans Azure.  Une fois que vous avez [installé Visual Studio Tools pour IA](installation.md), il est facile de créer un projet Python à l’aide de recettes prédéfinies dans la galerie d’exemples Azure Machine Learning.

1. Lancez Visual Studio. Ouvrez **l’Explorateur de serveurs** en ouvrant le menu **AI Tools** (Outils IA) et en choisissant **Sélectionner un cluster**

    ![Sélecteur de cluster](media\train-model\select-cluster.png)


2. Développez **AI Tools** (Outils IA). Toutes les ressources Batch AI dont vous disposez sont détectées automatiquement et apparaissent dans l’Explorateur de serveurs.

    ![Galerie d’exemples](media\train-model\batchai.png)

3. Sélectionnez **Affichage > Team Explorer...** pour ouvrir la fenêtre **Team Explorer**, dans laquelle vous pouvez vous connecter à GitHub ou à Visual Studio Team Services, ou cloner un dépôt.

    ![Fenêtre Team Explorer montrant Visual Studio Team Services, GitHub et le clonage d’un dépôt](media\train-model\team-explorer.png)

4. Dans le champ URL, sous **Dépôts Git locaux**, entrez `https://github.com/Microsoft/samples-for-ai`, entrez un dossier pour les fichiers clonés, puis sélectionnez **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans Team Explorer est le dossier spécifique pour recevoir les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans Team Explorer ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

5. Une fois le clonage terminé, cliquez sur **Fichier > Ouvrir une solution > Projet/Solution**

    ![Galerie d’exemples](media\train-model\open-solution.png)

5. Ouvrez **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** dans le répertoire dans lequel vous avez cloné le dépôt

    ![Galerie d’exemples](media\train-model\tensorflowexamples.png)

5. Définir le projet MNIST comme **Projet de démarrage**

    ![Galerie d’exemples](media\train-model\mnist-startup.png)

1. **Cliquez avec le bouton droit sur le **projet MNIST, **Envoyer la tâche**

    ![Galerie d’exemples](media\train-model\submit-job.png)

1. Sélectionnez votre cluster **Azure Batch AI**, puis cliquez sur **Importer**. Sélectionnez le fichier `AzureBatchAI_TF_MNIST.json` pour remplir rapidement quelques valeurs par défaut comme l’image Docker à utiliser. Cliquez ensuite sur **Envoyer**

    ![Galerie d’exemples](media\train-model\submit-batch.png)