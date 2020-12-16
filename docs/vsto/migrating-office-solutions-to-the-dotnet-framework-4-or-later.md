---
title: Migrer des solutions Office vers le .NET Framework 4 ou version ultérieure
description: Découvrez comment vous pouvez migrer des solutions Office vers le .NET Framework 4 ou version ultérieure pour que votre projet continue à fonctionner.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b7780b6fccef86dfe4a671c0c468e5899adc36c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528460"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrer des solutions Office vers le .NET Framework 4 ou version ultérieure
  Si la version cible du .NET Framework d’un projet Office est remplacée par la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] version ou ultérieure d’une version antérieure du .NET Framework, certaines étapes supplémentaires peuvent être nécessaires pour continuer à exécuter la solution sur les ordinateurs de développement et les ordinateurs des utilisateurs finaux. Pour plus d’informations, consultez [modifications requises pour exécuter des projets Office que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 En outre, la compilation du projet peut ne plus s'effectuer. Certaines fonctionnalités des projets Office possèdent des modèles de programmation différents selon les versions de .NET Framework. Lorsque l'infrastructure cible d'un projet Office est modifiée  en version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ultérieure d'une version antérieure de .NET Framework, vous devez apporter les modifications de code suivantes au projet :

- [Mettez à jour les projets Excel et Word que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Mettre à jour les personnalisations de ruban dans les projets Office que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Mettez à jour les zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  La version cible de .Net Framework d'un projet Office change lorsque vous mettez à niveau ce projet à partir d'une version antérieure de Visual Studio. Pour plus d’informations, consultez [mettre à niveau et migrer des solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Pour plus d’informations sur la raison pour laquelle certaines fonctionnalités des projets Office ont un modèle de programmation différent lorsque vous ciblez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, consultez [modifications apportées à la conception des projets Office ciblant le .NET Framework 4 ou les .NET Framework 4,5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) et [Visual Studio Tools pour Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Voir aussi
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Guide pratique : Cibler une version de .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Résoudre les erreurs dans les solutions Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Prise en charge supplémentaire des erreurs dans les solutions Office](../vsto/additional-support-for-errors-in-office-solutions.md)
