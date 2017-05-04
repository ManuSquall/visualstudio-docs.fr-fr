---
title: "Comment&#160;: emp&#234;cher Outlook d&#39;afficher une zone de formulaire | Microsoft Docs"
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
  - "annuler l'affichage de la zone de formulaire"
  - "zones de formulaire (développement Office dans Visual Studio), annuler l'affichage"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: emp&#234;cher Outlook d&#39;afficher une zone de formulaire
  Dans certains cas, vous ne souhaitez pas que Microsoft Office Outlook affiche une zone de formulaire pour un élément particulier.  Par exemple, si un contact ne contient pas d'adresse professionnelle, vous pouvez empêcher l'affichage d'une zone indiquant l'emplacement de l'entreprise sur une carte.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### Pour empêcher Outlook d'afficher une zone de formulaire  
  
1.  Ouvrez le fichier de code de la zone de formulaire que vous souhaitez modifier.  
  
2.  Développez la région de code **Fabrique de zones de formulaire**.  
  
3.  Ajoutez le code au gestionnaire d'événements  `FormRegionInitializing` qui affecte à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de la classe <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> la valeur **true**.  
  
 Dans cet exemple, si l'élément de contact ne contient pas d'adresse, la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> a la valeur **true** et la zone de formulaire n'apparaît pas.  
  
## Exemple  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## Voir aussi  
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procédure pas à pas : importation d'une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  