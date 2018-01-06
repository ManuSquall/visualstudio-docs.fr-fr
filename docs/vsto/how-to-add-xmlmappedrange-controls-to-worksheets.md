---
title: "Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 59c82cd16da614229cedd01bccd7a5057246299c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul
  Lorsque vous mappez un élément XML à une cellule dans Microsoft Office Excel, Visual Studio ajoute automatiquement un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle à votre feuille de calcul.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle n’est pas disponible sur le **boîte à outils** ou **des Sources de données** fenêtre. En outre, vous ne pouvez pas créer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôles par programmation.  
  
### <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Pour ajouter un contrôle XMLMappedRange à une feuille de calcul  
  
1.  Ouvrez le classeur Excel dans le concepteur Visual Studio.  
  
2.  Ouvrez la feuille de calcul où vous souhaitez ajouter le contrôle.  
  
3.  Sur le **Developer** , cliquez sur **Source**.  
  
    > [!NOTE]  
    >  Si le **développeur** onglet n’est pas visible sur le ruban, vous devez l’activer. Pour plus d'informations, consultez [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Le **Source XML** volet s’affiche.  
  
4.  Dans le **Source XML** volet de tâches, cliquez sur **mappages XML**.  
  
5.  Dans le **mappages XML** boîte de dialogue, cliquez sur **ajouter**.  
  
     Le **Source XML** boîte de dialogue s’affiche.  
  
6.  Sélectionnez un schéma XML à partir de la **Source XML** boîte de dialogue et cliquez sur **ouvrir**.  
  
     Le schéma est ajouté à la **mappages XML** boîte de dialogue.  
  
7.  Dans le **mappages XML** boîte de dialogue, cliquez sur **OK**.  
  
8.  Faites glisser un élément à partir de la **Source XML** volet de tâches à une cellule de la feuille de calcul.  
  
     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est créé et ajouté au projet.  
  
    > [!NOTE]  
    >  Si vous faites glisser un élément parent à partir de la **Source XML** volet des tâches, une <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle est créé.  
  
## <a name="see-also"></a>Voir aussi  
 [XmlMappedRange, contrôle](../vsto/xmlmappedrange-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Guide pratique pour mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  