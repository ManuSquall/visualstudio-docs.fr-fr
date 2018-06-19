---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 4 - Déboguer un conteneur dans Kubernetes | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31886190"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Bien démarrer avec Connected Environment et .NET Core et Visual Studio

Étape précédente : [Créer un environnement de développement dans Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Déboguer un conteneur dans Kubernetes
Une fois que l’environnement de développement a été créé, vous pouvez déboguer l’application. Définissez un point d’arrêt dans le code, par exemple à la ligne 20 dans le fichier `HomeController.cs` où la variable `Message` est définie. Cliquez sur **F5** pour commencer le débogage. 

Visual Studio communique avec l’environnement de développement pour générer et déployer l’application et ouvrir ensuite un navigateur dans lequel l’application web s’exécute. Vous pouvez penser que le conteneur s’exécute localement, mais en réalité, il s’exécute dans notre environnement de développement dans Azure. La présence de l’adresse localhost s’explique par le fait que Connected Environment crée un tunnel SSH temporaire vers le conteneur en cours d’exécution dans Azure.

Cliquez sur le lien « **About** » en haut de la page pour déclencher le point d’arrêt. Vous disposez d’un accès complet aux informations de débogage (pile des appels, variables locales, informations sur les exceptions, etc.) comme si le code s’exécutait localement.

> [!div class="nextstepaction"]
> [Appeler un autre conteneur](get-started-netcore-visualstudio-05.md)