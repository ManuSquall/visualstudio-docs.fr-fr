---
title: "Coexistence des versions de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installations côte à côte (Visual Studio)"
  - "Aide ([Visual Studio], installer"
  - "Express Edition [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Coexistence des versions de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio peut être installé sur un ordinateur sur lequel une version antérieure de Visual Studio l’est déjà. Si vous rencontrez un problème d’installation, vous pouvez utiliser l’[outil de collecte de journaux](http://go.microsoft.com/fwlink/?LinkId=262077) pour collecter des informations sur les échecs de sorte que vous puissiez déboguer les problèmes vous\-même.  
  
> [!NOTE]
>  Nous vous recommandons d’installer des versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans leur ordre de commercialisation. Par exemple, installez Visual Studio 2013 avant d’installer Visual Studio 2015.  
  
 Avant d’installer plusieurs versions sur la même machine, vérifiez que les conditions suivantes sont bien réunies :  
  
-   Si vous utilisez Visual Studio 2015 pour ouvrir une solution créée dans [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], vous pouvez par la suite ouvrir et modifier à nouveau la solution dans la version antérieure à condition de ne pas avoir implémenté de fonctionnalités spécifiques à Visual Studio 2015.  
  
-   Si vous essayez d’utiliser Visual Studio 2015 pour ouvrir une solution créée dans [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] ou une version antérieure, vous devrez peut\-être modifier vos projets et fichiers pour qu’ils soient compatibles avec Visual Studio 2015. Pour plus d’informations, consultez [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Si vous désinstallez une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sur un ordinateur ayant plusieurs versions installées, les associations de fichiers pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont supprimées pour toutes les versions. Vous pouvez remapper ces associations de fichiers à l’aide du bouton **Restaurer les associations de fichiers** sous les onglets **Environnement**, **Général** de la boîte de dialogue [Options](../ide/reference/general-environment-options-dialog-box.md).  
  
-   Visual Studio ne met pas automatiquement à niveau les extensions, car elles ne sont pas toutes compatibles. Vous devez réinstaller les extensions à partir de la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) ou de l’éditeur du logiciel.  
  
## Versions du .NET Framework et installations côte à côte  
  
-   Les projets Visual Basic, Visual C\#, Visual F\# utilisent l’option **Framework cible** dans le **Concepteur de projets** pour spécifier la version du .NET Framework qu’un projet utilise. Pour un projet C\+\+, vous pouvez changer manuellement la version cible du .NET Framework en modifiant le fichier .vcxproj. Pour plus d’informations, consultez [Compatibilité des versions](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md).  
  
     Au moment de créer un projet, vous pouvez spécifier la version du .NET Framework que le projet cible dans la liste **.NET Framework** de la boîte de dialogue **Nouveau projet**.  
  
     Pour des informations spécifiques au langage, consultez la rubrique appropriée dans le tableau suivant.  
  
    |Langage|Rubrique|  
    |-------------|--------------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[Page Application, Concepteur de projets \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[Page Application, Concepteur de projets \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[comment : modifier la version cible de .Net Framework et l'ensemble d'outils de la plateforme](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../extensibility/debugger/includes/jsprjscript_md.md)]|[Exécution d’une application JScript sur une version précédente du Common Language Runtime](http://msdn.microsoft.com/fr-fr/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## Voir aussi  
 [Installation de Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Compatibilité des versions](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [Installation de versions multilingues de Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Génération d'applications isolées C\/C\+\+ et d'assemblys côte à côte](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)