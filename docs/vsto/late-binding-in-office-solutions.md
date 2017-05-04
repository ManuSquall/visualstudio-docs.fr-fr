---
title: "Liaison tardive dans les solutions Office | Microsoft Docs"
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
  - "objets (développement Office dans Visual Studio), cast"
  - "types (développement Office dans Visual Studio), cast"
  - "automation (développement Office dans Visual Studio), cast d’objets"
  - "cast, objet en type spécifique"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Liaison tardive dans les solutions Office
  Certains types des modèles objets d'applications Office fournissent des fonctionnalités disponibles via des fonctionnalités de liaison tardive.  Par exemple, certaines méthodes et propriétés peuvent retourner différents types d'objets selon le contexte de l'application Office et certains types peuvent exposer différentes méthodes ou propriétés dans différents contextes.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Les projets Visual Basic où **Option Strict** est désactivé et les projets Visual c qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] peuvent fonctionner directement avec les types qui utilisent ces fonctionnalités de liaison tardive.  
  
## Conversion implicite et explicite des valeurs de retour d'objet  
 De nombreuses méthodes et propriétés des assemblys PIA \(Primary Interop Assembly\) Microsoft Office retournent des valeurs <xref:System.Object>, car elles peuvent retourner plusieurs types d'objets différents.  Par exemple, la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> retourne <xref:System.Object> car sa valeur de retour peut être un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.Chart>, selon la feuille active.  
  
 Lorsqu'une méthode ou une propriété retourne <xref:System.Object>, vous devez convertir explicitement \(en Visual Basic\) l'objet approprié au type dans les projets Visual Basic où **Option Strict** est activé.  Vous ne devez pas caster explicitement des valeurs de retour d' <xref:System.Object> dans les projets Visual Basic où **Option Strict** est désactivé.  
  
 Dans la plupart des cas, la documentation de référence répertorie les types de valeur de retour possibles pour un membre qui retourne <xref:System.Object>.  La conversion ou le cast de l'objet active la fonctionnalité IntelliSense relative à cet objet dans l'éditeur de code.  
  
 Pour plus d'informations sur la conversion en Visual Basic, consultez [Implicit and Explicit Conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) et [Fonction CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### Exemples  
 L'exemple de code suivant montre comment effectuer un cast d'un objet en un type spécifique dans un projet Visual Basic dans lesquels **Option Strict** est activé.  Dans ce type de projet, vous devez caster explicitement la propriété d' <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> à <xref:Microsoft.Office.Interop.Excel.Range>.  Cet exemple requiert un projet Excel de niveau document avec une classe de feuille de calcul nommée `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 L'exemple de code suivant montre comment caster implicitement un objet en un type spécifique dans un projet Visual Basic dans lequel **Option Strict** est désactivé ou dans un projet Visual C\# qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Dans ces types de projets, la propriété <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> est castée implicitement en <xref:Microsoft.Office.Interop.Excel.Range>.  Cet exemple requiert un projet Excel de niveau document avec une classe de feuille de calcul nommée `Sheet1`.  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## Accès à des membres disponibles uniquement via une liaison tardive  
 Certaines propriétés et méthodes des assemblys PIA Office sont uniquement disponibles via une liaison tardive.  Dans les projets Visual Basic en dehors de l' **Option Strict** est activé ou dans les projets Visual c qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vous pouvez utiliser les fonctionnalités de liaison tardive dans ces langages pour accéder aux membres à liaison tardive.  Dans les projets Visual Basic où **Option Strict** est activé, vous devez utiliser la réflexion pour accéder à ces membres.  
  
### Exemples  
 L'exemple de code suivant montre comment accéder aux membres à liaison tardive dans un projet Visual Basic dans lequel **Option Strict** est désactivé ou dans un projet Visual C\# qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Cet exemple accède à la propriété **Name** à liaison tardive de la boîte de dialogue **Ouvrir** dans Word.  Pour utiliser cet exemple, exécutez\-le à partir de la classe `ThisDocument` ou `ThisAddIn` dans un projet Word.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 L'exemple de code suivant montre comment utiliser la réflexion pour accomplir la même tâche dans un projet Visual Basic dans lesquels **Option Strict** est activé.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Voir aussi  
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Utilisation du type dynamic &#40;Guide de programmation C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Réflexion &#40;C&#35; et Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  