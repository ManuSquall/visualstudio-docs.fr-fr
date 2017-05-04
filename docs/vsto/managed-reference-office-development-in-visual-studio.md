---
title: "R&#233;f&#233;rence manag&#233;e (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "référence (développement Office dans Visual Studio), version 2007 de Microsoft Office System"
  - "développement Office dans Visual Studio (référence)"
ms.assetid: 1fa66da0-9d90-4524-ba4f-4da13aab73b5
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# R&#233;f&#233;rence manag&#233;e (d&#233;veloppement Office dans Visual Studio)
  Cette section contient la documentation de référence des API pour les espaces de noms et types utilisés dans les projets Office qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour obtenir la documentation de référence des API sur les espaces de noms et les types utilisés par les projets Office qui ciblent .NET Framework 3.5, consultez la section de référence suivante dans la documentation de Visual Studio : [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
## Dans cette section  
 <xref:Microsoft.Office.Tools>  
 Contient des classes courantes pour la programmation de solutions Office. Celles\-ci incluent notamment la classe de base des compléments VSTO, les classes pour la création de volets des tâches personnalisés dans les compléments VSTO, les classes pour la création de balises actives dans les solutions Excel et Word, ainsi que les classes pour la création de volets Actions dans les personnalisations au niveau du document.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Contient des contrôles hôtes et des éléments hôtes qui peuvent être utilisés dans les solutions pour Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Contient des contrôles Excel et des contrôles Windows Forms qui peuvent être utilisés dans les solutions pour Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Contient des classes utilisées par les compléments VSTO pour Outlook, notamment les classes utilisées pour créer des zones de formulaire personnalisées.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Contient les classes utilisées pour modifier par programmation des personnalisations de ruban créées à l’aide du Concepteur de ruban.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Contient des contrôles hôtes et des éléments hôtes qui peuvent être utilisés dans les solutions pour Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Contient des contrôles Word et des contrôles Windows Forms qui peuvent être utilisés dans les solutions pour Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Contient la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> et un ensemble de classes des données en mémoire cache associées. Ces classes peuvent être utilisées pour modifier certains aspects de personnalisations au niveau du document sur les ordinateurs sur lesquels Microsoft Office n’est pas installé.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Contient l’interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> \(que vous pouvez implémenter pour créer une *action de post\-déploiement* pour une solution Office\), des exceptions pouvant être levées lors de l’installation d’une solution Office, ainsi que d’autres API qui font partie de l’infrastructure Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Contient la plupart des exceptions pouvant être levées par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], plusieurs classes pouvant être utilisées pour mettre en cache des données dans les personnalisations au niveau du document, ainsi que d’autres API qui font partie de l’infrastructure Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Contient des classes de tâche MSBuild utilisées pour générer des projets Office.  
  
## Voir aussi  
 [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  