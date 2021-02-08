---
title: Ajouter le cache Azure pour les ReDim à l’aide de Services connectés | Microsoft Docs
description: Ajouter le cache Azure pour la prise en charge d’Redims à votre application à l’aide de Visual Studio pour ajouter un service connecté
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: dd08cc9cc44b0866d718fe03392e99d5fa6467b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841171"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Ajouter le cache Azure pour les éléments ReDim à l’aide de Visual Studio Services connectés

Avec Visual Studio, vous pouvez connecter l’un des éléments suivants à Azure cache pour les opérations ReDim à l’aide de la fonctionnalité **services connectés** :

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Se connecter au cache Azure pour les ReDim à l’aide de Services connectés

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

1. Sous l’onglet **services connectés** , sélectionnez l’icône + pour les **dépendances de service**.

    ![Ajouter une dépendance de service](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Dans la page **Ajouter une dépendance** , sélectionnez **cache Azure pour redims**.

    ![Ajouter Azure Cache pour Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Si vous n’êtes pas déjà connecté, connectez-vous à votre compte Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire pour bénéficier d’une [version d’évaluation gratuite](https://azure.microsoft.com/account/free).

1. Dans l’écran **configurer le cache Azure pour les redims** , sélectionnez un cache Azure existant pour les ReDim, puis sélectionnez **suivant**.

    Si vous avez besoin de créer un nouveau composant, passez à l’étape suivante. Sinon, passez à l’étape 7.

    ![Se connecter à un cache Azure existant pour les ReDim](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Pour créer un cache Redims Azure :

   1. Sélectionnez **créer un nouveau cache redims Azure** en bas de l’écran.

   1. Remplissez le **cache Azure pour les éléments ReDim : créer un** écran, puis sélectionnez **créer**.

       ![Nouveau cache Azure pour les ReDim](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Lorsque l’écran **configurer le cache Azure pour les redims** s’affiche, le nouveau cache s’affiche dans la liste. Sélectionnez la nouvelle base de données dans la liste, puis sélectionnez **suivant**.

1. Entrez un nom de chaîne de connexion ou choisissez la valeur par défaut, et indiquez si vous souhaitez que la chaîne de connexion soit stockée dans un fichier de secrets locaux ou dans [Azure Key Vault](/azure/key-vault).

   ![Spécifier la chaîne de connexion](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. L’écran **Résumé des modifications** affiche toutes les modifications qui seront apportées à votre projet si vous terminez le processus. Si les modifications semblent correctes, choisissez **Terminer**.

   ![Résumé des modifications](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. La connexion s’affiche sous la section **dépendances du service** de l’onglet **services connectés** .

   ![Dépendances de services](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Voir aussi

- [Page du produit cache Azure pour Redims](https://azure.microsoft.com/services/cache)
- [Documentation sur Azure Cache pour Redis](/azure/azure-cache-for-redis/)
- [Services connectés (Visual Studio pour Mac)](/visualstudio/mac/connected-services)