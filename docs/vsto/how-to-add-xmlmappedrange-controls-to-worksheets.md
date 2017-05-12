---
title: "Comment&#160;: ajouter des contr&#244;les XMLMappedRange aux feuilles de calcul"
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
  - "contrôles (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
  - "XMLMappedRange (contrôle), ajouter à des feuilles de calcul"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: ajouter des contr&#244;les XMLMappedRange aux feuilles de calcul
  Lorsque vous mappez un élément XML à une cellule dans Microsoft Office Excel, Visual Studio ajoute automatiquement un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> à votre feuille de calcul.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> n'est pas disponible dans la **Boîte à outils** ou la fenêtre **Sources de données**.  En outre, vous ne pouvez pas créer les contrôles <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> par programmation.  
  
### Pour ajouter un contrôle XMLMappedRange à une feuille de calcul  
  
1.  Ouvrez le classeur Excel dans le concepteur Visual Studio.  
  
2.  Ouvrez la feuille de calcul à laquelle vous souhaitez ajouter le contrôle.  
  
3.  Dans l'onglet **Développeur**, cliquez sur **Source**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible sur le ruban, vous devez l'activer.  Pour plus d’informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Le volet de tâches **Source XML** apparaît.  
  
4.  Dans le volet de tâches **Source XML**, cliquez sur **Mappages XML**.  
  
5.  Dans la boîte de dialogue **Mappages XML**, cliquez sur **Ajouter**.  
  
     La boîte de dialogue **Source XML** s'affiche.  
  
6.  Sélectionnez un schéma XML dans la boîte de dialogue **Source XML** et cliquez sur **Ouvrir**.  
  
     Le schéma est ajouté à la boîte de dialogue **Mappages XML**.  
  
7.  Dans la boîte de dialogue **Mappages XML**, cliquez sur **OK**.  
  
8.  Faites glisser un élément du volet de tâches **Source XML** vers une cellule sur la feuille de calcul.  
  
     Une <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est alors créée et ajoutée au projet.  
  
    > [!NOTE]  
    >  Si vous faites glisser un élément parent du volet de tâches **Source XML**, un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> est créé.  
  
## Voir aussi  
 [XmlMappedRange, contrôle](../vsto/xmlmappedrange-control.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  