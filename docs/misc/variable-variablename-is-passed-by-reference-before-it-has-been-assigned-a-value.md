---
title: "La variable &#39;&lt;nom_variable&gt;&#39; est pass&#233;e par r&#233;f&#233;rence avant qu’une valeur lui ait &#233;t&#233; attribu&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42030"
  - "BC42030"
helpviewer_keywords: 
  - "BC42030"
ms.assetid: 8f1aae99-f032-4fdf-b6dc-3360cc5b94de
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable &#39;&lt;nom_variable&gt;&#39; est pass&#233;e par r&#233;f&#233;rence avant qu’une valeur lui ait &#233;t&#233; attribu&#233;e
La variable '\<nom\_variable\>' est passée par référence avant qu’une valeur lui ait été attribuée. Cela peut provoquer une exception de référence null au moment de l’exécution.  
  
 Un appel de procédure passe une variable en tant qu’argument à un paramètre `ByRef` avant qu’une valeur ait été assignée à la variable.  
  
 Si aucune valeur n’a jamais été assignée à une variable, elle contient la valeur par défaut de son type de données. Pour un type de données référence, cette valeur par défaut est [Nothing](/dotnet/visual-basic/language-reference/nothing). La lecture d’une variable de référence qui a la valeur `Nothing` peut provoquer une <xref:System.NullReferenceException> dans certaines circonstances.  
  
 Quand un argument est passé à une procédure `ByRef`, cette dernière peut apporter des modifications à la variable sous\-jacente à l’argument.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42030  
  
### Pour corriger cette erreur  
  
-   Si vous prévoyez que la procédure affecte une valeur à la variable par le biais de l’argument `ByRef` et qu’il vous importe peu que la variable contienne déjà une valeur, aucune action n’est nécessaire.  
  
-   Si la logique de la procédure lit l’argument avant de lui assigner une valeur et que la variable est un type valeur, vérifiez que la logique de la procédure ne dépend pas de la présence dans la variable de sa valeur par défaut.  
  
-   Si la logique de la procédure lit l’argument avant de lui assigner une valeur et que la variable est un type référence, vérifiez que la logique de la procédure peut gérer une valeur `Nothing`. Par exemple, elle pourrait utiliser [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) pour intercepter <xref:System.NullReferenceException>.  
  
## Voir aussi  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Déclaration de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Dépannage des variables](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)