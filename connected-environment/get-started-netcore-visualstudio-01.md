---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 1 - Installer les outils | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 4f25d4ae550f47533628bf073f2f22d9ed158cab
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
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

1. Installez [Git pour Windows](https://git-scm.com/downloads), sélectionnez les options d’installation par défaut. 
1. Téléchargez **kubectl.exe** à partir de [ce lien](https://storage.googleapis.com/kubernetes-release/release/v1.9.0/bin/windows/amd64/kubectl.exe) et **enregistrez** ce fichier à un emplacement sur votre chemin (PATH).
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