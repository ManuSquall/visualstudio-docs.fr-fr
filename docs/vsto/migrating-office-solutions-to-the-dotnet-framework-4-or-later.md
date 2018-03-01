---
title: "Migration de Solutions Office vers .NET Framework 4 ou version ultérieure | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 8cb61186c7e8260578e9b69242c594c198f7e525
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migration de solutions Office vers .NET Framework 4 ou version ultérieure
  Si la version cible de .NET Framework d'un projet Office est remplacée par la version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieure d'une version antérieure de .NET Framework, certaines étapes supplémentaires peuvent être requises pour continuer à exécuter la solution sur les ordinateurs de développement et des utilisateurs finaux. Pour plus d’informations, consultez [les modifications requises pour exécuter les projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 En outre, la compilation du projet peut ne plus s'effectuer. Certaines fonctionnalités des projets Office possèdent des modèles de programmation différents selon les versions de .NET Framework. Lorsque l'infrastructure cible d'un projet Office est modifiée  en version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieure d'une version antérieure de .NET Framework, vous devez apporter les modifications de code suivantes au projet :  
  
-   [Mise à jour des projets Excel et Word que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Mise à jour des personnalisations de ruban dans les projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Mise à jour de zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 La version cible de .Net Framework d'un projet Office change lorsque vous mettez à niveau ce projet à partir d'une version antérieure de Visual Studio. Pour plus d'informations, consultez [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Pour plus d’informations sur la raison pour laquelle certaines fonctionnalités dans les projets Office ont un modèle de programmation différent lorsque vous ciblez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, consultez [modifications apportées à la conception des projets Office qui ciblent le .NET Framework 4 ou .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) et [Visual Studio Tools pour Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Dépannage des erreurs dans les Solutions Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Ressources supplémentaires de résolution des erreurs dans les solutions Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  