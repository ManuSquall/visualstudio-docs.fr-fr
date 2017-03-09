---
title: "Comment&#160;: cibler une version du .NET&#160;Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cibler la version du .NET Framework (Visual Studio)"
  - "versions (Visual Studio), cibler la version du .NET Framework"
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 50
caps.handback.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comment&#160;: cibler une version du .NET&#160;Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document explique comment cibler une version de .NET Framework lorsque vous créez un projet et comment modifier la version ciblée dans un projet Visual Basic, Visual C\# ou Visual F\# existant.  
  
> [!IMPORTANT]
>  Pour plus d'informations sur la façon de modifier la version cible des projets C\+\+, voir [comment : modifier la version cible de .Net Framework et l'ensemble d'outils de la plateforme](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md).  
  
 **Dans cette rubrique**  
  
-   [Ciblage d'une version lorsque vous créez un projet](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Modification de la version cible](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Ciblage d'une version lorsque vous créez un projet  
 Lorsque vous créez un projet, la version du .NET Framework que vous ciblez détermine les modèles que vous pouvez utiliser.  
  
> [!NOTE]
>  Dans les éditions Express de Visual Studio, vous devez créer le projet en premier, et vous pouvez modifier la cible, comme indiqué dans [Modification de la version cible](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) plus loin dans cette rubrique.  
  
#### Pour cibler une version lorsque vous créez un projet  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la liste située en haut de la boîte de dialogue **Nouveau projet**, choisissez la version de .NET Framework que votre projet doit cibler.  
  
    > [!NOTE]
    >  En général, une seule version de .NET Framework est installée avec Visual Studio.  Si vous souhaitez cibler une autre version, vous devez d'abord vous assurer qu'elle est installée.  Consultez [Vue d'ensemble du multi\-ciblage Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Dans la liste des modèles installés, choisissez le type de projet à créer, puis nommez\-le et choisissez le bouton **OK**.  
  
     La liste de modèles affiche uniquement les projets qui sont pris en charge par la version du .NET Framework que vous avez choisie.  
  
##  <a name="bkmk_existing"></a> Modification de la version cible  
 Vous pouvez modifier la version ciblée de .NET Framework dans un projet Visual Basic, Visual C\# ou Visual F\# en suivant cette procédure.  
  
#### Pour modifier la version ciblée  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet que vous souhaitez modifier, puis choisissez **Propriétés**.  
  
     ![Propriétés de l'Explorateur de solutions dans Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs\_slnExplorer\_Properties")  
  
    > [!IMPORTANT]
    >  Pour plus d'informations sur la façon de modifier la version cible des projets C\+\+, voir [comment : modifier la version cible de .Net Framework et l'ensemble d'outils de la plateforme](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md).  
  
2.  Dans la colonne de gauche de la fenêtre Propriétés, choisissez l'onglet **Application**.  
  
     ![Onglet Propriétés de la fenêtre Propriétés de l'application Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs\_slnExplorer\_Properties\_ApplicationTab")  
  
    > [!NOTE]
    >  Après avoir créé une application du Windows Store, vous ne pouvez pas modifier la version ciblée de Windows ou du .NET Framework.  
  
3.  Dans la liste **Framework cible**, choisissez la version que vous souhaitez.  
  
4.  Dans la boîte de dialogue de vérification qui apparaît, choisissez le bouton **Oui**.  
  
     Le projet est alors déchargé.  Lorsqu'il se recharge, il cible la version du . NET Framework que vous venez de choisir.  
  
    > [!NOTE]
    >  Si votre code contient des références à une autre version du .NET Framework que celui que vous avez ciblé, des messages d'erreur peuvent s'afficher lorsque vous compilez et exécutez le code.  Pour résoudre ces erreurs, vous devez modifier les références.  Consultez [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## Voir aussi  
 [Vue d'ensemble du multi\-ciblage Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET Framework Multi\-Targeting for ASP.NET Web Projects](../Topic/.NET%20Framework%20Multi-Targeting%20for%20ASP.NET%20Web%20Projects.md)   
 [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Page Application, Concepteur de projets \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Page Application, Concepteur de projets \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)   
 [comment : modifier la version cible de .Net Framework et l'ensemble d'outils de la plateforme](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)