---
title: "System.Diagnostics.DebuggerHiddenAttribute n’affecte pas &#39;Get&#39; ou &#39;Set&#39; lorsqu’il est appliqu&#233; &#224; la d&#233;finition Property | Microsoft Docs"
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
  - "bc40051"
  - "vbc40051"
helpviewer_keywords: 
  - "BC40051"
ms.assetid: 623d5e48-7fb2-48a9-bbbb-92914b08c01c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Diagnostics.DebuggerHiddenAttribute n’affecte pas &#39;Get&#39; ou &#39;Set&#39; lorsqu’il est appliqu&#233; &#224; la d&#233;finition Property
System.Diagnostics.DebuggerHiddenAttribute n’affecte pas « Get » ou « Set » lorsqu’il est appliqué à la définition Property. Appliquez l’attribut directement aux procédures « Get » et « Set » comme il convient.  
  
 Le <xref:System.Diagnostics.DebuggerHiddenAttribute> est appliqué à une déclaration de propriété.  
  
 Le code source peut appliquer le <xref:System.Diagnostics.DebuggerHiddenAttribute> à une procédure. Cela indique au débogueur Visual Studio qu’il ne doit pas s’arrêter à l’intérieur de la procédure et qu’il ne doit autoriser la définition d’aucun point d’arrêt dans la procédure.  
  
 Bien que vous puissiez appliquer <xref:System.Diagnostics.DebuggerHiddenAttribute> à une propriété, cela n’a aucun effet. Il a l’effet souhaité uniquement si vous l’appliquez à la procédure `Get` ou `Set` de la propriété.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40051  
  
### Pour corriger cette erreur  
  
-   Supprimez le <xref:System.Diagnostics.DebuggerHiddenAttribute> de la déclaration de propriété et appliquez\-le à la procédure `Get` ou `Set` de la propriété, comme il convient.  
  
## Voir aussi  
 <xref:System.Diagnostics.DebuggerHiddenAttribute>   
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)