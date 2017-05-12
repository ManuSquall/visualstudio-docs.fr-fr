---
title: "Param&#232;tres optionnels dans les solutions Office"
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
  - "développement d'applications (développement Office dans Visual Studio), paramètres optionnels"
  - "champs manquant (développement Office dans Visual Studio)"
  - "applications Office (développement Office dans Visual Studio), paramètres optionnels"
  - "paramètres optionnels (développement Office dans Visual Studio)"
  - "paramètres (développement Office dans Visual Studio), facultatifs"
  - "Visual Basic (développement Office dans Visual Studio), paramètres optionnels"
  - "Visual C# (développement Office dans Visual Studio), paramètres optionnels"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Param&#232;tres optionnels dans les solutions Office
  De nombreuses méthodes des modèles objet fournis dans les applications Microsoft Office acceptent les paramètres optionnels.  Si vous utilisez Visual Basic pour développer une solution Office dans Visual Studio, vous n'avez pas besoin de passer de valeur pour les paramètres optionnels, car les valeurs par défaut sont automatiquement utilisées pour les paramètres manquants.  Dans la plupart des cas, vous pouvez également omettre les paramètres optionnels dans les projets Visual C\#. Toutefois, vous ne pouvez pas omettre les paramètres **ref** optionnels de la classe `ThisDocument` dans les projets de niveau document pour Word.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Pour plus d'informations sur l'utilisation de paramètres optionnels dans les projets Visual C\# et Visual Basic, consultez [Arguments nommés et facultatifs &#40;Guide de programmation C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) et [Optional Parameters &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  Dans les versions antérieures de Visual Studio, vous devez passer une valeur pour chaque paramètre optionnel défini dans les projets Visual C\#.  Pour des raisons pratiques, ces projets incluent une variable globale nommée `missing` que vous pouvez passer à un paramètre optionnel quand vous voulez utiliser la valeur par défaut du paramètre.  Les projets Visual C\# pour Office dans Visual Studio incluent toujours la variable `missing`, mais vous n'avez généralement pas besoin de l'utiliser quand vous développez des solutions Office dans [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], sauf si vous appelez des méthodes avec les paramètres **ref** optionnels de la classe `ThisDocument` dans des projets de niveau document pour Word.  
  
## Exemple dans Excel  
 La méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> possède de nombreux paramètres optionnels.  Vous pouvez spécifier des valeurs pour certains paramètres et accepter la valeur par défaut pour d'autres, comme indiqué dans l'exemple de code suivant.  Cet exemple utilise un projet de niveau document avec une classe de feuille de calcul nommée `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Exemple dans Word  
 La méthode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> possède de nombreux paramètres optionnels.  Vous pouvez spécifier des valeurs pour certains paramètres et accepter la valeur par défaut pour d'autres, comme indiqué dans l'exemple de code suivant.  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## Utilisation des paramètres optionnels des méthodes de la classe ThisDocument dans les projets de niveau document Visual C\# pour Word  
 Le modèle objet Word contient de nombreuses méthodes comportant des paramètres **ref** optionnels qui acceptent des valeurs <xref:System.Object>.  Cependant, vous ne pouvez pas omettre les paramètres **ref** optionnels des méthodes de la classe `ThisDocument` générée dans des projets de niveau document Visual C\# pour Word.  Visual C\# vous permet d'omettre les paramètres **ref** optionnels uniquement pour les méthodes d'interfaces, pas pour les méthodes de classes.  Par exemple, l'exemple de code suivant ne se compile pas, car les paramètres **ref** optionnels de la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> de la classe `ThisDocument` ont été omis.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 Quand vous appelez des méthodes de la classe `ThisDocument`, suivez ces consignes :  
  
-   Pour accepter la valeur par défaut d'un paramètre **ref** optionnel, passez la variable `missing` au paramètre.  La variable `missing` est automatiquement définie dans les projets Office Visual C\# et est assignée à la valeur <xref:System.Type.Missing> dans le code de projet généré.  
  
-   Pour spécifier votre propre valeur pour un paramètre **ref** optionnel, déclarez un objet assigné à la valeur que vous souhaitez spécifier, puis passez l'objet au paramètre.  
  
 L'exemple de code suivant montre comment appeler la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> en spécifiant une valeur pour le paramètre *ignoreUppercase* et en acceptant la valeur par défaut pour les autres paramètres.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 Pour écrire du code qui omet les paramètres **ref** optionnels d'une méthode de la classe `ThisDocument`, vous pouvez également appeler la même méthode sur l'objet <xref:Microsoft.Office.Interop.Word.Document> retourné par la propriété <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> et omettre les paramètres de cette méthode.  Vous pouvez faire cela dans la mesure où <xref:Microsoft.Office.Interop.Word.Document> est une interface, pas une classe.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 Pour plus d'informations sur les paramètres de types valeur et référence, consultez [Passing Arguments by Value and by Reference &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) et [Passage de paramètres &#40;Guide de programmation C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Voir aussi  
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
  
  