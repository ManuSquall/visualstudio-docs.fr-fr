---
title: Ajout de Mobile Services à l’aide de Services connectés
description: Ajouter Mobile Services à l’aide de la boîte de dialogue Ajouter un Services connectés de Visual Studio
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300182"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Ajout d’Mobile Services à l’aide de Visual Studio Services connectés
Avec Visual Studio 2015, vous pouvez vous connecter à Azure Mobile Services à l’aide de la boîte de dialogue **Ajouter un service connecté** . Vous pouvez vous connecter à C# partir d’une application cliente, d’une application JavaScript ou d’une application Cordova multiplateforme. Une fois que vous êtes connecté, vous pouvez créer des données et y accéder, créer des API personnalisées et des tâches planifiées, ou ajouter la prise en charge des notifications push.  L’opération services connectés ajoute toutes les références et le code de connexion appropriés. Vous pouvez également tirer parti de la prise en charge intégrée de l’authentification avec un large éventail de schémas d’identité populaires, tels que les comptes Azure AD, Facebook, Twitter et Microsoft.

## <a name="supported-project-types"></a>Types de projets pris en charge
> [!NOTE]
> Dans Visual Studio 2015, l’ajout de Mobile Services Azure à un projet Windows universel (Windows 10) à l’aide de la boîte de dialogue Ajouter un Services connectés n’est pas pris en charge. Vous pouvez ajouter des Mobile Services Azure en installant les packages appropriés à l’aide du gestionnaire de package NuGet pour votre projet.
>
>

Vous pouvez utiliser la boîte de dialogue Services connectés pour vous connecter à Azure Mobile Services dans les types de projets suivants.

* .NET Windows 8.1 Store, téléphone et projets d’application universelle
* JavaScript Windows 8.1 les projets de magasin, de téléphone et d’application universelle
* Projets créés à l’aide de Visual Studio Tools pour Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Se connecter à Azure Mobile Services à l’aide de la boîte de dialogue Ajouter un Services connectés
1. Vérifiez que vous disposez d’un compte Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire pour bénéficier d’une [version d’évaluation gratuite](https://go.microsoft.com/fwlink/?LinkId=518146).
2. Ouvrez la boîte de dialogue **Ajouter un services connectés** .

   * Pour les applications .NET, ouvrez votre projet dans Visual Studio, ouvrez le menu contextuel du nœud **références** dans Explorateur de solutions, puis choisissez **Ajouter un service connecté** .

        ![Connexion à Azure Mobile service](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Pour Apache Cordova projets d’application, ouvrez votre projet dans Visual Studio, ouvrez le menu contextuel du nœud de projet dans Explorateur de solutions, puis choisissez **Ajouter un service connecté**.
3. Dans la boîte de dialogue **Ajouter un service connecté**, choisissez **Azure Mobile Services**, puis choisissez le bouton **Configurer**. Vous pouvez être invité à vous connecter à Azure si vous ne l’avez pas déjà fait.

    ![Ajout d’un service mobile Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Dans la boîte de dialogue **Azure Mobile Services**, choisissez un service mobile existant si vous en avez un. Si vous avez besoin de créer un nouveau service mobile Azure, suivez la procédure ci-dessous. Sinon, passez à l'étape suivante.

    Pour créer un compte de service mobile :

   1. Choisissez le lien **Créer un service** en bas de la boîte de dialogue.
       ![ajouter un nouveau service connecté mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Dans la boîte de dialogue **créer un service mobile** , vous pouvez choisir un service mobile principal JavaScript ou un service mobile principal .net dans la liste déroulante d' **exécution** .

       ![Création d’un service mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Un service principal JavaScript est simple et puissant. Si vous créez un service mobile principal JavaScript, le code JavaScript côté serveur est stocké dans le cloud, mais vous pouvez modifier les scripts serveur à l'aide de l'Explorateur de serveurs ou du portail de gestion Azure.

       Un service mobile principal .NET vous offre toute la puissance et la flexibilité de l’API Web et de la Entity Framework. Si vous créez un service mobile principal .NET, un projet est créé pour vous et ajouté à votre solution.
   3. Choisissez la **région** où vous souhaitez créer le service mobile, puis entrez un nom d'utilisateur et un mot de passe pour le serveur.
   4. Une fois que vous avez entré toutes les informations requises, cliquez sur le bouton **Créer** pour créer le service mobile.
   5. Le nouveau service mobile doit apparaître dans la liste service de la boîte de dialogue **Mobile services Azure** . Choisissez le nouveau service mobile dans la liste, puis cliquez sur le bouton **Ajouter** pour ajouter le service à votre projet.
5. Passez en revue la page mise en route qui s’affiche et découvrez comment votre projet a été modifié. La page de mise en route s'affiche dans votre navigateur lorsque vous ajoutez un service connecté. Vous pouvez consulter les étapes suggérées et les exemples de code, ou bien basculer vers la page Que s'est-il passé pour voir quelles références ont été ajoutées à votre projet et comment vos fichiers de code et de configuration ont été modifiés.
6. En utilisant les exemples de code comme guide, commencez à écrire du code pour accéder à votre service mobile !

## <a name="how-your-project-is-modified"></a>Modifications apportées à votre projet
La façon dont Visual Studio modifie votre projet dépend du type de projet. Pour C# les applications clientes, consultez [que C# s’est-il passé – projets](https://go.microsoft.com/fwlink/p/?LinkId=513119). Pour les applications clientes JavaScript, consultez [que s’est-il passé – projets JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=513120). Pour les applications Cordova, consultez que s’est-il [passé – projets Cordova](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Étapes suivantes :
Posez des questions et recevez de l’aide :

* [Forum MSDN : Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Mobile Services Azure sur le blog de l’équipe Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Mobile Services Azure sur azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentation Azure Mobile Services sur azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
