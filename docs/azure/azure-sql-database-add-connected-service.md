---
title: Ajouter une connexion à Azure SQL Database | Microsoft Docs
description: Ajoutez Azure SQL Database connexion à votre application à l’aide de Visual Studio Services connectés
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 26a01bfe2a34422f9596710f832a1c4af699fd3b
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588486"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Ajouter une connexion à Azure SQL Database

Avec Visual Studio, vous pouvez connecter l’un des éléments suivants à Azure SQL Database à l’aide de la fonctionnalité **services connectés** :

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Se connecter à Azure SQL Database à l’aide de Services connectés

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

1. Sous l’onglet **services connectés** , sélectionnez l’icône + pour les **dépendances de service**.

    ![Ajouter une dépendance de service](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Dans la page **Ajouter une dépendance** , sélectionnez **Azure SQL Database**.

    ![Ajouter Azure SQL Database Service](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Si vous n’êtes pas déjà connecté, connectez-vous à votre compte Azure. Si vous n’en avez pas, vous pouvez demander un [essai gratuit](https://azure.microsoft.com/account/free).

1. Dans l’écran **configurer l’Azure SQL Database** , sélectionnez un Azure SQL Database existant, puis sélectionnez **suivant**.

    Si vous avez besoin de créer un nouveau composant, passez à l’étape suivante. Sinon, passez à l’étape 7.

    ![Se connecter à un composant de Azure SQL Database existant](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Pour créer un Azure SQL Database :

   1. Sélectionnez **créer un SQL Database** en bas de l’écran.

   1. Renseignez le **Azure SQL Database : créer un** écran, puis sélectionnez **créer**.

       ![Nouvelle Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Lorsque l’écran **configurer Azure SQL Database** s’affiche, la nouvelle base de données s’affiche dans la liste. Sélectionnez la nouvelle base de données dans la liste, puis sélectionnez **suivant**.

1. Entrez un nom de chaîne de connexion ou choisissez la valeur par défaut, et indiquez si vous souhaitez que la chaîne de connexion soit stockée dans un fichier de secrets locaux ou dans [Azure Key Vault](/azure/key-vault).

   ![Spécifier la chaîne de connexion](./media/azure-sql-database-add-connected-service/connection-string.png)

1. L’écran **Résumé des modifications** affiche toutes les modifications qui seront apportées à votre projet si vous terminez le processus. Si les modifications semblent correctes, choisissez **Terminer**.

   ![Résumé des modifications](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Si vous êtes invité à définir des règles de pare-feu, choisissez **Oui**.

   ![Règles de pare-feu](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. La connexion s’affiche sous la section **dépendances du service** de l’onglet **services connectés** .

   ![Dépendances de services](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Voir aussi

- [Page Azure SQL Database produit](https://azure.microsoft.com/services/sql-database/)
- [Documentation Azure SQL Database](/azure/azure-sql/database/)
- [Services connectés (Visual Studio pour Mac)](/visualstudio/mac/connected-services)
