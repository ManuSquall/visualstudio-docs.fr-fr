---
title: "Guide pratique pour cibler une version du .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67145a9aaaf4c01b02bc1cc6db89e375639b4fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Comment : cibler une version du .NET Framework
Ce document explique comment cibler une version de .NET Framework lorsque vous créez un projet et comment modifier la version ciblée dans un projet Visual Basic, Visual C# ou Visual F# existant.  
  
> [!IMPORTANT]
>  Pour plus d’informations sur la façon de modifier la version cible des projets C++, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
 **Dans cette rubrique**  
  
-   [Ciblage d’une version quand vous créez un projet](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Modification de la version cible](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Ciblage d’une version quand vous créez un projet  
 Lorsque vous créez un projet, la version du .NET Framework que vous ciblez détermine les modèles que vous pouvez utiliser.  
  
> [!NOTE]
>  Dans les éditions Express de Visual Studio, vous devez créer le projet en premier, et vous pouvez modifier la cible, comme indiqué dans [Modification de la version cible](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) plus loin dans cette rubrique.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Pour cibler une version lorsque vous créez un projet  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la liste située en haut de la boîte de dialogue **Nouveau projet**, choisissez la version de .NET Framework que votre projet doit cibler.  
  
    > [!NOTE]
    >  En général, une seule version de .NET Framework est installée avec Visual Studio. Si vous souhaitez cibler une autre version, vous devez d'abord vous assurer qu'elle est installée. Consultez [Vue d’ensemble du multiciblage Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Dans la liste des modèles installés, choisissez le type de projet à créer, puis nommez-le et choisissez le bouton **OK**.  
  
     La liste de modèles affiche uniquement les projets qui sont pris en charge par la version du .NET Framework que vous avez choisie.  
  
##  <a name="bkmk_existing"></a> Modification de la version cible  
 Vous pouvez modifier la version ciblée de .NET Framework dans un projet Visual Basic, Visual C# ou Visual F# en suivant cette procédure.  
  
#### <a name="to-change-the-targeted-version"></a>Pour modifier la version ciblée  
  
1.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet que vous souhaitez modifier, puis choisissez **Propriétés**.  
  
     ![Propriétés de l’Explorateur de solutions dans Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Pour plus d’informations sur la façon de modifier la version cible des projets C++, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
2.  Dans la colonne de gauche de la fenêtre Propriétés, choisissez l’onglet **Application**.  
  
     ![Onglet Application de la fenêtre de propriétés de l’application Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Après avoir créé une application UWP, vous ne pouvez pas modifier la version ciblée de Windows ou du .NET Framework.  
  
3.  Dans la liste **Framework cible**, choisissez la version que vous souhaitez.  
  
4.  Dans la boîte de dialogue de vérification qui apparaît, choisissez le bouton **Oui**.  
  
     Le projet est alors déchargé. Lorsqu'il se recharge, il cible la version du . NET Framework que vous venez de choisir.  
  
    > [!NOTE]
    >  Si votre code contient des références à une autre version du .NET Framework que celui que vous avez ciblé, des messages d'erreur peuvent s'afficher lorsque vous compilez et exécutez le code. Pour résoudre ces erreurs, vous devez modifier les références. Consultez [Dépannage des erreurs de ciblage du .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du multiciblage Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET Framework Multi-Targeting pour les projets web ASP.NET](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Dépannage des erreurs de ciblage du .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Configuration de projets](http://msdn.microsoft.com/Library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)