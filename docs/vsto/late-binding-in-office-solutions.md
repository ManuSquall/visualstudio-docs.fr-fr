---
title: Liaison tardive dans les solutions Office
description: Découvrez comment certains types dans les modèles objet dans Microsoft Office applications fournissent des fonctionnalités qui sont disponibles via des fonctionnalités de liaison tardive.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823884"
---
# <a name="late-binding-in-office-solutions"></a>Liaison tardive dans les solutions Office
  Certains types dans les modèles objet des applications Office fournissent des fonctionnalités disponibles via les fonctionnalités de liaison tardive. Par exemple, certaines méthodes et propriétés peuvent retourner différents types d’objets en fonction du contexte de l’application Office, et certains types peuvent exposer différentes méthodes ou propriétés dans différents contextes.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic projets où **option strict** a la valeur OFF et les projets Visual C# qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] peuvent fonctionner directement avec les types qui utilisent ces fonctionnalités de liaison tardive.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Conversion implicite et explicite des valeurs de retour de l’objet
 De nombreuses méthodes et propriétés dans le Microsoft Office les assemblys PIA (Primary Interop Assembly) retournent des <xref:System.Object> valeurs, car elles peuvent retourner plusieurs types d’objets différents. Par exemple, la <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> propriété retourne un <xref:System.Object> , car sa valeur de retour peut être un <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> objet ou, en fonction de la feuille active.

 Quand une méthode ou une propriété retourne un <xref:System.Object> , vous devez convertir explicitement (dans Visual Basic) l’objet vers le type approprié dans Visual Basic projets où **option strict** a la valeur on. Vous n’avez pas besoin de convertir explicitement les <xref:System.Object> valeurs de retour dans les projets Visual Basic où **option strict** est désactivée.

 Dans la plupart des cas, la documentation de référence répertorie les types possibles de la valeur de retour pour un membre qui retourne un <xref:System.Object> . La conversion ou le cast de l’objet Active IntelliSense pour l’objet dans l’éditeur de code.

 Pour plus d’informations sur la conversion dans Visual Basic, consultez [conversions implicites et explicites &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) et [CType Function &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;.

### <a name="examples"></a>Exemples
 L’exemple de code suivant montre comment effectuer un cast d’un objet en un type spécifique dans un projet Visual Basic dans lequel **option strict** a la valeur on. Dans ce type de projet, vous devez effectuer un cast explicite <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> de la propriété en <xref:Microsoft.Office.Interop.Excel.Range> . Cet exemple requiert un projet Excel au niveau du document avec une classe de feuille de calcul nommée `Sheet1` .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 L’exemple de code suivant montre comment effectuer un cast implicite d’un objet en un type spécifique dans un projet Visual Basic, où **option strict** est désactivé ou dans un projet Visual C# qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Dans ces types de projets, la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> propriété est convertie implicitement en <xref:Microsoft.Office.Interop.Excel.Range> . Cet exemple requiert un projet Excel au niveau du document avec une classe de feuille de calcul nommée `Sheet1` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Accéder aux membres qui sont uniquement disponibles via la liaison tardive
 Certaines propriétés et méthodes dans les assemblys PIA Office sont disponibles uniquement via une liaison tardive. Dans Visual Basic projets où **option strict** est désactivé ou dans les projets Visual C# qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , vous pouvez utiliser les fonctionnalités de liaison tardive dans ces langages pour accéder aux membres à liaison tardive. Dans Visual Basic projets où **option strict** a la valeur on, vous devez utiliser la réflexion pour accéder à ces membres.

### <a name="examples"></a>Exemples
 L’exemple de code suivant montre comment accéder aux membres à liaison tardive dans un projet Visual Basic, où **option strict** est désactivé ou dans un projet Visual C# qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Cet exemple accède à la propriété de **nom** à liaison tardive de la boîte de dialogue **ouvrir un fichier** dans Word. Pour utiliser cet exemple, exécutez-le à partir de la `ThisDocument` `ThisAddIn` classe ou dans un projet Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 L’exemple de code suivant montre comment utiliser la réflexion pour accomplir la même tâche dans un projet de Visual Basic où **option strict** a la valeur on.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Voir aussi
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Utilisez le Guide de programmation du&#35; de type Dynamic &#40;C&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Réflexion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Réflexion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
