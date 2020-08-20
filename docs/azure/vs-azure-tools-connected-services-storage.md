---
title: Ajouter le Stockage Azure à l’aide des Services connectés | Microsoft Docs
description: Ajoutez une dépendance de service de stockage Azure à votre application à l’aide de Visual Studio Services connectés
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: 4a1b7bcc8b95b30ea3737dc2561c5abb280e2b5c
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88639425"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Ajout de stockage Azure à l’aide des services connectés de Visual Studio

Avec Visual Studio, vous pouvez connecter l’un des éléments suivants au stockage Azure à l’aide de la fonctionnalité **services connectés** :

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

## <a name="connect-to-azure-storage-using-connected-services"></a>Se connecter au stockage Azure à l’aide de Services connectés

::: moniker range="vs-2017"

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

    ![Ajouter un service connecté Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Sur la page **Services connectés**, sélectionnez **Stockage cloud avec le Stockage Azure**.

    ![Ajouter le Stockage Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Dans la boîte de dialogue **Stockage Azure**, sélectionnez un compte de stockage existant, puis sélectionnez **Ajouter**.

    Si vous devez créer un compte de stockage, passez à l’étape suivante. Sinon, passez à l’étape 6.

    ![Ajouter un compte de stockage existant au projet](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Pour créer un compte de stockage :

   1. Sélectionnez **Créer un compte de stockage** au bas de la boîte de dialogue.

   1. Renseignez les informations demandées dans la boîte de dialogue **Créer un compte de stockage**, puis sélectionnez **Créer**.

       ![Nouveau compte de stockage Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Lorsque la boîte de dialogue **Stockage Azure** apparaît, le nouveau compte de stockage s’affiche dans la liste. Sélectionnez le nouveau compte de stockage dans la liste, puis **Ajouter**.

1. Le service connecté de stockage s’affiche sous le nœud **Références de service** de votre projet.
:::moniker-end

:::moniker range=">=vs-2019"

1. Ouvrez votre projet dans Visual Studio.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **services connectés** et, dans le menu contextuel, sélectionnez **Ajouter un service connecté**.

    ![Ajouter un service connecté Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Sous l’onglet **services connectés** , sélectionnez l’icône + pour les **dépendances de service**.

    ![Ajouter une dépendance de service](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Dans la page **Ajouter une dépendance** , sélectionnez **stockage Azure**.

    ![Ajouter le Stockage Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Si vous n’êtes pas déjà connecté, connectez-vous à votre compte Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire pour bénéficier d’une [version d’évaluation gratuite](https://azure.microsoft.com/account/free).

1. Dans l’écran **configurer le stockage Azure** , sélectionnez un compte de stockage existant, puis sélectionnez **suivant**.

    Si vous devez créer un compte de stockage, passez à l’étape suivante. Sinon, passez à l’étape 6.

    ![Ajouter un compte de stockage existant au projet](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Pour créer un compte de stockage :

   1. Sélectionnez **créer un compte de stockage** au bas de la boîte de dialogue.

   1. Renseignez la boîte de dialogue **stockage Azure : créer** , puis sélectionnez **créer**.

       ![Nouveau compte de stockage Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Lorsque la boîte de dialogue **Stockage Azure** apparaît, le nouveau compte de stockage s’affiche dans la liste. Sélectionnez le nouveau compte de stockage dans la liste, puis sélectionnez **suivant**.

1. Entrez un nom de chaîne de connexion et indiquez si vous souhaitez que la chaîne de connexion soit stockée dans un fichier de secrets locaux ou dans [Azure Key Vault](/azure/key-vault).

   ![Spécifier la chaîne de connexion](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. L’écran **Résumé des modifications** affiche toutes les modifications qui seront apportées à votre projet si vous terminez le processus. Si les modifications semblent correctes, choisissez **Terminer**.

   ![Résumé des modifications](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Le service connecté de stockage s’affiche sous le nœud **Références de service** de votre projet.
:::moniker-end

## <a name="see-also"></a>Voir aussi

- [Forum Internet du Stockage Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Documentation sur le stockage Azure](/azure/storage/)
- [Services connectés (Visual Studio pour Mac)](/visualstudio/mac/connected-services)
