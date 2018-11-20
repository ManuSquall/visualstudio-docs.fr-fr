---
title: Création d’un projet de service cloud Azure avec Visual Studio | Microsoft Docs
description: Apprenez dès maintenant à créer un projet de service cloud Azure avec Visual Studio
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002060"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Création d’un projet de service cloud Azure avec Visual Studio
Azure Tools pour Visual Studio fournit un modèle de projet qui vous permet de créer un [service cloud Azure](/azure/cloud-services/cloud-services-choose-me), qui est un simple service Azure à usage général. Une fois que le projet a été créé, Visual Studio vous permet de configurer, déboguer, et déployer le service cloud dans Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Étapes de création d’un projet de service cloud Azure dans Visual Studio
Cette section vous explique comment créer un projet de service cloud Azure dans Visual Studio avec un ou plusieurs rôles web.  

1. Démarrez Visual Studio en tant qu’administrateur.

1. Dans le menu principal, sélectionnez **fichier** > **New** > **projet**.

1. Sélectionnez **Cloud** à partir de l’élément visuel C# ou Visual Basic nœuds du modèle de projet, puis sélectionnez **Azure Cloud Service** à partir de la liste des modèles.

    ![Nouveau service cloud Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Spécifier la version du .NET Framework que vous souhaitez utiliser pour développer votre projet.

1. Entrez un nom et un emplacement pour votre projet et un nom pour la solution. 

1. Sélectionnez **OK**.

1. Dans le **nouveau Microsoft Azure Cloud Service** boîte de dialogue, sélectionnez les rôles que vous souhaitez ajouter, puis choisissez le bouton de flèche droite pour les ajouter à votre solution.

    ![Sélectionnez les nouveaux rôles de service cloud Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Pour renommer un rôle que vous avez ajouté, placez le curseur sur le rôle dans le **nouveau Microsoft Azure Cloud Service** boîte de dialogue, puis, dans le menu contextuel, sélectionnez **renommer**. Vous pouvez également renommer un rôle au sein de votre solution (dans le **l’Explorateur de solutions**) après avoir été ajoutée.

    ![Renommer le rôle de service cloud Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Le projet Azure Visual Studio est associé aux projets de rôle de la solution. Le projet comprend également le *fichier de définition de service* et *fichier de configuration de service*:

- **Fichier de définition de service** -définit les paramètres d’exécution pour votre application, notamment les rôles requis, points de terminaison et taille de machine virtuelle. 
- **Fichier de configuration de service** -configure le nombre d’instances d’un rôle sont exécutées et les valeurs des paramètres définis pour un rôle. 

Pour plus d’informations sur ces fichiers, consultez [configurer les rôles pour un service cloud Azure avec Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Étapes suivantes
- [Gestion des rôles dans les projets de service cloud Azure avec Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
