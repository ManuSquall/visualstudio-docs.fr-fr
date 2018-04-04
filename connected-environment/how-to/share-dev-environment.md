---
title: Guide pratique pour partager un environnement de développement | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 3/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 9808e1ac3a6d7b3381b807bc0ce209e15f3e97cf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="share-a-development-environment"></a>Partager un environnement de développement

Avec Connected Environment, vous pouvez partager votre environnement de développement avec les autres membres de votre équipe. Chaque développeur peut travailler dans son propre espace sans craindre de perturber les autres. De même, le travail collaboratif au sein d’un même environnement peut vous permettre de tester le code de bout en bout sans avoir à créer des objets fictifs ou à simuler des dépendances. Pour plus d’informations, consultez le guide intitulé [Découvrir le développement en équipe](../get-started-nodejs-06.md).

Pour configurer un environnement pour plusieurs développeurs :
1. [Créez un environnement connecté dans Azure](../get-started.md). Vous devez disposer d’un accès Propriétaire ou Contributeur à l’abonnement Azure sélectionné.
1. Configurez le **groupe de ressources** de l’environnement de sorte qu’un [accès Contributeur soit accordé](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure) à chaque membre de l’équipe. Vous pouvez vérifier le groupe de ressources d’un environnement en exécutant cette commande : `vsce env list`
1. Demandez aux membres de l’équipe de **sélectionner l’environnement** dans lequel ils vont développer.
     * **Ligne de commande ou VS Code** : pour afficher les environnements connectés existants, vous avez accès à : `vsce env list`. Pour sélectionner un environnement : `vsce env select`.
     * **IDE Visual Studio** : ouvrez un projet dans Visual Studio, sélectionnez **Connected Environment for AKS** dans la liste déroulante des paramètres de lancement. Dans la boîte de dialogue qui s’ouvre, sélectionnez un environnement de développement existant.

![Liste déroulante des paramètres de lancement Visual Studio](../images/LaunchSettings.png)