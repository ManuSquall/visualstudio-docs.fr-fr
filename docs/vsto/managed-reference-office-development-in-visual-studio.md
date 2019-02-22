---
title: Référence managée (développement Office dans Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d6fa14bfffb500ab107523bc7444efa12f930e0c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646758"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Référence managée (développement Office dans Visual Studio)
  Cette section contient la documentation de référence des API pour les espaces de noms et types utilisés dans les projets Office qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour la documentation de référence des API sur les espaces de noms et les types qui sont utilisés dans les projets Office qui ciblent le .NET Framework 3.5, consultez la section de référence suivante dans la documentation de Visual Studio : [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).

> [!NOTE]
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.

## <a name="in-this-section"></a>Dans cette section
 <xref:Microsoft.Office.Tools>

 Contient des classes courantes pour la programmation de solutions Office. Celles-ci incluent notamment la classe de base des compléments VSTO, les classes pour la création de volets des tâches personnalisés dans les compléments VSTO, les classes pour la création de balises actives dans les solutions Excel et Word, ainsi que les classes pour la création de volets Actions dans les personnalisations au niveau du document.

 <xref:Microsoft.Office.Tools.Excel>

 Contient des contrôles hôtes et des éléments hôtes qui peuvent être utilisés dans les solutions pour Excel.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Contient des contrôles Excel et des contrôles Windows Forms qui peuvent être utilisés dans les solutions pour Excel.

 <xref:Microsoft.Office.Tools.Outlook>

 Contient des classes utilisées par les compléments VSTO pour Outlook, notamment les classes utilisées pour créer des zones de formulaire personnalisées.

 <xref:Microsoft.Office.Tools.Ribbon>

 Contient les classes utilisées pour modifier par programmation des personnalisations de ruban créées à l’aide du Concepteur de ruban.

 <xref:Microsoft.Office.Tools.Word>

 Contient des contrôles hôtes et des éléments hôtes qui peuvent être utilisés dans les solutions pour Word.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Contient des contrôles Word et des contrôles Windows Forms qui peuvent être utilisés dans les solutions pour Word.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Contient la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> et un ensemble de classes des données en mémoire cache associées. Ces classes peuvent être utilisées pour modifier certains aspects de personnalisations au niveau du document sur les ordinateurs sur lesquels Microsoft Office n’est pas installé.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Contient l’interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> (que vous pouvez implémenter pour créer une *action de post-déploiement* pour une solution Office), des exceptions pouvant être levées lors de l’installation d’une solution Office, ainsi que d’autres API qui font partie de l’infrastructure Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Contient la plupart des exceptions pouvant être levées par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], plusieurs classes pouvant être utilisées pour mettre en cache des données dans les personnalisations au niveau du document, ainsi que d’autres API qui font partie de l’infrastructure Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Contient des classes de tâche MSBuild utilisées pour générer des projets Office.

## <a name="see-also"></a>Voir aussi
- [Visual Studio tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
