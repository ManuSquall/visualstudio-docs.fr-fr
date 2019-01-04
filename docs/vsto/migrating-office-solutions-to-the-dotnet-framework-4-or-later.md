---
title: Migrer des solutions Office vers .NET Framework 4 ou version ultérieure
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 88f417ef8835e0614a2bf13b3717f19e3718feaf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845124"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrer des solutions Office vers .NET Framework 4 ou version ultérieure
  Si le framework cible d’un projet Office est remplacé par la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieurement à partir d’une version antérieure du .NET Framework, certaines étapes supplémentaires peuvent être nécessaires pour continuer à exécuter la solution sur les ordinateurs de développement et de l’utilisateur final. Pour plus d’informations, consultez [requis des modifications pour exécuter des projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 En outre, la compilation du projet peut ne plus s'effectuer. Certaines fonctionnalités des projets Office possèdent des modèles de programmation différents selon les versions de .NET Framework. Lorsque l'infrastructure cible d'un projet Office est modifiée  en version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieure d'une version antérieure de .NET Framework, vous devez apporter les modifications de code suivantes au projet :  
  
- [Mettre à jour des projets Excel et Word que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
- [Mettre à jour des personnalisations de ruban dans les projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)  
  
- [Mettre à jour de zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
  La version cible de .Net Framework d'un projet Office change lorsque vous mettez à niveau ce projet à partir d'une version antérieure de Visual Studio. Pour plus d’informations, consultez [mise à niveau et migrer des solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
  Pour plus d’informations sur la raison pour laquelle certaines fonctionnalités dans les projets Office ont un modèle de programmation différent lorsque vous ciblez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, consultez [modifications apportées à la conception des projets Office qui ciblent le .NET Framework 4 ou .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) et [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Guide pratique pour Cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Résoudre les erreurs dans les solutions Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Prise en charge supplémentaire pour les erreurs dans les solutions Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
