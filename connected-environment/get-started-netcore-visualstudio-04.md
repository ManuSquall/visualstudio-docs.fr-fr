---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 4 - Déboguer un conteneur dans Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 9b3aa6b0f710707800ea9a1f0533b0c37681ea05
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Bien démarrer avec Connected Environment et .NET Core et Visual Studio

Étape précédente : [Créer un environnement de développement dans Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Déboguer un conteneur dans Kubernetes
Une fois que l’environnement de développement a été créé, vous pouvez déboguer l’application. Définissez un point d’arrêt dans le code, par exemple à la ligne 20 dans le fichier `HomeController.cs` où la variable `Message` est définie. Cliquez sur **F5** pour commencer le débogage. 

Visual Studio communique avec l’environnement de développement pour générer et déployer l’application et ouvrir ensuite un navigateur dans lequel l’application web s’exécute. Vous pouvez penser que le conteneur s’exécute localement, mais en réalité, il s’exécute dans notre environnement de développement dans Azure. La présence de l’adresse localhost s’explique par le fait que Connected Environment crée un tunnel SSH temporaire vers le conteneur en cours d’exécution dans Azure.

Cliquez sur le lien « **About** » en haut de la page pour déclencher le point d’arrêt. Vous disposez d’un accès complet aux informations de débogage (pile des appels, variables locales, informations sur les exceptions, etc.) comme si le code s’exécutait localement.

> [!div class="nextstepaction"]
> [Appeler un autre conteneur](get-started-netcore-visualstudio-05.md)