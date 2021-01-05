---
title: Ajouter Azure App configuration à l’aide de Services connectés | Microsoft Docs
description: Ajouter une dépendance de service de configuration Azure à votre application à l’aide de Visual Studio Services connectés
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a0db2f2e4993fcc3c986686322b8915615758e13
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727292"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Ajout de Azure App configuration à l’aide de Visual Studio Services connectés

Dans ce didacticiel, vous allez apprendre à ajouter facilement tout ce dont vous avez besoin pour commencer à utiliser Azure App configuration pour gérer votre configuration et vos indicateurs de fonctionnalités pour les projets Web dans Visual Studio, que vous utilisiez ASP.NET Core ou n’importe quel type de projet ASP.NET. À l’aide de la fonctionnalité Services connectés dans Visual Studio, vous pouvez faire en sorte que Visual Studio ajoute automatiquement l’ensemble du code, des packages NuGet et des paramètres de configuration dont vous avez besoin pour vous connecter à votre ressource de configuration d’application dans Azure. Pour utiliser cette fonctionnalité, vous devez utiliser Visual Studio 2019 version 16,9 ou ultérieure.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Services connectés dans Visual Studio pour Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Prérequis

- Visual Studio avec la charge de travail Azure installée.
- Projet de l’un des types pris en charge

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Se connecter à la configuration de Azure App à l’aide de Services connectés

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

    ![Ajouter un service connecté Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Sous l’onglet **services connectés** , sélectionnez l’icône + pour les **dépendances de service**.

    ![Ajouter une dépendance de service](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Dans la page **Ajouter une dépendance** , sélectionnez **Azure App configuration**.

    ![Ajouter une configuration d’application](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Si vous n’êtes pas déjà connecté, connectez-vous à votre compte Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire pour bénéficier d’une [version d’évaluation gratuite](https://azure.microsoft.com/free/dotnet).

1. Dans l’écran **configurer Azure App configuration** , sélectionnez votre abonnement et un magasin de configurations existant. Sélectionnez ensuite **Suivant**.

    Si vous avez besoin de créer un magasin de configurations d’applications, passez à l’étape suivante. Sinon, passez à l’étape 6.

    ![Ajouter un compte de configuration existant au projet](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Pour créer un magasin de configuration d’application :

   1. Sélectionnez l’icône + à droite de l’en-tête **magasins de configuration d’application** . 

   1. Renseignez la boîte de dialogue Configuration de l' **Azure App : créer un nouveau** , puis sélectionnez **créer**. Notez que le champ nom de la ressource doit être unique. 

       ![Nouveau magasin de configuration d’application Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Quand la boîte de dialogue de **configuration de Azure App** s’affiche, le nouveau magasin de configuration s’affiche dans la liste. Sélectionnez ce nouveau magasin, puis sélectionnez **suivant**.

1. Entrez un nom de chaîne de connexion et indiquez si vous souhaitez que la chaîne de connexion soit stockée dans un fichier de secrets locaux ou dans [Azure Key Vault](/azure/key-vault).

   ![Spécifier la chaîne de connexion](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. L’écran **Résumé des modifications** affiche toutes les modifications qui seront apportées à votre projet si vous terminez le processus. Si les modifications semblent correctes, choisissez **Terminer**.

   ![Résumé des modifications](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Une fois le **processus de configuration de dépendance** terminé, Azure App configuration apparaît désormais sous le nœud **dépendances du service** de votre projet.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur la configuration de Azure App dans [Azure App documentation de configuration](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Voir aussi

- [Didacticiel sur l’utilisation de la configuration dynamique dans une configuration d’application connectée ASP.NET Core application](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Services connectés (Visual Studio pour Mac)](/visualstudio/mac/connected-services)