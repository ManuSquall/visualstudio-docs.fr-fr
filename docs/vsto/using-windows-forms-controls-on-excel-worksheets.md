---
title: "Utilisation de Windows Forms contrôles sur des feuilles de calcul Excel | Documents Microsoft"
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
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bbd9c19698a9c81b5af29d27bba91b8aa36dcd2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Utilisation de contrôles Windows Forms sur des feuilles de calcul Excel
  Vous pouvez ajouter des contrôles Windows Forms dans vos classeurs Microsoft Office Excel de la même manière que vous ajoutez des contrôles aux Windows Forms. Pour obtenir des informations générales sur l’utilisation des contrôles sur des documents, consultez [contrôles Windows Forms dans une vue d’ensemble des Documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Considérations sur les contrôles pour Excel  
 Il existe quelques règles qui sont spécifiques à Excel.  
  
### <a name="matching-control-size-to-cell-size"></a>Taille de contrôle correspondant à la taille de cellule  
 Vous pouvez configurer le contrôle pour qu’il soit redimensionné automatiquement quand la taille de la cellule parente change. Pour plus d’informations, consultez [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Ajout de composants partagés par toutes les feuilles de calcul  
 Vous pouvez ajouter des composants que vous souhaitez partager parmi toutes les feuilles de calcul, comme un <xref:System.Data.DataSet>, au Concepteur de classeurs plutôt qu’aux feuilles de calcul. Le composant apparaîtra dans la barre d’état des composants.  
  
### <a name="formula-for-embedding-controls"></a>Formule pour incorporer des contrôles  
 Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : redimensionner des contrôles dans les cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Procédure pas à pas : Modification de mise en forme de feuille de calcul à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Procédure pas à pas : Affichage de texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Procédure pas à pas : mise à jour d’un graphique dans une feuille de calcul à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  