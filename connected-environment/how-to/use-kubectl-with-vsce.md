---
title: Guide pratique pour utiliser kubectl avec un environnement connecté | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Utiliser `kubectl` avec un environnement connecté

Vous pouvez accéder au cluster Kubernetes à partir d’un environnement connecté et utiliser les outils Kubernetes existants comme `kubectl`.

Sachant que l’exécution de `vsce env create` ou `vsce env select` a pour effet d’ajouter automatiquement un contexte de configuration `kubectl`, kubectl doit déjà être connecté à votre cluster Kubernetes VSCE. Exemples :
- Confirmez le contexte actuel : `kubectl config current-context`
- Listez tous les contextes disponibles : `kubectl config get-contexts`. Le nom d’un cluster kubernetes créé par VSCE se présente comme ceci : « vsce -<guid> ».
- Changez de contexte : `kubectl config use-context <context-name>`
- Affichez le tableau de bord Kubernetes : exécutez `kubectl proxy`, puis ouvrez votre navigateur à l’adresse émise à par cette commande (ajoutez `/ui` à l’URL pour accéder au tableau de bord Kubernetes).
- Listez les services s’exécutant dans l’espace VSCE par défaut nommé *mainline* : `kubectl get services --namespace=mainline`

