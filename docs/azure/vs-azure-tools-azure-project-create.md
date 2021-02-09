---
title: Créer un projet de service cloud Azure
description: Apprenez dès maintenant à créer un projet de service cloud Azure avec Visual Studio
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: d652172bde2ecd3aea4bb027e46173eaa5fe7b17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844500"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Créer un projet de service cloud Azure avec Visual Studio

Visual Studio fournit un modèle de projet qui vous permet de créer un [service Cloud Azure](/azure/cloud-services/cloud-services-choose-me), qui est un service Azure simple à usage général. Une fois le projet créé, Visual Studio vous permet de configurer, déboguer et déployer le service cloud dans Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Étapes pour créer un projet de service cloud Azure dans Visual Studio
Cette section vous guide dans le processus de création d’un projet de service cloud Azure dans Visual Studio avec un ou plusieurs rôles web.

::: moniker range="vs-2017"
1. Ouvrez Visual Studio en tant qu’administrateur.

1. Dans le menu principal, sélectionnez **Fichier** > **Nouveau** > **Projet**.

1. Sélectionnez **Cloud** à partir des nœuds de modèles de projets Visual C# ou Visual Basic , puis sélectionnez **Service cloud Azure** dans la liste des modèles.

    ![Nouveau service cloud Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Spécifiez la version de .NET Framework que vous souhaitez utiliser pour développer votre projet.

1. Entrez un nom et un emplacement pour votre projet et un nom pour la solution.

1. Sélectionnez **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

1. Dans la zone de recherche, tapez *Cloud*, puis choisissez **Azure Cloud Service**.

   ![Nouveau service cloud Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Nommez le projet et choisissez **Créer**.

   ![Nommer le projet](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. Dans la boîte de dialogue **Nouveau service cloud Microsoft Azure**, sélectionnez les rôles que vous souhaitez ajouter et appuyez sur la touche de direction droite pour les ajouter à votre solution.

    ![Sélectionner de nouveaux rôles de service cloud Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Pour renommer un rôle que vous avez ajouté, passez la souris sur le rôle dans la boîte de dialogue **Nouveau service cloud Microsoft Azure**, puis, dans le menu contextuel, sélectionnez **Renommer**. Vous pouvez également renommer un rôle dans votre solution (dans **l’Explorateur de solutions**) une fois qu’il a été ajouté.

    ![Renommer un rôle de service cloud Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Le projet Azure Visual Studio est associé aux projets de rôle de la solution. Le projet comprend également le *fichier de définition de service* et le *fichier de configuration de service* :

- **Fichier de définition de service** : définit les paramètres d’exécution de votre application, notamment les rôles nécessaires, les points de terminaison et la taille de la machine virtuelle.
- **Fichier de configuration de service** : configure le nombre d’instances d’un rôle exécutées et les valeurs des paramètres définis pour un rôle.

Pour plus d’informations sur ces fichiers, consultez [configurer les rôles pour un service Cloud Azure avec Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Étapes suivantes
- [Gestion des rôles dans les projets de service cloud Azure avec Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
