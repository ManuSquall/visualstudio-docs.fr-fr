---
title: "Comment : afficher par programme une chaîne dans une cellule de feuille de calcul | Documents Microsoft"
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
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e297a2f6c1752053557dd7bcea5adab1c2184aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Comment : afficher une chaîne dans une cellule de feuille de calcul par programmation
  Cet exemple montre comment afficher le texte dans une cellule par programme. Pour afficher le texte dans la cellule, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>À l’aide d’un contrôle NamedRange  
 Cet exemple utilise un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle nommé `message`. Le contrôle doit être ajouté à une personnalisation au niveau du document au moment du design. Le code suivant doit être placé dans une classe sheet et non pas dans le `ThisWorkbook` classe.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Pour afficher le texte dans un contrôle NamedRange  
  
1.  Définir la valeur de la <xref:Microsoft.Office.Tools.Excel.NamedRange> le contrôle à **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>À l’aide d’une plage Excel Native  
 Le code suivant crée une nouvelle plage par programme et puis assigne une valeur à celle-ci.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Pour afficher le texte dans une plage Excel  
  
1.  Récupérez la plage à la cellule **A1** sur `Sheet1` et définissez la valeur sur **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Collecte de données à l’aide d’un Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Dépannage des Solutions Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  