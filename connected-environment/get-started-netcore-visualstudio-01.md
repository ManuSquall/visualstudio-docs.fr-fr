---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 1 - Installer les outils | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: b2edc476ffd4648f9ddb0e3d076f8eb400458242
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Bien démarrer avec Connected Environment et .NET Core et Visual Studio

Dans ce guide, vous allez apprendre à :

1. Créer un environnement Kubernetes dans Azure qui est optimisé pour le développement.
1. Développer de manière itérative du code dans des conteneurs en utilisant Visual Studio.
1. Développer de façon indépendante deux services distincts en utilisant la fonctionnalité de découverte du service DNS de Kubernetes pour appeler un autre service.
1. Développer et tester de façon productive votre code dans un environnement d’équipe.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Installer l’interface CLI Connected Environment
Connected Environment nécessite une installation minimale sur un ordinateur local. L’essentiel de la configuration de votre environnement de développement est stocké dans le cloud et peut être partagé avec d’autres utilisateurs.

1. Téléchargez et exécutez le [programme d’installation de l’interface CLI Connected Environment](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Obtenir les outils de débogage Kubernetes
Outre l’interface CLI Connected Environment que vous pouvez utiliser comme outil autonome, il existe des fonctionnalités évoluées comme le **débogage Kubernetes** auxquelles les développeurs .NET Core utilisant **VS Code** ou **Visual Studio** peuvent accéder.

### <a name="visual-studio-debugging"></a>Débogage Visual Studio 
1. Installer la dernière version de [Visual Studio 2017](https://www.visualstudio.com/vs/)
1. Dans le programme d’installation de Visual Studio, vérifiez que la charge de travail suivante est sélectionnée :
    * Développement web et ASP.NET
1. Installer l’[extension Visual Studio pour Connected Environment](https://aka.ms/get-vsce-visualstudio)

Nous sommes maintenant prêts à créer une application web ASP.NET avec Visual Studio.

> [!div class="nextstepaction"]
> [Créer une application web ASP.NET](get-started-netcore-visualstudio-02.md)
