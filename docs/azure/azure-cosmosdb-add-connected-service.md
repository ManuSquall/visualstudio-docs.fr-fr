---
title: Ajouter des CosmosDB Azure à l’aide de Services connectés | Microsoft Docs
description: Ajouter la prise en charge d’Azure CosmosDB à votre application à l’aide de Visual Studio pour ajouter un service connecté
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2d23081f541fbc12581450c60c6eb4b09f20c64a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643526"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Ajoutez Azure Cosmos DB à votre application à l’aide de Visual Studio Services connectés

Avec Visual Studio, vous pouvez connecter l’un des éléments suivants à Azure Cosmos DB à l’aide de la fonctionnalité **services connectés** :

- Application console .NET Framework
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (y compris l’application console, WPF, Windows Forms, bibliothèque de classes)
- Rôle de travail .NET Core
- Azure Functions
- Application plateforme Windows universelle
- Xamarin
- Cordova

La fonctionnalité de service connecté ajoute l’ensemble des références et du code de connexion nécessaires à votre projet, et modifie vos fichiers de configuration de manière appropriée.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Services connectés dans Visual Studio pour Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prérequis

- Visual Studio avec la charge de travail Azure installée.
- Projet de l’un des types pris en charge

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Se connecter à Azure Cosmos DB à l’aide de Services connectés

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

1. Sous l’onglet **services connectés** , sélectionnez l’icône + pour les **dépendances de service**.

    ![Ajouter une dépendance de service](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Dans la page **Ajouter une dépendance** , sélectionnez **Azure Cosmos DB**.

    ![Ajouter Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Si vous n’êtes pas déjà connecté, connectez-vous à votre compte Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire pour bénéficier d’une [version d’évaluation gratuite](https://azure.microsoft.com/account/free).

1. Dans l’écran **Azure Cosmos DB** , sélectionnez un Azure Cosmos DB existant, puis sélectionnez **suivant**.

    Si vous avez besoin de créer une base de données, passez à l’étape suivante. Sinon, passez à l’étape 7.

    ![Ajouter des Cosmos DB existants au projet](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Pour créer un Azure Cosmos DB :

   1. Sélectionnez **créer un nouveau Azure Cosmos DB** en bas de l’écran.

   1. Renseignez le **Azure Cosmos DB : créer un** écran, puis sélectionnez **créer**.

       ![Nouvelle Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Quand la boîte de dialogue **configurer Azure Cosmos DB** s’affiche, la nouvelle base de données s’affiche dans la liste. Sélectionnez la nouvelle base de données dans la liste, puis sélectionnez **suivant**.

1. Entrez un nom de chaîne de connexion et indiquez si vous souhaitez que la chaîne de connexion soit stockée dans un fichier de secrets locaux ou dans [Azure Key Vault](/azure/key-vault).

   ![Spécifier la chaîne de connexion](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. L’écran **Résumé des modifications** affiche toutes les modifications qui seront apportées à votre projet si vous terminez le processus. Si les modifications semblent correctes, choisissez **Terminer**.

   ![Résumé des modifications](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. La connexion s’affiche sous la section **dépendances du service** de l’onglet **services connectés** .

   ![Dépendances de services](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Voir aussi

- [Page Azure Cosmos DB produit](https://azure.microsoft.com/services/cosmos-db/)
- [Documentation Azure Cosmos DB](/azure/cosmos-db/)
- [Services connectés (Visual Studio pour Mac)](/visualstudio/mac/connected-services)
