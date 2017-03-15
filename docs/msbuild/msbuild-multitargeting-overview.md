---
title: "MSBuild Multitargeting Overview | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# MSBuild Multitargeting Overview
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grâce à MSBuild, compilez une application pour l'exécuter sur n'importe quelle version du .NET Framework, et sur n'importe laquelle de plusieurs plateformes du système.  Par exemple, compilez une application qui s'exécutera sur le .NET Framework version 2.0 sur une plateforme 32\-bit et compilez la même application pour qu'elle s'exécute sur le .NET Framework version 4.5 sur une plateforme 64\-bit.  
  
> [!IMPORTANT]
>  En dépit du nom « multi\-ciblage », un projet peut cibler uniquement une infrastructure et une seule plateforme à la fois.  
  
 Voici quelques\-unes des fonctionnalités du cibleur MSBuild :  
  
-   Vous pouvez développer une applications qui cible des versions antérieures du .NET Framework \(par exemple, les versions 2.0, 3.5 ou 4\).  
  
-   Vous pouvez cibler un Framework autres que le .NET Framework \(par exemple, le framework Silverlight\).  
  
-   Vous pouvez cibler un*profil Framework*, qui est un sous\-ensemble prédéfini d'une version cible du .NET Framework.  
  
-   Si des packs de services pour la version actuelle de .NET Framework sont publiés, vous pouvez les cibler.  
  
-   Le ciblage MSBuild garantit qu'une application utilise uniquement les fonctionnalités disponibles dans la version cible du .NET Framework.  
  
## Framework cible et plateforme  
 La *version cible de. Net Framework* est la version du .NET Framework sur laquelle l'exécution d'un projet doit fonctionner, et une *une plateforme cible* est la plateforme de système sur laquelle le projet doit fonctionner.  Par exemple, vous pouvez cibler une application du .NET Framework 2.0 pour qu'elle fonctionne sur une plateforme 32 bits et soit compatible avec la famille de processeurs 802x86 \(« x86 "\).  La combinaison de la version cible de. Net Framework et de la plateforme cible est appelé *contexte cible*.  Pour plus d'informations, consultez [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## Ensemble d'outils \(ToolsVersion\)  
 Un ensemble d'outils collecte ensemble des outils, des tâches, et les cibles utilisés pour créer l'application.  Un ensemble d'outils inclut des compilateurs tels que csc.exe et vbc.exe, le fichier des cibles communes \(microsoft.common.targets\) et le fichier des tâches courantes \(microsoft.common.tasks\).  L'ensemble d'outils 4,5 peut être utilisé pour cibler des versions du .Net Framework 2,0, 3,0, 3,5, 4, et 4,5. Toutefois, l'ensemble d'outils MSBuild 2,0 ne peut être utilisé que pour cibler .NET Framework 2.0.  Pour plus d'informations, consultez [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Assemblys de référence  
 Les assemblys de référence spécifiés dans l'aide de l'ensemble d'outils vous aident à concevoir et générer une application.  Ces assemblys de référence permettent non seulement une génération cible particulière, mais limitent également les composants et les fonctionnalités dans l'IDE de Visual Studio à ceux qui sont compatibles avec la cible.  Pour plus d’informations, consultez [Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md)  
  
## Configuration des cibles et des tâches  
 Vous pouvez configurer les cibles et les tâches MSBuild pour qu'elle s'exécutent hors processus avec MSBuild afin que vous puissiez cibler les contextes qui sont très différents que celui sur lesquels vous fonctionnez.  Par exemple, vous pouvez cibler une application sur .NET Framework 2.0 à 32\-bit pendant que l'ordinateur de développement s'exécute sur une plateforme 64 bits avec .NET Framework 4,5. Pour plus d'informations, consultez [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md).  
  
## Dépannage  
 Vous pouvez rencontrer des erreurs si vous essayez de référencer un assembly qui ne fait pas partie du contexte cible.  Pour plus d'informations sur ces erreurs et comment les gérer, consultez [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).