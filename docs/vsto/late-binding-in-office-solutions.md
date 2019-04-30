---
title: Liaison tardive dans les solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62224006d04e0a1e7447053e868dd9946f00c97e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583944"
---
# <a name="late-binding-in-office-solutions"></a>Liaison tardive dans les solutions Office
  Certains types dans les modèles objet des applications Office fournissent des fonctionnalités qui sont disponibles via les fonctionnalités de liaison tardive. Par exemple, certaines méthodes et propriétés peuvent retourner différents types d’objets en fonction du contexte de l’application Office, et certains types peuvent exposer des méthodes ou propriétés dans différents contextes.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Les projets Visual Basic où **Option Strict** est désactivé et Visual C# les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] peut travailler directement avec les types qui utilisent ces fonctionnalités de liaison tardive.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Conversion implicite et explicite de l’objet retournent des valeurs
 Nombreuses méthodes et propriétés retournent des assemblys PIA (Primary Interop Assemblies) de Microsoft Office <xref:System.Object> valeurs, car elles peuvent retourner plusieurs types d’objets différents. Par exemple, le <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> propriété retourne un <xref:System.Object> , car sa valeur de retour peut être un <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.Chart> objet, en fonction de la feuille active.

 Quand une méthode ou propriété retourne un <xref:System.Object>, vous devez convertir explicitement (en Visual Basic) l’objet en type correct dans les projets Visual Basic où **Option Strict** se trouve sur. Vous n’avez pas à effectuer un cast explicite <xref:System.Object> retournent des valeurs dans les projets Visual Basic où **Option Strict** est désactivé.

 Dans la plupart des cas, la documentation de référence répertorie les types de la valeur de retour possibles pour un membre qui retourne un <xref:System.Object>. Conversion ou le cast de l’objet permet à IntelliSense pour l’objet dans l’éditeur de Code.

 Pour plus d’informations sur la conversion en Visual Basic, consultez [conversions implicites et explicites &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) et [CType function &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>Exemples
 L’exemple de code suivant montre comment effectuer un cast d’un objet à un type spécifique dans un projet Visual Basic où **Option Strict** se trouve sur. Dans ce type de projet, vous devez caster explicitement la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propriété à un <xref:Microsoft.Office.Interop.Excel.Range>. Cet exemple requiert un projet d’Excel au niveau du document avec une classe de feuille de calcul nommée `Sheet1`.

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 L’exemple de code suivant montre comment effectuer une conversion implicite un objet à un type spécifique dans un projet Visual Basic où **Option Strict** est désactivé ou dans un élément visuel C# projet qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Dans ces types de projets, le <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propriété est implicitement convertie dans un <xref:Microsoft.Office.Interop.Excel.Range>. Cet exemple requiert un projet d’Excel au niveau du document avec une classe de feuille de calcul nommée `Sheet1`.

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Accès aux membres qui sont disponibles uniquement par le biais de la liaison tardive
 Certaines propriétés et méthodes dans les assemblys PIA Office sont disponibles uniquement par le biais de la liaison tardive. En Visual Basic, projets où **Option Strict** est désactivé ou dans Visual C# les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vous pouvez utiliser les fonctionnalités de liaison tardive dans ces langages pour accéder aux membres de la liaison tardive. En Visual Basic, projets où **Option Strict** est activé, vous devez utiliser la réflexion pour accéder à ces membres.

### <a name="examples"></a>Exemples
 L’exemple de code suivant montre comment accéder aux membres à liaison tardive dans un projet Visual Basic où **Option Strict** est désactivé ou dans un élément visuel C# projet qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Cet exemple accède à la liaison tardive **nom** propriété de la **ouvrir le fichier** boîte de dialogue dans Word. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` ou `ThisAddIn` classe dans un projet Word.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 L’exemple de code suivant montre comment utiliser la réflexion pour accomplir la même tâche dans un projet Visual Basic où **Option Strict** se trouve sur.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Voir aussi
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Utilisation du Type dynamic &#40;C&#35; guide de programmation&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
