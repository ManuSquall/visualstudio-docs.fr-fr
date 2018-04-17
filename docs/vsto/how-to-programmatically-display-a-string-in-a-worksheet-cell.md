---
title: 'Comment : afficher par programme une chaîne dans une cellule de feuille de calcul | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29dafd7a3eace9350bdb045b2aee0d90a92a445c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  