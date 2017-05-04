---
title: "Acc&#232;s au ruban au moment de l&#39;ex&#233;cution | Microsoft Docs"
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
  - "Globals (classe), ruban"
  - "ruban (développement Office dans Visual Studio), accéder"
  - "RibbonManager (classe)"
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Acc&#232;s au ruban au moment de l&#39;ex&#233;cution
  Vous pouvez écrire du code pour afficher, masquer et modifier le ruban, et permettre aux utilisateurs d'exécuter ce code à partir de contrôles dans un volet de tâches personnalisé, un volet Actions ou une zone de formulaire Outlook.  
  
 Vous pouvez accéder au ruban à l'aide de la classe `Globals`.  Pour les projets Outlook, vous pouvez accéder au ruban qui s'affiche dans une fenêtre de l'explorateur ou de l'inspecteur Outlook spécifique.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Accès au ruban à l'aide de la classe Globals  
 Vous pouvez utiliser la classe `Globals` pour accéder au ruban dans un projet au niveau du document ou un projet de complément VSTO, où que vous soyez dans le projet.  
  
 Pour plus d'informations sur la classe `Globals`, consultez [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 L'exemple suivant utilise la classe `Globals` pour accéder à un ruban personnalisé nommé `Ribbon1` et définir le texte qui apparaît dans une zone de liste modifiable du ruban sur `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#4)]
 [!code-vb[Trin_Outlook_FR_Access#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#4)]  
  
## Accès à une collection de rubans qui s'affichent dans une fenêtre d'inspecteur Outlook spécifique  
 Vous pouvez accéder à une collection de rubans qui s'affichent dans les *inspecteurs* Outlook.  Un inspecteur est une fenêtre qui s'ouvre dans Outlook quand les utilisateurs effectuent certaines tâches, telles que la création d'un message électronique.  Pour accéder au ruban d'une fenêtre d'inspecteur, appelez la propriété `Ribbons` de la classe `Globals` et passez\-lui un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> qui représente l'inspecteur.  
  
 L'exemple suivant obtient la collection de rubans de l'inspecteur actif.  Cet exemple accède ensuite à un ruban nommé `Ribbon1` et définit le texte qui s'affiche dans une zone de liste modifiable du ruban sur `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#5)]
 [!code-vb[Trin_Outlook_FR_Access#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#5)]  
  
## Accès à une collection de rubans qui s'affichent pour un explorateur Outlook spécifique  
 Vous pouvez accéder à une collection de rubans qui s'affichent dans un *explorateur* Outlook.  Un explorateur est l'interface utilisateur principale de l'application pour une instance d'Outlook.  Pour accéder au ruban d'une fenêtre d'explorateur, appelez la propriété `Ribbons` de la classe `Globals` et passez\-lui un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> qui représente l'explorateur.  
  
 L'exemple suivant obtient la collection de rubans de l'explorateur actif.  Cet exemple accède ensuite à un ruban nommé `Ribbon1` et définit le texte qui s'affiche dans une zone de liste modifiable du ruban sur `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#6)]
 [!code-vb[Trin_Outlook_FR_Access#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#6)]  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : mise à niveau des contrôles sur un ruban au moment de l'exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Accès à une zone de formulaire au moment de l'exécution](../vsto/accessing-a-form-region-at-run-time.md)  
  
  