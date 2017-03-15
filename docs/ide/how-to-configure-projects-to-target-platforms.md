---
title: "Comment&#160;: configurer des projets pour des plateformes cibles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "64 bits (Visual Studio)"
  - "applications 64 bits (Visual Studio)"
  - "programmation 64 bits (Visual Studio)"
  - "unités centrales, cibler spécifiquement"
  - "plateformes, cibler des unités centrales spécifiques"
  - "propriétés de projet (Visual Studio), cibler des plateformes"
  - "paramètres du projet (Visual Studio), cibler des plateformes"
  - "projets (Visual Studio), cibler des plateformes"
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comment&#160;: configurer des projets pour des plateformes cibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de configurer vos applications pour cibler différentes plateformes \(y compris des plateformes 64 bits\).  Pour plus d'informations sur la prise en charge des plateformes 64 bits dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Applications 64 bits](../Topic/64-bit%20Applications.md).  
  
## Ciblage de plateformes avec le Gestionnaire de configurations  
 Le **Gestionnaire de configurations** vous offre un moyen d'ajouter rapidement une nouvelle plateforme à cibler avec votre projet  Si vous sélectionnez l'une des plateformes incluses avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les propriétés de votre projet sont modifiées afin de générer votre projet pour la plateforme sélectionnée.  
  
#### Pour configurer un projet pour cibler une plateforme 64 bits  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**.  
  
2.  Dans la liste **Plateforme de la solution active**, choisissez une plateforme 64 bits pour la solution à cibler, puis choisissez le bouton **Fermer**.  
  
    1.  Si la plateforme voulue ne s'affiche pas dans la liste **Plateforme de la solution active**, choisissez **Nouveau**.  
  
         La boîte de dialogue **Nouvelle plateforme de solution** s'affiche.  
  
    2.  Dans la liste **Tapez ou sélectionnez la nouvelle plateforme**, choisissez **x64**.  
  
        > [!NOTE]
        >  Si vous affectez un nouveau nom à votre configuration, vous devrez peut\-être modifier les paramètres dans le **Concepteur de projets** pour cibler la plateforme correcte.  
  
    3.  Si vous souhaitez copier les paramètres d'une configuration de plateforme actuelle, choisissez\-la, puis choisissez le bouton **OK**.  
  
 Les propriétés de tous les projets qui ciblent la plateforme 64 bits sont mises à jour et la prochaine génération du projet est optimisée pour les plateformes 64 bits.  
  
## Ciblage de plateformes dans le Concepteur de projets  
 Le Concepteur de projets permet également de cibler différentes plateformes avec votre projet.  Si la sélection de l'une des plateformes incluses dans la liste dans la boîte de dialogue **Nouvelle plateforme de solution** ne fonctionne pas pour votre solution, vous pouvez créer un nom de configuration personnalisée, puis en modifier les paramètres dans le **Concepteur de projets** en fonction de la plateforme voulue.  
  
 L'exécution de cette tâche varie suivant le langage de programmation que vous utilisez.  Pour plus d'informations, consultez les liens suivants :  
  
-   Pour les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], consultez [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Pour les projets [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], consultez [Générer, page du Concepteur de projets \(C\#\)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Pour les projets [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)], consultez [\/clr \(Compilation pour le Common Language Runtime\)](/visual-cpp/build/reference/clr-common-language-runtime-compilation).  
  
## Voir aussi  
 [Présentation des plateformes de générations](../ide/understanding-build-platforms.md)   
 [\/platform \(Specify Output Platform\)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [Applications 64 bits](../Topic/64-bit%20Applications.md)   
 [Prise en charge de l'IDE de Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)