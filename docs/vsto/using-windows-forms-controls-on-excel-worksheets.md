---
title: "Utilisation de contr&#244;les Windows Forms sur des feuilles de calcul Excel | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), Windows Forms (contrôles)"
  - "Excel (développement Office dans Visual Studio), contrôles Windows Forms"
  - "contrôles Windows Forms (développement Office dans Visual Studio), Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Utilisation de contr&#244;les Windows Forms sur des feuilles de calcul Excel
  Pour ajouter des contrôles Windows Forms à vos classeurs Microsoft Office Excel, procédez de la même manière que pour ajouter des contrôles aux Windows Forms.  Pour plus d'informations générales sur l'utilisation de contrôles sur des documents, consultez [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Considérations sur les contrôles pour Excel  
 Certains aspects spécifiques à Excel doivent être pris en considération.  
  
### Adaptation de la taille des contrôles à la taille des cellules  
 Vous pouvez définir le contrôle pour qu'il soit automatiquement redimensionné lorsque la taille de la cellule parente est modifiée.  Pour plus d’informations, consultez [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### Ajout de composants partagés par toutes les feuilles de calcul  
 Vous pouvez ajouter des composants à partager entre toutes les feuilles de calcul \(un <xref:System.Data.DataSet>, par exemple\) au Concepteur de classeurs plutôt qu'aux feuilles de calcul.  Ils apparaîtront dans la barre d'état des composants.  
  
### Formule pour incorporer des contrôles  
 Lorsque vous sélectionnez un contrôle dans Excel, vous voyez **\=EMBED\("WinForms.Control.Host",""\)** dans la **Barre de formule**.  Ce texte est nécessaire et ne doit pas être supprimé.  
  
## Voir aussi  
 [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Comment : masquer des contrôles sur des feuilles de calcul lors de l'impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Procédure pas à pas : modification de la mise en forme d'une feuille de calcul à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Procédure pas à pas : affichage de texte dans une zone de texte d'une feuille de calcul à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Procédure pas à pas : mise à jour d'un graphique dans une feuille de calcul à l'aide de cases d'option](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  