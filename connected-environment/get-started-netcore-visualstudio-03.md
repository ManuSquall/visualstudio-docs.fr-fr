---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 3 - Créer un environnement de développement Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 01451ca57cbd4bac5c6bf08d040905b9463b15a3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Bien démarrer avec Connected Environment et .NET Core et Visual Studio

Étape précédente : [Créer une application web ASP.NET](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Créer un environnement de développement dans Azure
Avec Connected Environment, vous pouvez créer des environnements de développement Kubernetes entièrement gérés par Azure et optimisés pour le développement. En veillant à ce que le projet que nous venons de créer est ouvert, sélectionnez **Connected Environment pour AKS** dans la liste déroulante des paramètres de lancement, comme indiqué ci-dessous.

![](images/LaunchSettings.png)

Dans la boîte de dialogue qui s’affiche, vérifiez que vous êtes connecté avec le compte approprié, puis sélectionnez un environnement de développement existant ou sélectionnez **<Create New Connected Environment for AKS…>** (Créer un environnement connecté pour AKS) pour en créer un.

![](images/ConnectedEnvDialog.png)

Vous pouvez utiliser les valeurs par défaut fournies ou les modifier comme vous le souhaitez. Cliquez sur **OK** une fois que les valeurs sont définies de façon appropriée.

![](images/NewEnvDialog.png)

De retour dans la boîte de dialogue précédente, conservez pour l’instant la valeur par défaut de la liste déroulante **Space** (Espace) (`mainline`), nous reviendrons plus en détail sur ce point ultérieurement. Cochez la case **Publicly Accessible** (Accessible publiquement) de façon à rendre l’application web accessible via un point de terminaison public. Il ne s’agit pas là d’une obligation, mais cela pourra être utile pour illustrer certains concepts plus loin dans cette procédure pas à pas. Mais ne vous inquiétez pas, quoi qu’il en soit, vous pourrez déboguer votre site web à l’aide de Visual Studio.

![](images/ConnectedEnvDialog2.png)

Cliquez sur **OK** pour sélectionner ou créer l’environnement de développement. Une tâche en arrière-plan démarre ensuite pour effectuer cette opération, qui prend quelques minutes. Vous pouvez déterminer si l’opération de création est toujours en cours en plaçant votre curseur sur l’icône **Tâches en arrière-plan** dans l’angle inférieur gauche de la barre d’état (voir ci-dessous).

![](images/BackgroundTasks.png)

> [!Note]
Vous ne pouvez pas déboguer l’application tant que l’environnement de développement n’est pas créé.

## <a name="look-at-the-files-added-to-project"></a>Examiner les fichiers ajoutés au projet
En attendant que l’environnement de développement soit créé, examinons les fichiers qui ont été ajoutés au projet quand vous avez choisi d’utiliser un environnement de développement.

Tout d’abord, vous pouvez constater qu’un dossier nommé `charts` a été ajouté et qu’à l’intérieur de celui-ci, un [graphique Helm](https://docs.helm.sh) a été structuré pour votre application. Ces fichiers sont utilisés pour déployer votre application dans l’environnement de développement.

Vous remarquerez qu’un fichier nommé `Dockerfile` a été ajouté. Ce fichier contient les informations nécessaires pour empaqueter votre application dans le format Docker standard. Un fichier `HeaderPropagation.cs` est également créé, ce que nous évoquerons plus loin dans la procédure pas à pas. 

Enfin, vous noterez la présence d’un fichier nommé `vsce.yaml` qui contient les informations de configuration nécessaires à l’environnement de développement, déterminant notamment si l’application doit être accessible via un point de terminaison public.

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Déboguer un conteneur dans Kubernetes](get-started-netcore-visualstudio-04.md)