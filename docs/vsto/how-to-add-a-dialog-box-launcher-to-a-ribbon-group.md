---
title: "Comment&#160;: ajouter un lanceur de bo&#238;te de dialogue &#224; un groupe de ruban"
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
  - "lanceur de boîte de dialogue (développement Office dans Visual Studio)"
  - "ruban (développement Office dans Visual Studio), lanceur de boîte de dialogue"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Comment&#160;: ajouter un lanceur de bo&#238;te de dialogue &#224; un groupe de ruban
  Vous pouvez ajouter un lanceur de boîte de dialogue à n'importe quel groupe sur un ruban.  Un lanceur de boîte de dialogue est une petite icône qui apparaît dans un groupe.  Les utilisateurs cliquent sur cette icône pour ouvrir des boîtes de dialogue liées ou des volets Office qui fournissent des options supplémentaires en rapport avec le groupe.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Pour ajouter un lanceur de boîte de dialogue à un groupe de ruban  
  
1.  Sélectionnez le fichier de code du ruban \(fichier .vb ou .cs\) dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Affichage**, cliquez sur **Concepteur**.  
  
3.  Dans le Concepteur de ruban, cliquez avec le bouton droit sur un groupe, puis cliquez sur **Ajouter DialogBoxLauncher**.  
  
     Ajoutez du code à l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> du groupe pour ouvrir une boîte de dialogue personnalisée ou intégrée.  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : modifier la position d'un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Comment : afficher les erreurs de l'interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : mise à niveau des contrôles sur un ruban au moment de l'exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide d'un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  