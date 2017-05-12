---
title: "Comment&#160;: ajouter une r&#233;f&#233;rence de sortie de projet"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "références de sortie de projet (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, outils d'empaquetage avancés"
  - "développement SharePoint dans Visual Studio, références de sortie de projet"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: ajouter une r&#233;f&#233;rence de sortie de projet
  Pour déployer des assemblys de projet autres que SharePoint \(ou des fichiers .xap dans des projets Silverlight\) sur SharePoint, ajoutez\-les comme une référence de sortie de projet.  
  
 Ce processus crée une dépendance de génération de solution entre les deux projets.  Les projets associés aux références de sortie de projet sont générés avant la génération et le déploiement du projet SharePoint.  
  
### Pour ajouter une référence de sortie de projet  
  
1.  Chargez une solution qui contient au moins un projet SharePoint et un projet autre que SharePoint.  
  
2.  Dans l'**Explorateur de solutions**, cliquez sur un élément dans le noeud du projet SharePoint.  
  
3.  Dans la fenêtre **Propriétés**, cliquez sur la propriété **Project Output References**, puis sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\) en regard de celle\-ci.  
  
4.  Dans la boîte de dialogue **Références de sortie de projet**, cliquez sur le bouton **Ajouter**.  
  
5.  Dans le volet de propriétés, cliquez sur la flèche de déroulement en regard de la propriété **Deployment Type** et sélectionnez une valeur appropriée pour l'élément non\-SharePoint que vous référencez, par exemple **ElementFile**.  
  
6.  Cliquez sur la flèche à côté de **Nom de projet**, sélectionnez le nom de l'élément de projet autre que SharePoint, puis choisissez le bouton **OK**.  
  
## Voir aussi  
 [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Comment : marquer des contrôles comme étant des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  