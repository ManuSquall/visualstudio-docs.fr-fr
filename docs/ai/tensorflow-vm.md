---
title: "Exécuter un modèle TensorFlow dans le cloud"
description: "exécuter un modèle tensorflow dans une machine virtuelle azure deep learning"
keywords: ia, visual studio, machine virtuelle deep learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: 424072fd91672921c470dbc16e1a9287b1cc575a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Former un modèle TensorFlow dans le cloud

Dans ce didacticiel, nous allons former un modèle TensorFlow avec le [jeu de données MNIST](http://yann.lecun.com/exdb/mnist/) dans une machine virtuelle Azure [Deep Learning](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview). 

La base de données MNIST a un jeu d’apprentissage constitué de 60 000 exemples et un jeu de test de 10 000 exemples de chiffres manuscrits.

## <a name="prerequisites"></a>Prérequis
Avant de commencer, vérifiez que les composants suivants sont installés et configurés :

### <a name="setup-azure-deep-learning-virtual-machine"></a>Configurer la machine virtuelle Azure Deep Learning

> [!NOTE] 
> Définissez Linux comme **type de système d’exploitation**.

Des instructions de configuration de la machine virtuelle Deep Learning sont accessibles [ici](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm). 

### <a name="remove-comment-in-parens"></a>Supprimer le commentaire entre parenthèses

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Télécharger un exemple de code

Téléchargez ce [dépôt GitHub](https://github.com/Microsoft/samples-for-ai) contenant des exemples pour démarrer le deep learning sur TensorFlow, CNTK, Theano et bien plus encore. 

## <a name="open-project"></a>Ouvrir un projet

- Lancez Visual Studio et sélectionnez **Fichier > Ouvrir > Projet/Solution**.

- Sélectionnez le dossier **Exemples TensorFlow** dans le dépôt des exemples téléchargé et ouvrez le fichier **TensorflowExamples.sln**. 

![Ouvrir un projet](media\tensorflow-local\open-project.png)

![Ouvrir une solution](media\tensorflow-local\open-solution.png)

## <a name="add-azure-remote-vm"></a>Ajouter la machine virtuelle distante Azure

Dans l’Explorateur de serveurs, cliquez avec le bouton droit sur le nœud **Remote Machines** (Ordinateurs distants) sous le nœud AI Tools (Outils IA) et sélectionnez « Ajouter...». Entrez le nom d’affichage de l’ordinateur distant ainsi que l’hôte IP, le port SSH, le nom d’utilisateur et le fichier de clé/mot de passe. 

![Ajouter un nouvel ordinateur distant](media\tensorflow-vm\add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Envoyer la tâche à la machine virtuelle Azure
Cliquez avec le bouton droit sur le projet MNIST dans **l’Explorateur de solutions**, puis sélectionnez **Envoyer la tâche**.

![Envoi de tâche à un ordinateur distant](media\tensorflow-vm\job-submission.png)

Dans la fenêtre d’envoi :

- Dans la liste **Cluster to use** (Utiliser le cluster), sélectionnez l’ordinateur distant (avec le préfixe « rm: ») auquel envoyer la tâche.

- Entrez un **nom de la tâche**. 

- Cliquez sur **Envoyer**. 

## <a name="check-status-of-job"></a>Vérifier l’état de la tâche 
Pour afficher l’état et les détails relatifs aux tâches : développez la machine virtuelle à laquelle vous avez envoyé la tâche dans **l’Explorateur de serveurs**. Double cliquez sur **Tâches**.

![Explorateur de travaux](media\tensorflow-vm\job-browser.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Arrêtez la machine virtuelle si vous prévoyez de l’utiliser dans un futur proche. Si vous avez terminé ce didacticiel, exécutez la commande suivante pour nettoyer les ressources :

```azurecli-interactive
az group delete --name myResourceGroup
```