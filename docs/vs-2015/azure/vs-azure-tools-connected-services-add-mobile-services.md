---
title: Ajout de Mobile Services à l’aide des Services connectés dans Visual Studio | Microsoft Docs
description: Ajouter Mobile Services à l’aide de la boîte de dialogue Ajouter des Services connectés Visual Studio
documentationcenter: na
author: ghogen
manager: douge
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 1679f8e20c4516ab64c4358229b4eec6ab5029ba
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001983"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Ajout de Mobile Services à l’aide des Services connectés Visual Studio
Visual Studio 2015, vous pouvez vous connecter à Azure Mobile Services à l’aide du **ajouter un Service connecté** boîte de dialogue. Vous pouvez vous connecter à partir d’un C# application cliente, toute application JavaScript ou inter-plateformes Cordova. Une fois que vous vous connectez, vous pouvez créer et accéder aux données, créer des API personnalisées et des travaux planifiés ou ajouter la prise en charge pour les notifications push.  Les services connectés ajoutent toutes les références appropriées et code de connexion. Vous pouvez également tirer parti de la prise en charge intégrée pour l’authentification avec un large éventail de systèmes d’identité populaires, tels qu’Azure AD, Facebook, Twitter et Microsoft Accounts.

## <a name="supported-project-types"></a>Types de projet pris en charge
> [!NOTE]
> Ajout d’Azure Mobile Services à un projet Windows universel (Windows 10) à l’aide de la boîte de dialogue Ajouter des Services connectés dans Visual Studio 2015, n’est pas pris en charge. Vous pouvez ajouter des Services mobiles Azure en installant les packages appropriés à l’aide du Gestionnaire de Package NuGet pour votre projet.
> 
> 

Vous pouvez utiliser la boîte de dialogue Services connectés pour se connecter à Azure Mobile Services dans les types de projet suivants.

* Projets .NET Windows 8.1 Store, Phone et application universelle
* Projets JavaScript Windows 8.1 Store, Phone et application universelle
* Projets créés à l’aide de Visual Studio Tools pour Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Se connecter à Azure Mobile Services à l’aide de la boîte de dialogue Ajouter des Services connectés
1. Assurez-vous que vous avez un compte Azure. Si vous n’avez pas un compte Azure, vous pouvez vous inscrire pour un [version d’évaluation gratuite](http://go.microsoft.com/fwlink/?LinkId=518146).
2. Ouvrez le **ajouter des Services connectés** boîte de dialogue.
   
   * Pour les applications .NET, ouvrez votre projet dans Visual Studio, ouvrez le menu contextuel pour le **références** nœud dans l’Explorateur de solutions, puis choisissez **ajouter un Service connecté**
     
        ![Connexion au Service Mobile Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Pour les projets d’application Apache Cordova, ouvrez votre projet dans Visual Studio, ouvrez le menu contextuel du nœud de projet dans l’Explorateur de solutions, puis choisissez **ajouter un Service connecté**.
3. Dans le **ajouter un Service connecté** boîte de dialogue, sélectionnez **Azure Mobile Services**, puis choisissez le **configurer** bouton. Vous pouvez être invité à se connecter à Azure si vous n’avez pas déjà fait.
   
    ![Ajout d’un Service Mobile Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Dans le **Azure Mobile Services** boîte de dialogue, sélectionnez un service mobile existant si vous en avez pas. Si vous avez besoin créer un nouveau service mobile Azure, suivez la procédure ci-dessous pour le faire. Sinon, passez à l'étape suivante.
   
    Pour créer un nouveau compte de service mobile :
   
   1. Choisissez le ** créer un Service ** lien en bas de la boîte de dialogue.
       ![Ajouter un service connecté mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Sur le **créer un Service Mobile** boîte de dialogue, vous pouvez choisir un service mobile de backend JavaScript, ou un service mobile de backend .NET à partir de la **Runtime** liste déroulante. 
      
       ![Création d’un service mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)
      
       Un service principal JavaScript est simple et puissante. Si vous créez un service mobile de backend JavaScript, le code JavaScript côté serveur est stocké dans le cloud, mais vous pouvez modifier les scripts serveur à l’aide de l’Explorateur de serveurs ou le portail de gestion Azure. 
      
       Un service mobile de backend .NET vous offre la puissance et la flexibilité de l’API Web et Entity Framework. Si vous créez un service mobile de backend .NET, un projet est créé pour vous et ajouté à votre solution. 
   3. Choisissez le **région** où vous souhaitez que le service mobile et puis entrez un nom d’utilisateur et le mot de passe pour le serveur.
   4. Une fois que vous avez entré toutes les informations requises, choisissez le **créer** bouton permettant de créer le service mobile.
   5. Le nouveau service mobile doit apparaître dans la liste des services sur le **Azure Mobile Services** boîte de dialogue. Choisissez le nouveau service mobile dans la liste, puis le **ajouter** pour ajouter le service à votre projet.
5. Passez en revue la page de démarrage qui s’affiche et de quelle manière votre projet a été modifié. Chaque fois que vous ajoutez un service connecté, une page mise en route s’affiche dans votre navigateur. Vous pouvez consulter les étapes suggérées et les exemples de code, ou basculez vers la page que s’est-il passé pour voir quelles références ont été ajoutés à votre projet, et comment vos fichiers de code et la configuration ont été modifiés.
6. Appuyez-vous sur les exemples de code, commencez à écrire du code pour accéder à votre service mobile !

## <a name="how-your-project-is-modified"></a>Comment votre projet est modifié
Visual Studio modifie votre projet varie selon le type de projet. Pour C# les applications clientes, consultez [que s’est-il passé – C# projets](http://go.microsoft.com/fwlink/p/?LinkId=513119). Pour les applications clientes JavaScript, consultez [que s’est-il passé – projets JavaScript](http://go.microsoft.com/fwlink/p/?LinkId=513120). Pour les applications Cordova, consultez [que s’est-il passé – projets de Cordova](http://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Étapes suivantes
Posez des questions et obtenir de l’aide : 

* [Forum MSDN : Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services sur le Blog de l’équipe Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure Mobile Services sur azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentation Azure Mobile Services sur azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)

