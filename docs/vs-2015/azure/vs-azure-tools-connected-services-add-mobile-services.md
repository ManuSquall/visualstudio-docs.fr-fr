---
title: Ajout de Mobile Services à l’aide de Services connectés
description: Ajouter Mobile Services à partir de la boîte de dialogue Ajouter des services connectés dans Visual Studio
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
ms.openlocfilehash: 0a8f6fab3c8f30834a467e2ad98843b16a9245b4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916712"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Ajout de Mobile Services à l’aide des services connectés de Visual Studio
Avec Visual Studio 2015, vous pouvez vous connecter à Azure Mobile Services à partir de la boîte de dialogue **Ajouter un service connecté** . Vous pouvez vous connecter depuis n'importe quelle application cliente C#, JavaScript, ou Cordova interplateforme. Une fois connecté, il est possible de créer et d'accéder aux données, de créer des API personnalisées, des tâches planifiées, ou encore d'ajouter la prise en charge pour les notifications Push.  Les services connectés ajoutent toutes les références et le code de connexion appropriés. Vous pouvez également profiter de la prise en charge intégrée de l'authentification d'une multitude de schémas d'identité populaires, tels que les comptes Azure AD, Facebook, Twitter et Microsoft.

## <a name="supported-project-types"></a>Types de projet pris en charge
> [!NOTE]
> Dans Visual Studio 2015, vous ne pouvez pas ajouter Azure Mobile Services à des projets Windows Universal (Windows 10) à partir de la boîte de dialogue Ajouter des services connectés. Vous pouvez le faire en installant les packages appropriés à l’aide du gestionnaire de package NuGet pour votre projet.
>
>

L’utilisation de la boîte de dialogue Services connectés vous permet de vous connecter à Azure Mobile Services pour les types de projet suivants.

* Projets d’applications Store, Phone et universelles Windows 8.1 .NET
* Projets d’applications Store, Phone et universelles Windows 8.1 JavaScript
* Projets créés à l’aide de Visual Studio Tools pour Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Connexion à Azure Mobile Services à partir de la boîte de dialogue Ajouter des services connectés
1. Assurez-vous de disposer d'un compte Azure. Si vous n’en avez pas, vous pouvez demander un [essai gratuit](https://azure.microsoft.com/pricing/free-trial/).
2. Ouvrez la boîte de dialogue **Ajouter des services connectés** .

   * Pour les applications .NET, ouvrez votre projet dans Visual Studio, ouvrez le menu contextuel du nœud **Références** dans l’Explorateur de solutions, puis choisissez **Ajouter un service connecté**.

        ![Connexion au service Azure Mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Pour les projets d’application Apache Cordova, ouvrez votre projet dans Visual Studio, ouvrez le menu contextuel du nœud du projet dans l’Explorateur de solutions, puis choisissez **Ajouter un service connecté**.
3. Dans la boîte de dialogue **Ajouter un service connecté**, choisissez **Azure Mobile Services**, puis choisissez le bouton **Configurer**. Si vous n’êtes pas encore connecté à Azure, vous serez invité à le faire.

    ![Ajout d’un service Azure Mobile Service](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Dans la boîte de dialogue **Azure Mobile Services** , choisissez un service mobile existant. Si vous devez créer un service mobile Azure, suivez la procédure ci-dessous. Sinon, passez à l'étape suivante.

    Pour créer un compte de service mobile :

   1. Cliquez sur le lien **créer un service** au bas de la boîte de dialogue.
       ![Ajouter un nouveau service connecté mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Dans la boîte de dialogue **Créer un service mobile**, choisissez un service mobile principal JavaScript ou .NET dans la liste déroulante **Runtime**.

       ![Création d’un service mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Le service principal JavaScript est simple et puissant. Si vous créez un service mobile principal JavaScript, le code JavaScript côté serveur est stocké dans le cloud, mais vous pouvez modifier les scripts serveur à l'aide de l'Explorateur de serveurs ou du portail de gestion Azure.

       Le service mobile principal .NET vous offre la puissance et la flexibilité de l’API web et d’Entity Framework. Si vous créez un service mobile principal .NET, un projet est automatiquement créé et ajouté à votre solution.
   3. Choisissez la **région** où vous souhaitez créer le service mobile, puis entrez un nom d’utilisateur et un mot de passe pour le serveur.
   4. Quand vous avez entré toutes les informations nécessaires, choisissez le bouton **Créer** pour créer le service mobile.
   5. Le nouveau service mobile doit d’afficher dans la liste des services de la boîte de dialogue **Azure Mobile Services** . Choisissez le nouveau service mobile dans la liste, puis choisissez le bouton **Ajouter** pour ajouter le service à votre projet.
5. Examinez la page Mise en route qui s'affiche pour en savoir plus sur les modifications apportés à votre projet. La page de mise en route s'affiche dans votre navigateur lorsque vous ajoutez un service connecté. Vous pouvez consulter les étapes suggérées et les exemples de code, ou bien basculer vers la page Que s'est-il passé pour voir quelles références ont été ajoutées à votre projet et comment vos fichiers de code et de configuration ont été modifiés.
6. En vous aidant des exemples de code fournis, commencez à écrire le code d’accès à votre service mobile.

## <a name="next-steps"></a>Étapes suivantes :
Posez des questions et obtenez de l’aide :

* [Forum MSDN : Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services sur le blog de l’équipe Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure Mobile Services sur azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentation Azure Mobile Services sur azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
