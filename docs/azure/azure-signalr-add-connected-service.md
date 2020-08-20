---
title: Ajouter Azure Signalr à l’aide de Services connectés | Microsoft Docs
description: Ajouter Azure Signalr à votre application à l’aide de Visual Studio pour ajouter un service connecté
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0e44416bd6a55796b62a7590856caab8466a6401
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643507"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Ajouter Azure Signalr à l’aide de Visual Studio Services connectés

Avec Visual Studio, vous pouvez connecter l’un des éléments suivants au service Azure Signalr à l’aide de la fonctionnalité **services connectés** :

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Connectez-vous à Azure Signalr à l’aide de Services connectés

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

1. Sous l’onglet **services connectés** , sélectionnez l’icône + pour les **dépendances de service**.

    ![Ajouter une dépendance de service](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Dans la page **Ajouter une dépendance** , sélectionnez **service Azure signalr**.

    ![Ajouter le service Azure Signalr](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Si vous n’êtes pas déjà connecté, connectez-vous à votre compte Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire pour bénéficier d’une [version d’évaluation gratuite](https://azure.microsoft.com/account/free).

1. Dans l’écran **configurer Azure signalr** , sélectionnez un composant Azure signalr existant, puis sélectionnez **suivant**.

    Si vous avez besoin de créer un nouveau composant, passez à l’étape suivante. Sinon, passez à l’étape 7.

    ![Se connecter à un composant Azure Signalr existant](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Pour créer une instance du service Azure Signalr :

   1. Sélectionnez **créer une instance de service Azure signalr** en bas de l’écran.

   1. Renseignez le **service Azure signalr : créer un** écran, puis sélectionnez **créer**.

       ![Nouvelle instance du service Azure Signalr](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Lorsque l’écran **configurer le service Azure signalr** s’affiche, la nouvelle instance s’affiche dans la liste. Sélectionnez la nouvelle instance dans la liste, puis sélectionnez **suivant**.

1. Entrez un nom de chaîne de connexion ou choisissez la valeur par défaut, et indiquez si vous souhaitez que la chaîne de connexion soit stockée dans un fichier de secrets locaux ou dans [Azure Key Vault](/azure/key-vault).

   ![Spécifier la chaîne de connexion](./media/azure-signalr-add-connected-service/connection-string.png)

1. L’écran **Résumé des modifications** affiche toutes les modifications qui seront apportées à votre projet si vous terminez le processus. Si les modifications semblent correctes, choisissez **Terminer**.

   ![Résumé des modifications](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. La connexion s’affiche sous la section **dépendances du service** de l’onglet **services connectés** .

   ![Dépendances de services](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Voir aussi

- [Page du produit Azure Signalr](https://azure.microsoft.com/services/signalr-service/)
- [Documentation Azure SignalR Service](/azure/azure-signalr)
- [Services connectés (Visual Studio pour Mac)](/visualstudio/mac/connected-services)
