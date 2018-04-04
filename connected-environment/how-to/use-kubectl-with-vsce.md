---
title: Guide pratique pour utiliser kubectl avec un environnement connecté | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Utiliser `kubectl` avec un environnement connecté

Vous pouvez accéder au cluster Kubernetes à partir d’un environnement connecté et utiliser les outils Kubernetes existants comme `kubectl`.

Sachant que l’exécution de `vsce env create` ou `vsce env select` a pour effet d’ajouter automatiquement un contexte de configuration `kubectl`, kubectl doit déjà être connecté à votre cluster Kubernetes VSCE. Exemples :
- Confirmez le contexte actuel : `kubectl config current-context`
- Listez tous les contextes disponibles : `kubectl config get-contexts`. Le nom d’un cluster kubernetes créé par VSCE se présente comme ceci : « vsce -<guid> ».
- Changez de contexte : `kubectl config use-context <context-name>`
- Affichez le tableau de bord Kubernetes : exécutez `kubectl proxy`, puis ouvrez votre navigateur à l’adresse émise à par cette commande (ajoutez `/ui` à l’URL pour accéder au tableau de bord Kubernetes).
- Listez les services s’exécutant dans l’espace VSCE par défaut nommé *mainline* : `kubectl get services --namespace=mainline`

