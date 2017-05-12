---
title: "Migration de solutions Office vers .NET Framework&#160;4 ou version ult&#233;rieure | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "projets Office (développement Office dans Visual Studio), migration vers .NET Framework 4"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Migration de solutions Office vers .NET Framework&#160;4 ou version ult&#233;rieure
  Si la version cible de .NET Framework d'un projet Office est remplacée par la version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieure d'une version antérieure de .NET Framework, certaines étapes supplémentaires peuvent être requises pour continuer à exécuter la solution sur les ordinateurs de développement et des utilisateurs finaux. Pour plus d'informations, consultez [Modifications requises pour exécuter des projets Office qui font l'objet d'une migration vers .NET Framework 4 ou .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 En outre, la compilation du projet peut ne plus s'effectuer. Certaines fonctionnalités des projets Office possèdent des modèles de programmation différents selon les versions de .NET Framework. Lorsque l'infrastructure cible d'un projet Office est modifiée  en version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieure d'une version antérieure de .NET Framework, vous devez apporter les modifications de code suivantes au projet :  
  
-   [Mise à jour des projets Excel et Word qui font l'objet d'une migration vers .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Mise à jour des personnalisations de ruban dans les projets Office qui font l'objet d'une migration vers .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Mise à jour de zones de formulaire dans les projets Outlook qui font l'objet d'une migration vers .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 La version cible de .Net Framework d'un projet Office change lorsque vous mettez à niveau ce projet à partir d'une version antérieure de Visual Studio. Pour plus d'informations, consultez [Mise à niveau et migration de solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Pour plus d’informations sur la raison pour laquelle certaines fonctionnalités dans les projets Office ont un modèle de programmation différent quand vous ciblez [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, consultez [Modifications du design de projets Office qui ciblent .NET Framework 4 ou .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) et [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Voir aussi  
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Comment : cibler une version du .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Dépannage d'erreurs dans les solutions Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Ressources supplémentaires de résolution des erreurs dans les solutions Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  