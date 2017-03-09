---
title: "Proc&#233;dure&#160;: Mise &#224; niveau de projets Visual C++ vers Visual Studio&#160;2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets [C++], mettre à niveau"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: Mise &#224; niveau de projets Visual C++ vers Visual Studio&#160;2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous ouvrez pour la première fois un projet Visual C\+\+ créé dans une version antérieure de Visual Studio, vous pouvez être invité à le mettre à jour. Le message vous demande si vous souhaitez effectuer une mise à niveau vers la version la plus récente du compilateur et des bibliothèques Visual C\+\+. Les options de mise à niveau dépendent de la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui a été utilisée pour créer le projet.  
  
 Vous pouvez utiliser [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] pour ouvrir, modifier et générer des projets [!INCLUDE[win8](../debugger/includes/win8_md.md)] créés dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], mais pour créer un projet [!INCLUDE[win8](../debugger/includes/win8_md.md)], vous devez utiliser [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. \(Pour créer un projet [!INCLUDE[win81](../debugger/includes/win81_md.md)], vous devez utiliser [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].\)  
  
 Pour créer un projet Windows 10, vous devez utiliser [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)].  
  
 Si vous n’êtes pas invité à effectuer une mise à jour, vous n’aurez rien à faire pour améliorer le projet. Pour plus d’informations, consultez [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Si le projet \(.vcproj\) a été créé dans une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui est plus ancienne que [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], vous devez mettre à jour le projet.  
  
-   Si le projet \(.vcxproj\) a été créé dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ou [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], vous disposez de deux options :  
  
    -   Vous pouvez ignorer la mise à jour.[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] chargera le projet sans effectuer de modification s’il a accès aux outils Visual C\+\+ dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] avec SP1, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ou [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]. Vous pouvez fournir cet accès en installant la version de Visual Studio avec laquelle le projet a été créé sur le même ordinateur doté de [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)]. Pour plus d’informations, consultez [Coexistence des versions de Visual Studio](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md).  
  
    -   Vous pouvez mettre à jour le projet en permettant à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’apporter les modifications décrites plus loin dans cette rubrique. Si vous avez plusieurs projets Visual C\+\+ dans votre solution, vous devez tous les mettre à jour.  
  
        > [!NOTE]
        >  Si vous refusez la mise à jour lorsque vous y êtes invité, vous pouvez mettre à jour le projet ultérieurement en ouvrant le menu **Projet** et en choisissant l’option de **mise à jour du projet VC\+\+**. Si la commande ne s’affiche pas, une mise à jour ne sera pas obligatoire.  
  
## Mise à jour d’un projet Visual C\+\+  
 Si vous permettez à [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] de mettre automatiquement à jour le projet, ces modifications sont apportées :  
  
-   Modifie le projet afin qu’il utilise le compilateur et les bibliothèques [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] \(PlatformToolset \= VisualStudio v140\).  
  
-   Pour les projets [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)], remplace TargetFrameworkVersion par .NET Framework 4.5.2.  
  
## Utilisation constante d’un PlatformToolset personnalisé  
 Si vous souhaitez continuer à utiliser un PlatformToolset personnalisé dans [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)], l’ensemble d’outils doit se trouver sous %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ sur un ordinateur x86, ou sous %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ sur un ordinateur x64. Pour plus d’informations sur la création d’un PlatformToolset personnalisé, consultez le billet sur le [multi\-ciblage natif C\+\+](http://go.microsoft.com/fwlink/?LinkId=248587) dans le blog de l’équipe Visual C\+\+.  
  
## Voir aussi  
 [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)